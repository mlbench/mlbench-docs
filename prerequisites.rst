.. highlight:: shell

Prerequisites
=============

Kubernetes
----------

MLBench uses `Kubernetes <https://kubernetes.io/>`_ as basis for the distributed cluster.
This allows for easy and reproducible installation and use of the framework on a multitude of platforms.

Since mlbench manages the setup of nodes for experiments and uses Kubernetes to monitor the status of worker pods,
it needs to be installed with a service-account that has permission to manage and monitor ``Pods`` and ``StatefulSets``.

Additionally, `helm` requires a kubernetes user account with the ``cluster-admin`` role to deploy applications to a kubernetes cluster.

To use MLBench, one would need to install `kubectl <https://kubernetes.io/docs/tasks/tools/install-kubectl/>`_

On Ubuntu/Debian:

.. code-block:: bash

    $ sudo apt-get update && sudo apt-get install -y apt-transport-https gnupg2
    $ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
    $ echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
    $ sudo apt-get update
    $ sudo apt-get install -y kubectl

.. _google-cloud:

Google Cloud
------------

GCloud SDK (Required)
^^^^^^^^^^^^^^^^^^^^^

To use MLBench with GCLoud, it requires the `gcloud <https://cloud.google.com/sdk/install>`_ CLI to be installed and authenticated on the client machine.

On Ubuntu/Debian:

.. code-block:: bash

    $ echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
    $ sudo apt-get install apt-transport-https ca-certificates gnupg
    $ curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
    $ sudo apt-get update && sudo apt-get install google-cloud-sdk
    $ gcloud init

.. note::
    In order to set you credentials for gcloud, you need to run the commands ``gcloud auth login`` and ``gcloud auth application-default login``

Manually creating a cluster (Optional)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The GCloud SDK allows for `manual cluster creation <https://cloud.google.com/kubernetes-engine/docs/how-to/creating-a-cluster>`_
Please refer to `Kubernetes Quickstart <https://cloud.google.com/kubernetes-engine/docs/quickstart>`_ for more information




If you're planning to use GPUs in your cluster, see the `GPUs <https://cloud.google.com/kubernetes-engine/docs/how-to/gpus>`_ article, especially the "Installing NVIDIA GPU device drivers" section.

When creating a GKE cluster, make sure to use version ``1.15`` or above of kubernetes, as there is an issue with DNS resolution in earlier version.
You can do this with the ``--cluster-version=1.15``
flag for the ``gcloud container clusters create`` command.

Make sure credentials for your cluster are installed correctly (use the correct zone for your cluster):

Example of cluster creation:

.. code-block:: bash

    $ gcloud container clusters create dummy-2 --zone=europe-west1-b \
        --cluster-version="1.15" --enable-network-policy \
        --machine-type=n1-standard-4 --num-nodes=2 --disk-type=pd-standard \
        --disk-size=50 --scopes=storage-full

If you would like to add GPU acceleration, add the following parameter ``--accelerator type=${GPU_TYPE},count=${NUM_GPUS}``

.. _helm-install:

Helm (Required)
---------------

Helm charts are like recipes to install Kubernetes distributed applications. They consist of templates with some logic that get rendered into Kubernetes deployment `.yaml` files
They come with some default values, but also allow users to override those values.

Helm can be found `here <https://helm.sh/docs/intro/install/>`_, and only needs to be installed if manual cluster installation is needed (i.e. manually install MLBench on a cluster)

On Ubuntu/Debian:

.. code-block:: bash

    $ curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
    $ sudo apt-get install apt-transport-https --yes
    $ echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
    $ sudo apt-get update
    $ sudo apt-get install helm