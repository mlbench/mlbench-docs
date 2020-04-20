Change Log
==========

v2.0.0
^^^^^^

MLBench Helm
""""""""""""

**Implemented enhancements:**

- Added GKE and AWS Setup Scripts

MLBench Benchmarks
""""""""""""""""""

**Implemented enhancements:**

- Added Goals to PyTorch Benchmark
- Updated PyTorch Tutorial code
- Changed all images to newest ``mlbench-core`` version.

MLBench Dashboard
"""""""""""""""""
**Implemented enhancements:**

- Added Download of Task Goals
- Fixed some performance issues

v2.4.0
^^^^^^

MLBench Core
""""""""""""

`v2.4.0 <https://github.com/mlbench/mlbench-core/tree/v2.4.0>`__ (2020-04-20)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.3.2...v2.4.0>`__

**Implemented enhancements:**

-  Switch to black for code formatting
   `#35 <https://github.com/mlbench/mlbench-core/issues/35>`__

**Closed issues:**

-  Travis tests run only for Python 3.6
   `#65 <https://github.com/mlbench/mlbench-core/issues/65>`__
-  Downloading results fails if ``--output`` option is not provided
   `#57 <https://github.com/mlbench/mlbench-core/issues/57>`__
-  Remember user input in mlbench run
   `#56 <https://github.com/mlbench/mlbench-core/issues/56>`__
-  Aggregate the gradients by model, instead of by layers.
   `#45 <https://github.com/mlbench/mlbench-core/issues/45>`__
-  Update docker images to CUDA10, mlbench-core module to newest
   `#43 <https://github.com/mlbench/mlbench-core/issues/43>`__
-  Upgrade PyTorch to 1.4
   `#40 <https://github.com/mlbench/mlbench-core/issues/40>`__

**Merged pull requests:**

-  Pytorch v1.4.0
   `#68 <https://github.com/mlbench/mlbench-core/pull/68>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Fix ci `#67 <https://github.com/mlbench/mlbench-core/pull/67>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add aggregation by model
   `#61 <https://github.com/mlbench/mlbench-core/pull/61>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Remember user input in mlbench run
   `#60 <https://github.com/mlbench/mlbench-core/pull/60>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Add default name of output file in CLI
   `#58 <https://github.com/mlbench/mlbench-core/pull/58>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Cli adaptation
   `#55 <https://github.com/mlbench/mlbench-core/pull/55>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Update tags and patch version to 2.3.2
   `#52 <https://github.com/mlbench/mlbench-core/pull/52>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add get\_optimizer to create optimizer object
   `#48 <https://github.com/mlbench/mlbench-core/pull/48>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)

v2.3.2
^^^^^^

MLBench Core
""""""""""""

`v2.3.2 <https://github.com/mlbench/mlbench-core/tree/v2.3.2>`__ (2020-04-07)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.3.1...v2.3.2>`__

**Implemented enhancements:**

-  Add NCCL & GLOO Backend support
   `#49 <https://github.com/mlbench/mlbench-core/issues/49>`__
-  Add NCCL & GLOO Backend support
   `#47 <https://github.com/mlbench/mlbench-core/pull/47>`__
   (`giorgiosav <https://github.com/giorgiosav>`__)

**Fixed bugs:**

-  math ValueError with 1-node cluster
   `#38 <https://github.com/mlbench/mlbench-core/issues/38>`__

**Merged pull requests:**

-  num\_workers fix
   `#51 <https://github.com/mlbench/mlbench-core/pull/51>`__
   (`giorgiosav <https://github.com/giorgiosav>`__)
-  Adds centralized Adam implementation
   `#41 <https://github.com/mlbench/mlbench-core/pull/41>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)

v2.3.1
^^^^^^

MLBench Core
""""""""""""

`2.3.1 <https://github.com/mlbench/mlbench-core/tree/2.3.1>`__ (2020-03-09)
---------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.3.0...2.3.1>`__

**Implemented enhancements:**

-  Customize Communication Scheme For
   Sparsified/Quantizatized/Decentralized scenarios
   `#12 <https://github.com/mlbench/mlbench-core/issues/12>`__

v2.3.0
^^^^^^

MLBench Core
""""""""""""

`v2.3.0 <https://github.com/mlbench/mlbench-core/tree/v2.3.0>`__ (2019-12-23)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.2.1...v2.3.0>`__

v2.2.1
^^^^^^

MLBench Core
""""""""""""

`v2.2.1 <https://github.com/mlbench/mlbench-core/tree/v2.2.1>`__ (2019-12-16)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.2.0...v2.2.1>`__

v2.2.0
^^^^^^

MLBench Core
""""""""""""

`v2.2.0 <https://github.com/mlbench/mlbench-core/tree/v2.2.0>`__ (2019-11-11)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.1.0...v2.1.1>`__

**Implemented enhancements:** - ``initialize_backends`` can now be
called as context manager - Improved CLI to run multiple runs in
parallel

v2.1.1
^^^^^^

MLBench Core
""""""""""""

`v2.1.1 <https://github.com/mlbench/mlbench-core/tree/v2.1.1>`__ (2019-11-11)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.1.0...v2.1.1>`__

v2.1.0
^^^^^^

MLBench Core
""""""""""""

`v2.1.0 <https://github.com/mlbench/mlbench-core/tree/v2.1.0>`__ (2019-11-4)
----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.0.0...v2.1.0>`__

**Implemented enhancements:**

-  Added CLI for MLBench runs

v2.0.0
^^^^^^

MLBench Core
""""""""""""

`v2.0.0 <https://github.com/mlbench/mlbench-core/tree/v2.0.0>`__ (2019-06-13)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.4...v2.0.0>`__

v1.4.4
^^^^^^

MLBench Core
""""""""""""

`v1.4.4 <https://github.com/mlbench/mlbench-core/tree/v1.4.4>`__ (2019-05-28)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.3...v1.4.4>`__

v1.4.3
^^^^^^

MLBench Core
""""""""""""

`v1.4.3 <https://github.com/mlbench/mlbench-core/tree/v1.4.3>`__ (2019-05-23)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.2...v1.4.3>`__

v1.4.2
^^^^^^

MLBench Core
""""""""""""

`v1.4.2 <https://github.com/mlbench/mlbench-core/tree/v1.4.2>`__ (2019-05-21)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.1...v1.4.2>`__

v1.4.1
^^^^^^

MLBench Core
""""""""""""

`v1.4.1 <https://github.com/mlbench/mlbench-core/tree/v1.4.1>`__ (2019-05-16)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.0...v1.4.1>`__

v1.4.0
^^^^^^

MLBench Core
""""""""""""

`v1.4.0 <https://github.com/mlbench/mlbench-core/tree/v1.4.0>`__ (2019-05-02)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.4...v1.4.0>`__

**Implemented enhancements:**

-  Split Train and Validation in Tensorflow
   `#22 <https://github.com/mlbench/mlbench-core/issues/22>`__


v1.3.4
^^^^^^

MLBench Core
""""""""""""

`v1.3.4 <https://github.com/mlbench/mlbench-core/tree/v1.3.4>`__ (2019-03-20)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.3...v1.3.4>`__

**Implemented enhancements:**

-  in controlflow, don't mix train and validation
   `#20 <https://github.com/mlbench/mlbench-core/issues/20>`__

**Fixed bugs:**

-  Add metrics logging for Tensorflow
   `#19 <https://github.com/mlbench/mlbench-core/issues/19>`__

v1.3.3
^^^^^^

MLBench Core
""""""""""""

`v1.3.3 <https://github.com/mlbench/mlbench-core/tree/v1.3.3>`__ (2019-02-26)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.2...v1.3.3>`__

v1.3.2
^^^^^^

MLBench Core
""""""""""""

`v1.3.2 <https://github.com/mlbench/mlbench-core/tree/v1.3.2>`__ (2019-02-13)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.1...v1.3.2>`__

v1.3.1
^^^^^^

MLBench Core
""""""""""""

`v1.3.1 <https://github.com/mlbench/mlbench-core/tree/v1.3.1>`__ (2019-02-13)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.0...v1.3.1>`__

v1.3.0
^^^^^^

MLBench Core
""""""""""""

`v1.3.0 <https://github.com/mlbench/mlbench-core/tree/v1.3.0>`__ (2019-02-12)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.2.1...v1.3.0>`__

v1.2.1
^^^^^^

MLBench Core
""""""""""""

`v1.2.1 <https://github.com/mlbench/mlbench-core/tree/v1.2.1>`__ (2019-01-31)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.2.0...v1.2.1>`__

v1.2.0
^^^^^^

MLBench Core
""""""""""""

`v1.2.0 <https://github.com/mlbench/mlbench-core/tree/v1.2.0>`__ (2019-01-30)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.1.1...v1.2.0>`__

v1.1.1
^^^^^^

MLBench Core
""""""""""""

`v1.1.1 <https://github.com/mlbench/mlbench-core/tree/v1.1.1>`__ (2019-01-09)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.1.0...v1.1.1>`__

v1.1.0
^^^^^^

MLBench Core
""""""""""""

`v1.1.0 <https://github.com/mlbench/mlbench-core/tree/v1.1.0>`__ (2018-12-06)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.0.0...v1.1.0>`__

**Fixed bugs:**

-  Bug when saving checkpoints
   `#13 <https://github.com/mlbench/mlbench-core/issues/13>`__

**Implemented enhancements:**

-  Adds Tensorflow Controlflow, Dataset and Model code
-  Adds Pytorch linear models
-  Adds sparsified and decentralized optimizers

MLBench Benchmarks
""""""""""""""""""

**Implemented enhancements:**

-  Added Tensorflow Benchmark

MLBench Dashboard
"""""""""""""""""

**Implemented enhancements:**

- Added new Tensorflow Benchmark Image
- Remove Bandwidth limiting
- Added ability to run custom images in dashboard

MLBench Helm
""""""""""""

Nothing

v1.0.0
^^^^^^

MLBench Core
""""""""""""

`1.0.0 <https://github.com/mlbench/mlbench-core/tree/1.0.0>`__ (2018-11-15)
---------------------------------------------------------------------------

**Implemented enhancements:**

-  Add API Client to mlbench-core
   `#6 <https://github.com/mlbench/mlbench-core/issues/6>`__
-  Move to google-style docs
   `#4 <https://github.com/mlbench/mlbench-core/issues/4>`__
-  Add Imagenet Dataset for pytorch
   `#3 <https://github.com/mlbench/mlbench-core/issues/3>`__
-  Move worker code to mlbench-core repo
   `#1 <https://github.com/mlbench/mlbench-core/issues/1>`__

v0.1.0
^^^^^^

Main Repo
"""""""""

`0.1.0 <https://github.com/mlbench/mlbench/tree/0.1.0>`__ (2018-09-14)
----------------------------------------------------------------------

**Implemented enhancements:**

-  Add documentation in reference implementation to docs
   `#46 <https://github.com/mlbench/mlbench/issues/46>`__
-  Replace cAdvisor with Kubernetes stats for Resource usage
   `#38 <https://github.com/mlbench/mlbench/issues/38>`__
-  Rename folders `#31 <https://github.com/mlbench/mlbench/issues/31>`__
-  Change docker image names
   `#30 <https://github.com/mlbench/mlbench/issues/30>`__
-  Add continuous output for mpirun
   `#27 <https://github.com/mlbench/mlbench/issues/27>`__
-  Replace SQlite with Postgres
   `#25 <https://github.com/mlbench/mlbench/issues/25>`__
-  Fix unittest `#23 <https://github.com/mlbench/mlbench/issues/23>`__
-  Add/Fix CI/Automated build
   `#22 <https://github.com/mlbench/mlbench/issues/22>`__
-  Cleanup unneeded project files
   `#21 <https://github.com/mlbench/mlbench/issues/21>`__
-  Remove hardcoded values
   `#20 <https://github.com/mlbench/mlbench/issues/20>`__
-  Improves Notes.txt
   `#19 <https://github.com/mlbench/mlbench/issues/19>`__
-  Rename components
   `#15 <https://github.com/mlbench/mlbench/issues/15>`__

**Fixed bugs:**

-  504 Error when downloading metrics for long runs
   `#61 <https://github.com/mlbench/mlbench/issues/61>`__

**Closed issues:**

-  small doc improvements for first release
   `#54 <https://github.com/mlbench/mlbench/issues/54>`__
-  Check mlbench works on Google Cloud
   `#51 <https://github.com/mlbench/mlbench/issues/51>`__
-  learning rate scheduler
   `#50 <https://github.com/mlbench/mlbench/issues/50>`__
-  Add Nvidia k8s-device-plugin to charts
   `#48 <https://github.com/mlbench/mlbench/issues/48>`__
-  Add Weave to Helm Chart
   `#41 <https://github.com/mlbench/mlbench/issues/41>`__
-  Allow limiting of resources for experiments
   `#39 <https://github.com/mlbench/mlbench/issues/39>`__
-  Allow downloading of Run measurements
   `#35 <https://github.com/mlbench/mlbench/issues/35>`__
-  Worker Details page
   `#33 <https://github.com/mlbench/mlbench/issues/33>`__
-  Run Visualizations
   `#32 <https://github.com/mlbench/mlbench/issues/32>`__
-  Show experiment history in Dashboard
   `#18 <https://github.com/mlbench/mlbench/issues/18>`__
-  Show model progress in Dashboard
   `#13 <https://github.com/mlbench/mlbench/issues/13>`__
-  Report cluster status in Dashboard
   `#12 <https://github.com/mlbench/mlbench/issues/12>`__
-  Send metrics from SGD example to metrics api
   `#11 <https://github.com/mlbench/mlbench/issues/11>`__
-  Add metrics endpoint for experiments
   `#10 <https://github.com/mlbench/mlbench/issues/10>`__
-  Let Coordinator Dashboard start a distributed Experiment
   `#9 <https://github.com/mlbench/mlbench/issues/9>`__
-  Add mini-batch SGD model experiment
   `#8 <https://github.com/mlbench/mlbench/issues/8>`__

\* *This Change Log was automatically generated by
`github\_changelog\_generator <https://github.com/skywinder/Github-Changelog-Generator>`__*
