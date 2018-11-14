
Component Overview
=====================

.. figure:: images/DeploymentArchitecture.png
   :alt: Deployment Architecture Overview

   Deployment Overview: Relation between Worker and Master


mlbench consists of two components, the **Master** and the **Worker** Docker containers.

Master
-----------
The master contains the Dashboard, the  main interface for the project. The dashboard allows
you to start and run a distributed ML experiment and visualizes the progress and result of the
experiment. It allows management of the mlbench nodes in the Kubernetes cluster and for most
users constitutes the sole way they interact with the mlbench project.

It also contains a REST API that can be use instead of the Dashboard, as well as being used for receiving data from the Dashboard.

The Master also manages the ``StatefulSet`` of worker through the Kubernetes API.

The code for the Master can be found in the `mlbench-dashboard <https://github.com/mlbench/mlbench-dashboard>`__ repository.

Worker
----------

The worker images contain all the boilerplate code needed for a distributed ML model
as well as the actual model code. There is a docker image for each Benchmark implementation.
They take care of training the distributed model, with some configuration supplied by
the Master.

Worker nodes send status information to the metrics API of the Master to inform it
of the progress and state of the current run.

All official reference implementations along with useful base images can be found in the
`mlbench-benchmarks <https://github.com/mlbench/mlbench-benchmarks>`__ repository.


mlbench-core
------------

mlbench-core is a Python package that contains functionality to interact with the
Master node, such as writing metrics. It also contains common code used across
multiple benchmark implementations and implementation independent helper
functions.

The code can be found in the `mlbench-core <https://github.com/mlbench/mlbench-core>`__ repository.

Helm Chart
----------

The Helm chart allows automated installation of the MLBench framework into a Kubernetes cluster.

It can be found in the `mlbench-helm <https://github.com/mlbench/mlbench-helm>`__ repository.
