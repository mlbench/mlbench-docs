Tutorials
================

.. _Blog: https://mlbench.github.io/blog/

Also check out our Blog_ for good tips and the latest news!

Adding an existing PyTorch training script into MLBench
----------------------------------------------------------

In this tutorial, we will go through the process of adapting existing distributed PyTorch code to work with the MLBench framework. This allows you to run your models in the MLBench environment and easily compare them
with our reference implementations as baselines to see how well your code performs.

MLBench is designed to easily be used with third-party models, allowing for quick and fair comparisons by standardizing the data distribution, evaluation dataset and providing evaluation code.
It saves all of the hassle that's needed to implement your own baselines for comparison.

We will adapt the code from the official `PyTorch distributed tutorial <https://pytorch.org/tutorials/intermediate/dist_tuto.html>`_ to run in MLBench.
If you're unfamiliar with that tutorial, it might be worth giving it a quick look so you know what we're working with.

Adapting the Code
^^^^^^^^^^^^^^^^^

To get started, create a new directory ``mlbench-pytorch-tutorial`` and copy the `train_dist.py <https://github.com/seba-1511/dist_tuto.pth/blob/gh-pages/train_dist.py>`_ file into it.

The official tutorial spawns multiple parallel processes on a single machine, but we want to run the code on multiple machines, so first we need to replace the initialization functionality with our own.

Replace

.. code-block:: python
    :linenos:

    if __name__ == "__main__":
        size = 2
        processes = []
        for rank in range(size):
            p = Process(target=init_processes, args=(rank, size, run))
            p.start()
            processes.append(p)

        for p in processes:
            p.join()


with

.. code-block:: python
    :linenos:
    
    if __name__ == "__main__":
        parser = argparse.ArgumentParser(description='Process run parameters')
        parser.add_argument('--run_id', type=str, help='The id of the run')
        parser.add_argument('--rank', type=int, help='The rank of this worker')
        parser.add_argument('--hosts', type=str, help='The list of hosts')
        args = parser.parse_args()
        init_processes(args.rank, args.run_id, args.hosts)

and add

.. code-block:: python
    :linenos:
    
    import argparse

to the top of the file.

We also need to change the ``init_processes`` method to reflect our previous changes, along with setting the ``WORLD_SIZE`` and ``RANK`` environment variables:

.. code-block:: python
    :linenos:
        
    def init_processes(rank, run_id, hosts, backend='gloo'):
        """ Initialize the distributed environment. """
        hosts = hosts.split(',')
        os.environ['MASTER_ADDR'] = hosts[0] # first worker is the master worker
        os.environ['MASTER_PORT'] = '29500'
        world_size = len(hosts)
        os.environ['WORLD_SIZE'] = str(world_size)
        os.environ['RANK'] = str(rank)
        dist.init_process_group(backend, rank=rank, world_size=len(world_size))
        run(rank, world_size, run_id)

Next, we need to change the signature of the ``run`` method to add the ``run_id`` parameter. The ``run_id`` is a unique identifier automatically assigned
by MLBench to identify an individual run and all its data and performance metrics.

.. code-block:: python
    :linenos:
    
    def run(rank, size, run_id):


At this point, the script could technically already run in MLBench.
However, you would not be able to see any reported results or intermediate 
stats during training. Results are shown either in the Dashboard (where 
you can see them in real time) or can be downloaded at any time during the 
run from the command line. So let's add some reporting functionality.

The PyTorch script reports loss to ``stdout``, but we can easily report the loss to MLBench as well. First we need to import the relevant MLBench
functionality by adding the following line to the imports at the top of the file:

.. code-block:: python
    :linenos:
    
    from mlbench_core.utils import Tracker
    from mlbench_core.evaluation.goals import task1_time_to_accuracy_goal
    from mlbench_core.evaluation.pytorch.metrics import TopKAccuracy
    from mlbench_core.controlflow.pytorch import validation_round

``task1_time_to_accuracy_goal`` measures the time taken to reach 80% accuracy.

After this we can simply create a ``Tracker`` object and use it to report the loss and add metrics (``TopKAccuracy``) to track. We add code to record the timing of different steps with ``tracker.record_batch_step()``.
We have to tell the tracker that we're in the training loop by calling ``tracker.train()`` and that the epoch is done by calling ``tracker.epoch_end()``. The loss is recorded with ``tracker.record_loss()``.

.. code-block:: python
    :linenos:
    
    def run(rank, size, run_id):
        """ Distributed Synchronous SGD Example """
        torch.manual_seed(1234)
        train_set, bsz = partition_dataset()
        model = Net()
        optimizer = optim.SGD(model.parameters(), lr=0.01, momentum=0.5)
        metrics = [                                     # Add metrics to gather
            TopKAccuracy(topk=1),
            TopKAccuracy(topk=5)
        ]
        loss_func = nn.NLLLoss()

        tracker = Tracker(metrics, run_id, rank)        # Instantiate a Tracker

        num_batches = ceil(len(train_set.dataset) / float(bsz))

        tracker.start()                                 # Start the tracker

        for epoch in range(10):
            tracker.train()                             # Record training start

            epoch_loss = 0.0
            for data, target in train_set:
                tracker.batch_start()                   # Record batch start

                optimizer.zero_grad()
                output = model(data)

                tracker.record_batch_step('forward')    # Record batch forward step

                loss = loss_func(output, target)
                epoch_loss += loss.data.item()

                tracker.record_batch_step('loss')       # Record batch loss step

                loss.backward()

                tracker.record_batch_step('backward')   # Record batch backward step

                average_gradients(model)
                optimizer.step()

                tracker.batch_end()                     # Record batch end

            tracker.record_loss(epoch_loss, num_batches, log_to_api=True)

            logging.debug('Rank %s, epoch %s: %s',
                        dist.get_rank(), epoch,
                        epoch_loss / num_batches)       # Print to stderr

            tracker.epoch_end()                         # Record epoch end

            if tracker.goal_reached:                    # Goal reached
                logging.debug("Goal Reached!")
                return


That's it. Now the training will report the loss of each worker back to the Dashboard and the output result files. 
On the Dashboard, you will also see a nice graph showing this data.

For the official tasks, we also need to report validation stats to the tracker and use the official validation code. Rename the current ``partition_dataset()`` method to ``partition_dataset_train``
and add a new partition method to load the validation set:

.. code-block:: python
    :linenos:

    def partition_dataset_val():
        """ Partitioning MNIST validation set"""
        dataset = datasets.MNIST(
            './data',
            train=False,
            download=True,
            transform=transforms.Compose([
                transforms.ToTensor(),
                transforms.Normalize((0.1307, ), (0.3081, ))
            ]))
        size = dist.get_world_size()
        bsz = int(128 / float(size))
        partition_sizes = [1.0 / size for _ in range(size)]
        partition = DataPartitioner(dataset, partition_sizes)
        partition = partition.use(dist.get_rank())
        val_set = torch.utils.data.DataLoader(
            partition, batch_size=bsz, shuffle=True)
        return val_set, bsz

Then load the validation set and add the goal for the official task (The `Task 1a goal <https://mlbench.readthedocs.io/en/latest/benchmark-tasks.html#a-image-classification-resnet-cifar-10>`_
is used for illustration purposes in this example):

.. code-block:: python
    :linenos:

    def run(rank, size, run_id):
        """ Distributed Synchronous SGD Example """
        torch.manual_seed(1234)
        train_set, bsz = partition_dataset_train()
        val_set, bsz_val = partition_dataset_val()
        model = Net()
        optimizer = optim.SGD(model.parameters(), lr=0.01, momentum=0.5)
        metrics = [
            TopKAccuracy(topk=1),
            TopKAccuracy(topk=5)
        ]
        loss_func = nn.NLLLoss()

        goal = task1_time_to_accuracy_goal

        tracker = Tracker(metrics, run_id, rank, goal=goal)

        num_batches = ceil(len(train_set.dataset) / float(bsz))
        num_batches_val = ceil(len(val_set.dataset) / float(bsz_val))

        tracker.start()

Now all that is needed is to add the validation loop code (``validation_round()``) to run validation in the ``run()`` function. We also check if the goal is reached and stop training if it is.
``validation_round()`` evaluates the metrics on the validation set and reports the results to the Dashboard.

.. code-block:: python
    :linenos:

    tracker.record_loss(epoch_loss, num_batches, log_to_api=True)

    logging.debug('Rank %s, epoch %s: %s',
                  dist.get_rank(), epoch,
                  epoch_loss / num_batches)

    validation_round(val_set, model, loss_func, metrics, run_id, rank,
                      'fp32', transform_target_type=None, use_cuda=False,
                      max_batch_per_epoch=num_batches_val, tracker=tracker)

    tracker.epoch_end()

    if tracker.goal_reached:
        logging.debug("Goal Reached!")
        return

The full code (with some additional improvements) is in our `Github Repo <https://github.com/mlbench/mlbench-benchmarks/blob/master/examples/mlbench-pytorch-tutorial/>`_.

Creating a Docker Image for Kubernetes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To actually run our code, we need to wrap it in a Docker Image. We could create one from scratch, but it's easier to use the PyTorch Base image provided by MLBench, which already includes everything you might need for executing a PyTorch model.

Create a new file called ``Dockerfile`` in the ``mlbench-pytorch-tutorial`` directory and add the following code:

.. code-block:: docker
    :linenos:

    FROM mlbench/mlbench-pytorch-base:latest

    RUN pip install mlbench-core

    # The reference implementation and user defined implementations are placed here.
    # ADD ./requirements.txt /requirements.txt
    # RUN pip install --no-cache-dir -r /requirements.txt

    RUN mkdir /codes
    ADD ./train_dist.py /codes/train_dist.py

    EXPOSE 29500

    ENV PYTHONPATH /codes

The ``mlbench-pytorch-base:latest`` image already contains all necessary libraries, but if your image requires additional python libraries, you can add them with the commands on lines 6 and 7, along with adding a ``requirements.txt`` file.

In order for Kubernetes to access the image, you have to build and upload it to a Docker registry that's accessible to Kubernetes, for instance `Docker Hub <https://hub.docker.com/>`_ (Make sure to change the Docker image and repo name accordingly):

.. code-block:: shell

    $ docker login
    $ docker build -t <user|organisation>/<name>:latest mlbench-pytorch-tutorial/
    $ docker push mlbench/pytorch-tutorial:latest

The image is now built and available for running in MLBench.

Running the code in MLBench
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Navigate to the MLBench Dashboard and go to the ``Runs`` page.

Create a new Run:


.. figure:: images/tutorials/New_Run.png
    :width: 80%
    :align: center
    :alt: New Run Page

Enter the URL of the newly uploaded Docker image (The host can be left out if you use Docker Hub). Then enter the command to execute on each worker:

.. code-block:: shell

    /conda/bin/python /codes/train_dist.py --hosts {hosts} --rank {rank} --run_id {run_id}


The values in brackets will be substituted by MLBench with the correct values and passed to our script.

We also need to choose which backend we want to run on (in our case, MPI) and 
set the number of workers on which we want to execute our run.


.. image:: images/tutorials/Pytorch_New_Run.png
    :width: 60%
    :align: center
    :alt: Create New PyTorch Run

Now we're all set to start our experiment. Hit ``Add Run`` and that's it. You just ran a custom model on MLBench.
If you are only running from the command line, you can execute:

.. code-block:: shell

    mlbench run custom-pytorch-run 2

When prompted, choose ``Custom Image`` and enter the image and execution command.

If you are using the Dashboard, you should see a graph of the training loss of each worker, along with the combined ``stdout`` and ``stderr`` of all workers.
If you are running from the command line, you will see these printed to your terminal 
and will be able to access the training data and results using ``mlbench download <run_name>``
(check out our tutorial on :ref:`cmdline-tutorial` for more information).


.. image:: images/tutorials/pytorch-tutorial-result.png
    :align: center
    :width: 80%
    :alt: Result of the Tutorial


.. _cmdline-tutorial:

Using the MLBench Command-Line Interface
-----------------------------------------

In this tutorial we'll introduce the CLI and show you how easy it is to get it up and running.

**Please beware any costs that might be incurred by running this tutorial on the Google cloud. Usually costs should only be on the order of 5-10USD. We don't take any responsibility for the costs incurred**

Install the `mlbench-core <https://github.com/mlbench/mlbench-core/tree/master>`_ python package by running:

.. code-block:: shell

    pip install mlbench-core

After installation, mlbench is usable by calling the ``mlbench`` command.

MLBench supports multiple clouds, but for the purposes of this tutorial we will focus on Google Cloud. 
To create a new Google cloud cluster, simply run (this might take a couple of minutes):

.. code-block:: shell

    $ mlbench create-cluster gcloud 3 my-cluster
    [...]
    MLBench successfully deployed


This creates a cluster with 3 nodes called ``my-cluster-3`` and sets up the mlbench deployment in that cluster. Note that the number of nodes should always be 1 higher than the maximum number of workers you want to run.

To start an experiment, simply run:

.. code-block:: shell

    $ mlbench run my-run 2

    Benchmark:

    [0]     PyTorch Cifar-10 ResNet-20
    [1]     PyTorch Cifar-10 ResNet-20 (Scaling LR)
    [2]     PyTorch Linear Logistic Regression
    [3]     PyTorch Machine Translation GNMT
    [4]     PyTorch Machine Translation Transformer
    [5]     Tensorflow Cifar-10 ResNet-20 Open-MPI
    [6]     PyTorch Distributed Backend benchmarking
    [7]     Custom Image

    Selection [0]: 1
    Backend:

    [0]     MPI
    [1]     GLOO
    [2]     NCCL
    [3]     Custom Backend

    Selection [0]: 0

    [...]

    Run started with name my-run-2


You will be prompted to select the benchmark image you want to run (or to specify a custom image). Afterwards, a new benchmark run will be started in the cluster with 2 workers.

You can also start multiple runs at the same time, which will be scheduled as nodes become available:

.. code-block:: shell

    $ mlbench run my-run 2 4 8 16

    Benchmark:

    [0]     PyTorch Cifar-10 ResNet-20
    [1]     PyTorch Cifar-10 ResNet-20 (Scaling LR)
    [2]     PyTorch Linear Logistic Regression
    [3]     PyTorch Machine Translation GNMT
    [4]     PyTorch Machine Translation Transformer
    [5]     Tensorflow Cifar-10 ResNet-20 Open-MPI
    [6]     PyTorch Distributed Backend benchmarking
    [7]     Custom Image


    Selection [0]: 1
    Backend:

    [0]     MPI
    [1]     GLOO
    [2]     NCCL
    [3]     Custom Backend

    Selection [0]: 0

    [...]

    Run started with name my-run-2
    Run started with name my-run-4
    Run started with name my-run-8
    Run started with name my-run-16


which would start runs with 2, 4, 8 and 16 workers, respectively.

To see the status of a run, execute:

.. code-block:: shell

    $ mlbench status my-run-2
    [...]
    id      name    created_at            finished_at state
    ---     ------  -----------            ----------- -----
    1       my-run-2 2019-11-11T13:35:06              started
    No Validation Loss Data yet
    No Validation Precision Data yet

After the first round of validation, this command also outputs the current validation loss and precision.

To download the results of a current or finished run, use:

.. code-block:: shell

    $ mlbench download my-run-2


which will download all the metrics of the run as a zip file. This file also contains the official benchmark result once the run finishes, in the form of the ``official_result.txt``.

You can also access all the information of the run in the dashboard. To get the dashboard URL, simply run:

.. code-block:: shell

    $ mlbench get-dashboard-url
    [...]
    http://34.76.223.123:32535


Don't forget to delete the cluster once you're done!

.. code-block:: shell

    $ mlbench delete-cluster gcloud my-cluster-3
    [...]


**NOTE**: if you created a cluster in a non-default zone using the ``-z`` flag, 
you also need to delete it by passing the same flag and argument to ``mlbench delete-cluster``.

.. code-block:: shell

    # create cluster in europe-west2-b (non-default)
    $ mlbench create-cluster gcloud -z europe-west2-b 3 my-cluster

    # delete cluster
    $ mlbench delete-cluster gcloud -z europe-west2-b my-cluster-3
