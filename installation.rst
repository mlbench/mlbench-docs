.. highlight:: shell

Installation
============

Make sure to read :doc:`prerequisites` before installing mlbench.

Automated Setup
---------------

MLBench can be installed automatically using the MLBench CLI.

Install the CLI:

.. code-block:: bash

   $ pip install mlbench-core


Then you can create a cluster by running:

.. code-block:: bash

   $ mlbench create-cluster gcloud 3 my-cluster
   [...]
   MLBench successfully deployed

Which creates a cluster called ``my-cluster-3`` with 3 nodes (See ``mlbench create-cluster gcloud --help`` for more options).

Once created, you can run experiments with:

.. code-block:: bash

   $ mlbench run my-run 2

   Benchmark:

   [0] PyTorch Cifar-10 ResNet-20 Open-MPI
   [1] PyTorch Cifar-10 ResNet-20 Open-MPI (SCaling LR)
   [2] PyTorch Linear Logistic Regrssion Open-MPI
   [3] Tensorflow Cifar-10 ResNet-20 Open-MPI
   [4] Custom Image

   Selection [0]: 1

   [...]

   Run started with name my-run-2

See ``mlbench run --help`` for more options.

You can access the dashboard with ``mlbench get-dashboard-url``.

To see the state of the experiment, run ``mlbench status my-run-2``.

To download the results of the experiment, run ``mlbench download my-run-2``.

Don't forget to delete the cluster once you're done by running ``mlbench delete-cluster gcloud my-cluster-3``

Manual Setup
------------
The manual setup assumes you have checked out the `mlbench-helm <https://github.com/mlbench/mlbench-helm>`__ github repository and have a terminal open in the checked-out ``mlbench-helm`` directory.

.. _google-cloud-setup:

Google Cloud and Cluster Setup
""""""""""""""""""""""""""""""

This project provides a script to make all the Google Cloud and Cluster setup. In order to do so, please run the following commands:

.. code-block:: bash

    $ ./google_cloud_setup.sh create-cluster
    $ ./google_cloud_setup.sh install-chart


To delete cluster and cleanup:

.. code-block:: bash

    $ ./google_cloud_setup.sh delete-cluster

To uninstall chart:

.. code-block:: bash

    $ ./google_cloud_setup.sh uninstall-chart

For general information on the available commands, please run:

.. code-block:: bash

    $ ./google_cloud_setup.sh help


.. _helm-charts:

Helm Chart values
"""""""""""""""""

Since every Kubernetes is different, there are no reasonable defaults for some values, so the following properties have to be set.
You can save them in a yaml file of your chosing. This guide will assume you saved them in `myvalues.yaml`. For a reference file for all configurable values, you can copy the `values.yaml` file to `myvalues.yaml`.

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
   If you set ``workers``, ``cpu`` or ``gpu`` higher than available in your cluster, Kubernetes will not be able to allocate nodes to mlbench and the deployment will hang indefinitely, without throwing an exception.
   Kubernetes will just wait until nodes that fit the requirements become available. So make sure your cluster actually has the requirements avilable that you requested.

.. note::
   To use ``gpu`` in the cluster, the `nvidia device plugin <https://github.com/NVIDIA/k8s-device-plugin>`_ should be installed. See :ref:`plugins` for details

.. note::
   Use commands like ``gcloud compute disks create --size=10G --zone=europe-west1-b my-pd-name`` to create persistent disk.

.. note::
   The GCE persistent disk will be mounted to `/datasets/` directory on each worker.

Helm Install
""""""""""""

Set the :ref:`helm-charts`

Use helm to install the mlbench chart (Replace ``${RELEASE_NAME}`` with a name of your choice):

.. code-block:: bash

   $ helm upgrade --wait --recreate-pods -f values.yaml --timeout 900 --install ${RELEASE_NAME} .

Follow the instructions at the end of the helm install to get the dashboard URL. E.g.:

.. code-block:: bash
   :emphasize-lines: 5,6,7

   $ helm upgrade --wait --recreate-pods -f values.yaml --timeout 900 --install rel .
     [...]
     NOTES:
     1. Get the application URL by running these commands:
        export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services rel-mlbench-master)
        export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
        echo http://$NODE_IP:$NODE_PORT

This outputs the URL the Dashboard is accessible at.

.. _plugins:

Plugins
"""""""
In ``values.yaml``, one can optionally install Kubernetes plugins by turning on/off the following flags:

- ``weave.enabled``: If true, install the `weave network plugin <https://github.com/weaveworks/weave>`_.
- ``nvidiaDevicePlugin.enabled``: If true, install the `nvidia device plugin <https://github.com/NVIDIA/k8s-device-plugin>`_.

Google Cloud / Google Kubernetes Engine
"""""""""""""""""""""""""""""""""""""""

Set the :ref:`helm-charts`

.. important::
   Make sure to read the prerequisites for :ref:`google-cloud`

Please make sure that ``kubectl`` is configured `correctly <https://cloud.google.com/kubernetes-engine/docs/quickstart>`_.

.. caution::
   Google installs several pods on each node by default, limiting the available CPU. This can take up to 0.5 CPU cores per node. So make sure to provision VM's that have at least 1 more core than the amount of cores you want to use for you mlbench experiment.
   See `here <https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture#memory_cpu>`__ for further details on node limits.

Install mlbench (Replace ``${RELEASE_NAME}`` with a name of your choice):

.. code-block:: bash

   $ helm upgrade --wait --recreate-pods -f values.yaml --timeout 900 --install ${RELEASE_NAME} .

To access mlbench, run these commands and open the URL that is returned (**Note**: The default instructions returned by `helm` on the commandline return the internal cluster ip only):

.. code-block:: bash

   $ export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services ${RELEASE_NAME}-mlbench-master)
   $ export NODE_IP=$(gcloud compute instances list|grep $(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}") |awk '{print $5}')
   $ gcloud compute firewall-rules create --quiet mlbench --allow tcp:$NODE_PORT,tcp:$NODE_PORT
   $ echo http://$NODE_IP:$NODE_PORT

.. danger::
   The last command opens up a firewall rule to the google cloud. Make sure to delete the rule once it's not needed anymore:

   .. code-block:: bash

      $ gcloud compute firewall-rules delete --quiet mlbench


Minikube
""""""""

Minikube allows running a single-node Kubernetes cluster inside a VM on your laptop, for users looking to try out Kubernetes or to develop with it.

Installing mlbench to `minikube <https://github.com/kubernetes/minikube>`_.

Set the :ref:`helm-charts`

.. important::
   If you are using Kubernetes version 1.16 or higher you will need to to add the following line to `/etc/kubernetes/manifest/kube-apiserver.yaml`

   .. code-block:: bash

      --runtime-config=apps/v1beta1=true,apps/v1beta2=true,extensions/v1beta1/daemonsets=true,extensions/v1beta1/deployments=true,extensions/v1beta1/replicasets=true,extensions/v1beta1/networkpolicies=true,extensions/v1beta1/podsecuritypolicies=true


Start minikube cluster

.. code-block:: bash

    $ minikube start


Next install or upgrade a helm chart with desired configurations with name `${RELEASE_NAME}`

.. code-block:: bash

    $ helm init --kube-context minikube --wait
    $ helm upgrade --wait --recreate-pods -f myvalues.yaml --timeout 900 --install ${RELEASE_NAME} .

.. note::
    The minikube runs a single-node Kubernetes cluster inside a VM. So we need to fix the :code:`replicaCount=1` in `values.yaml`.

Once the installation is finished, one can obtain the url

.. code-block:: bash

    $ export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services ${RELEASE_NAME}-mlbench-master)
    $ export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
    $ echo http://$NODE_IP:$NODE_PORT

Now the mlbench dashboard should be available at :code:`http://${NODE_IP}:${NODE_PORT}`.

.. note::
  To access :code:`http://$NODE_IP:$NODE_PORT` outside minikube, run the following command on the host:

  .. code-block:: bash

      $ ssh -i ${MINIKUBE_HOME}/.minikube/machines/minikube/id_rsa -N -f -L localhost:${NODE_PORT}:${NODE_IP}:${NODE_PORT} docker@$(minikube ip)

  where :code:`$MINIKUBE_HOME` is by default :code:`$HOME`. One can view mlbench dashboard at :code:`http://localhost:${NODE_PORT}`
  
  
Kubernetes-in-Docker (KIND)
"""""""""""""""""""""""""""

Kubernetes-in-Docker allows simulating multiple nodes locally on a single machine. This is useful for development.

To use KIND, you need to setup a local registry and start a KIND server. We provide the script ``kind-with-registry.sh`` that can be used to start a local registry and a local cluster with one master and two worker nodes. 

In order to push an image to the local registry you need to follow the procedure below. We use the image ``mlbench/pytorch-cifar10-resnet-scaling:2.3.0`` for illustration, but you can use any image of your choice.

1. Pull (or build) an image on your local machine:

.. code-block:: bash

      $ docker pull mlbench/pytorch-cifar10-resnet-scaling:2.3.0
   
2. Tag the image to use the local registry:

.. code-block:: bash

      $ docker tag mlbench/pytorch-cifar10-resnet-scaling:2.3.0 localhost:5000/pytorch-cifar10-resnet-scaling:2.3.0
      
3. Push the image to the local registry 

.. code-block:: bash

      $ docker push localhost:5000/pytorch-cifar10-resnet-scaling:2.3.0

4. Now you can use the image as a custom image when starting a run on your cluster. Please make sure to specify the new tag of the image (``localhost:5000/pytorch-cifar10-resnet-scaling:2.3.0`` in the running example).

Next, you need to install ``helm`` (See :doc:`prerequisites`) and set the :ref:`helm-charts`.

Finally, to install mlbench on your local cluster run the following command (you can replace ``rel`` with a release name of your choice)

.. code-block:: bash

   $ helm upgrade --wait --recreate-pods -f values.yaml --timeout 900s --install rel .
   [...]
   NOTES:
   1. Get the application URL by running these commands:
      export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services rel-mlbench-master)
      export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")
      echo http://$NODE_IP:$NODE_PORT

Run the 3 commands printed by the last command. The third command will output the URL where you can access the MLBench Dashboard. From there, you can start and monitor runs on your local cluster. 
