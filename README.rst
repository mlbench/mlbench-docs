***********************************************
MLBench: Distributed Machine Learning Benchmark
***********************************************

.. image:: https://github.com/mlbench/mlbench-core/workflows/mlbench-core/badge.svg?branch=develop

.. image:: https://github.com/mlbench/mlbench-docs/workflows/mlbench-docs/badge.svg?branch=develop

.. image:: https://github.com/mlbench/mlbench-helm/workflows/mlbench-helm/badge.svg?branch=develop

.. image:: https://github.com/mlbench/mlbench-dashboard/workflows/mlbench-dashboard/badge.svg?branch=develop

.. image:: https://github.com/mlbench/mlbench-benchmarks/workflows/mlbench-benchmarks/badge.svg?branch=develop

.. image:: https://readthedocs.org/projects/mlbench/badge/?version=latest
        :target: https://mlbench.readthedocs.io/en/latest/?badge=latest
        :alt: Documentation Status




A public and reproducible collection of reference implementations and benchmark suite for distributed machine learning algorithms, frameworks and systems.


* Project website: https://mlbench.github.io/
* Free software: Apache Software License 2.0
* Documentation: https://mlbench.readthedocs.io.


Features
########

* For reproducibility and simplicity, we currently focus on standard **supervised ML**, including standard deep learning tasks as well as classic linear ML models.
* We provide **reference implementations** for each algorithm, to make it easy to port to a new framework.
* Our goal is to benchmark all/most currently relevant **distributed execution frameworks**. We welcome contributions of new frameworks in the benchmark suite.
* We provide **precisely defined tasks** and datasets to have a fair and precise comparison of all algorithms, frameworks and hardware.
* Independently of all solver implementations, we provide universal **evaluation code** allowing to compare the result metrics of different solvers and frameworks.
* Our benchmark code is easy to run on **public clouds**.


Repositories
############
MLBench consists of 5 Github repositories:

* Documentation: http://github.com/mlbench/mlbench-docs
* Helm Charts for Kubernetes: http://github.com/mlbench/mlbench-helm
* Python Core Library: http://github.com/mlbench/mlbench-core
* Benchmark Implementations: http://github.com/mlbench/mlbench-benchmarks
* Dashboard: http://github.com/mlbench/mlbench-dashboard


Community
#########

Mailing list: https://groups.google.com/d/forum/mlbench

Contact Email: mlbench-contact@googlegroups.com
