.. highlight:: shell

Installation
============

Make sure to read :doc:`prerequisites` before installing mlbench.

Then, the library can be installed directly using ``pip``:

.. code-block:: bash

   $ pip install mlbench-core

This will install the ``mlbench`` CLI to the current environment, and will allow creation/deletion of clusters, as well as creating runs.

In addition to installation of CLI, we have provided alternative ways of installing `mlbench-core` depending on the use-case.
These are alternatives and allow installation of extra libraries which are not needed for CLI use.
Here are all the installation possibilities:

.. code-block:: bash

    $ pip install mlbench-core[test] # Install with test requirements
    $ pip install mlbench-core[lint] # Install with lint requirements
    $ pip install mlbench-core[torch] # Install only with torch requirements
    $ pip install mlbench-core[tensorflow] # Install only with tensorflow requirements
    $ pip install mlbench-core[dev] # Install all dependencies for development (all of the above)

.. code-block:: bash

   $ mlbench --help
      Usage: mlbench [OPTIONS] COMMAND [ARGS]...

      Console script for mlbench_cli.

      Options:
        --version  Print mlbench version
        --help     Show this message and exit.

      Commands:
        charts             Chart the results of benchmark runs Save generated...
        create-cluster     Create a new cluster.
        delete             Delete a benchmark run
        delete-cluster     Delete a cluster.
        download           Download the results of a benchmark run
        get-dashboard-url  Returns the dashboard URL of the current cluster
        list-clusters      List all currently configured clusters.
        run                Start a new run for a benchmark image
        set-cluster        Set the current cluster to use.
        status             Get the status of a benchmark run, or all runs if no...

Cluster & Run Deployment (using CLI)
------------------------------------

One can easily deploy a cluster on both AWS and GCloud, using the ``mlbench`` CLI.

For example, one can create a GCloud cluster by running:

.. code-block:: bash

   $ mlbench create-cluster gcloud 3 my-cluster
   [...]
   MLBench successfully deployed

Which creates a cluster called ``my-cluster-3`` with 3 nodes (See ``mlbench create-cluster gcloud --help`` for more options).

Once created, experiments can be run using:

.. code-block:: bash

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

   [...]

   Run started with name my-run-2

A few handy commands for quickstart:

 - To obtain the dashboard URL: ``mlbench get-dashboard-url``.
 - To see the state of the experiment: ``mlbench status my-run-2``.
 - To download the results of the experiment: ``mlbench download my-run-2``.
 - To delete the cluster: ``mlbench delete-cluster gcloud my-cluster-3``


Kubernetes in Docker (Debugging only)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

MLBench also supports deployment of dashboard and tasks to a local cluster. This uses the KIND technology and can be
easily deployed using the CLI. This can be used for debugging code or development, but is not meant to 

Click `here <https://kind.sigs.k8s.io/docs/user/quick-start/#installation>`_ to download and install KIND.

.. code-block:: bash

    $ mlbench create-cluster kind 3 my-cluster
    [...]
    MLBench successfully deployed

This creates a local cluster of 3 "nodes", as well as a local docker registry on port 5000.
This allows for deploying runs using local docker images.
To do that, one needs to push their docker image to the local repository:

.. code-block:: bash

    $ docker tag <repo>/<image-name>:<tag> localhost:5000/<image-name>:<tag>
    $ docker push localhost:5000/<image-name>:<tag>

You can now use the image ``localhost:5000/<image-name>:<tag>`` in MLBench's dashboard to run a task.

.. _helm-charts:

Manual helm chart deployment (Optional)
---------------------------------------

Helm Chart installation
^^^^^^^^^^^^^^^^^^^^^^^

The manual deployment requires the repo `mlbench-helm <https://github.com/mlbench/mlbench-helm>`_ to be cloned, and helm to be installed :ref:`helm-install`

MLBench's Helm charts can also be deployed manually on a running Kubernetes cluster.
For that, it is needed to have the credentials for the cluster in the ``kubectl`` config.
For example, to obtain the credentials for a GCloud Kubernetes cluster, one should run

.. code-block:: bash

   $ gcloud container clusters get-credentials --zone ${MACHINE_ZONE} ${CLUSTER_NAME}

This will setup ``kubectl`` for the cluster.

Then to deploy the dashboard on the running cluster, we need to apply our values to the existing helm template, and deploy it onto the cluster

.. code-block:: bash

   $ cd mlbench-helm
   $ helm template ${RELEASE_NAME} . \
        --set limits.workers=${NUM_NODES-1} \
        --set limits.gpu=${NUM_GPUS} \
        --set limits.cpu=${NUM_CPUS-1} | kubectl apply -f -

Where :
   - ``RELEASE_NAME`` represents the cluster name (called ``my-cluster-3`` in the example above)
   - ``NUM_NODES`` is the maximum number of worker nodes available. This sets the maximum number of nodes that can be chosen for an experiment in the UI/CLI.
   - ``NUM_GPUS`` is the number of gpus requested by each worker pod.
   - ``NUM_CPUS`` is the maximum number of CPUs (Cores) available on each worker node. Uses Kubernetes notation (`8` or `8000m` for 8 cpus/cores). This is also the maximum number of Cores that can be selected for an experiment in the UI

This will deploy the helm charts with the corresponding images to each node, and will set the hardware limits.

.. note::
   Get the application URL by running these commands:
    .. code-block:: bash

       $ export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services ${RELEASE_NAME}-mlbench-master)
       $ export NODE_IP=$(gcloud compute instances list|grep $(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}") |awk '{print $5}')
       $ gcloud compute firewall-rules create --quiet mlbench --allow tcp:$NODE_PORT,tcp:$NODE_PORT
       $ echo http://$NODE_IP:$NODE_PORT

.. danger::
    The last command opens up a firewall rule to the google cloud. Make sure to delete the rule once it's not needed anymore:

    .. code-block:: bash

      $ gcloud compute firewall-rules delete --quiet mlbench

One can also create a new ``myvalues.yml`` file with custom limits:

.. code-block:: yaml

   limits:
     workers:
     cpu:
     gpu:

   gcePersistentDisk:
     enabled:
     pdName:

- ``limits.workers`` is the maximum number of worker nodes available to mlbench. This sets the maximum number of nodes that can be chosen for an experiment in the UI. By default mlbench starts 2 workers on startup.
- ``limits.cpu`` is the maximum number of CPUs (Cores) available on each worker node. Uses Kubernetes notation (`8` or `8000m` for 8 cpus/cores). This is also the maximum number of Cores that can be selected for an experiment in the UI
- ``limits.gpu`` is the number of gpus requested by each worker pod.
- ``gcePersistentDisk.enabled`` create resources related to NFS persistentVolume and persistentVolumeClaim.
- ``gcePersistentDisk.pdName`` is the name of persistent disk existed in GKE.

.. Caution::
   If ``workers``, ``cpu`` or ``gpu`` are set higher than available in the cluster, Kubernetes will not be able to allocate nodes to mlbench and the deployment will hang indefinitely, without throwing an exception.
   Kubernetes will just wait until nodes that fit the requirements become available. So make sure the cluster actually has the requested requirements.

.. note::
   To use ``gpu`` in the cluster, the `nvidia device plugin <https://github.com/NVIDIA/k8s-device-plugin>`_ should be installed. See :ref:`plugins` for details

.. note::
   Use commands like ``gcloud compute disks create --size=10G --zone=europe-west1-b my-pd-name`` to create persistent disk.

.. note::
   The GCE persistent disk will be mounted to `/datasets/` directory on each worker.

.. caution::
   Google installs several pods on each node by default, limiting the available CPU. This can take up to 0.5 CPU cores per node. So make sure to provision VM's that have at least 1 more core than the amount of cores you want to use for you mlbench experiment.
   See `here <https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture#memory_cpu>`__ for further details on node limits.

.. _plugins:

Plugins
^^^^^^^

In ``values.yaml``, one can optionally install Kubernetes plugins by turning on/off the following flags:

- ``weave.enabled``: If true, install the `weave network plugin <https://github.com/weaveworks/weave>`_.
- ``nvidiaDevicePlugin.enabled``: If true, install the `nvidia device plugin <https://github.com/NVIDIA/k8s-device-plugin>`_.