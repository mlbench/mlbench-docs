Change Log
==========

MLBench Core
^^^^^^^^^^^^

v3.0.0
""""""

`v3.0.0 <https://github.com/mlbench/mlbench-core/tree/v3.0.0>`__ (2020-12-07)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.4.0...v3.0.0>`__

**Implemented enhancements:**

-  Support multiple clusters in CLI
   `#91 <https://github.com/mlbench/mlbench-core/issues/91>`__
-  Add notebook/code to visualize results
   `#72 <https://github.com/mlbench/mlbench-core/issues/72>`__
-  Support AWS in CLI
   `#33 <https://github.com/mlbench/mlbench-core/issues/33>`__
-  Fix rnn language model
   `#303 <https://github.com/mlbench/mlbench-core/pull/303>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Transformer language translation
   `#99 <https://github.com/mlbench/mlbench-core/pull/99>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)

**Fixed bugs:**

-  Training code keeps running for PyTorch after training is done
   `#26 <https://github.com/mlbench/mlbench-core/issues/26>`__

**Closed issues:**

-  Remove loss argument for metric computation
   `#295 <https://github.com/mlbench/mlbench-core/issues/295>`__
-  Update PyTorch to 1.7
   `#286 <https://github.com/mlbench/mlbench-core/issues/286>`__
-  Refactor optimizer and chose more appropriate names
   `#284 <https://github.com/mlbench/mlbench-core/issues/284>`__
-  fails to create kind cluster
   `#277 <https://github.com/mlbench/mlbench-core/issues/277>`__
-  Refactor CLI
   `#253 <https://github.com/mlbench/mlbench-core/issues/253>`__
-  Dependabot couldn't authenticate with https://pypi.python.org/simple/
   `#252 <https://github.com/mlbench/mlbench-core/issues/252>`__
-  Unify requirements/setup.py versions
   `#244 <https://github.com/mlbench/mlbench-core/issues/244>`__
-  isort failing on all PRs
   `#227 <https://github.com/mlbench/mlbench-core/issues/227>`__
-  torch.div is not supported in PyTorch 1.6
   `#223 <https://github.com/mlbench/mlbench-core/issues/223>`__
-  Refactor common functionality for tiller and helm
   `#108 <https://github.com/mlbench/mlbench-core/issues/108>`__
-  Add GPU support for AWS in CLI
   `#104 <https://github.com/mlbench/mlbench-core/issues/104>`__
-  Change CPU limit to #CPUs - 1
   `#101 <https://github.com/mlbench/mlbench-core/issues/101>`__
-  Add --version flag
   `#97 <https://github.com/mlbench/mlbench-core/issues/97>`__
-  Cluster creation/deletion errors with non-default zone
   `#94 <https://github.com/mlbench/mlbench-core/issues/94>`__
-  Add command to list runs
   `#86 <https://github.com/mlbench/mlbench-core/issues/86>`__
-  RefreshError from gcloud
   `#83 <https://github.com/mlbench/mlbench-core/issues/83>`__
-  Run new benchmarks and document costs
   `#82 <https://github.com/mlbench/mlbench-core/issues/82>`__
-  Make nvidia k80 default GPU
   `#80 <https://github.com/mlbench/mlbench-core/issues/80>`__
-  Fix random seeds
   `#79 <https://github.com/mlbench/mlbench-core/issues/79>`__
-  benchmark against torch.nn.parallel.DistributedDataParallel MPSG
   `#75 <https://github.com/mlbench/mlbench-core/issues/75>`__
-  upgrade to pytorch 1.5
   `#74 <https://github.com/mlbench/mlbench-core/issues/74>`__
-  Provide comparison to competitors
   `#66 <https://github.com/mlbench/mlbench-core/issues/66>`__
-  Add some integration tests
   `#64 <https://github.com/mlbench/mlbench-core/issues/64>`__
-  Remove stale branches
   `#62 <https://github.com/mlbench/mlbench-core/issues/62>`__
-  Add PowerSGD optimizer
   `#59 <https://github.com/mlbench/mlbench-core/issues/59>`__
-  Add RNN Language Model
   `#54 <https://github.com/mlbench/mlbench-core/issues/54>`__
-  Use torch.nn.DataParallel for intra-node computation
   `#46 <https://github.com/mlbench/mlbench-core/issues/46>`__
-  Add CLI support for DIND
   `#42 <https://github.com/mlbench/mlbench-core/issues/42>`__
-  Port over functionality from Language Model benchmark to the core
   library `#34 <https://github.com/mlbench/mlbench-core/issues/34>`__
-  make results reproducible from command-line
   `#24 <https://github.com/mlbench/mlbench-core/issues/24>`__
-  Contribution and docs section on README.md
   `#17 <https://github.com/mlbench/mlbench-core/issues/17>`__
-  test new torch.distributed
   `#15 <https://github.com/mlbench/mlbench-core/issues/15>`__

**Merged pull requests:**

-  Bugfix KIND cli
   `#307 <https://github.com/mlbench/mlbench-core/pull/307>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Update README.md to show new badge
   `#306 <https://github.com/mlbench/mlbench-core/pull/306>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Create manual.yml
   `#305 <https://github.com/mlbench/mlbench-core/pull/305>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Switch to github actions
   `#304 <https://github.com/mlbench/mlbench-core/pull/304>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump sphinx from 3.3.0 to 3.3.1
   `#301 <https://github.com/mlbench/mlbench-core/pull/301>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Remove loss from metric argument
   `#297 <https://github.com/mlbench/mlbench-core/pull/297>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Fix translators
   `#294 <https://github.com/mlbench/mlbench-core/pull/294>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Update pytorch
   `#292 <https://github.com/mlbench/mlbench-core/pull/292>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump sphinx from 3.2.1 to 3.3.0 in /docs
   `#288 <https://github.com/mlbench/mlbench-core/pull/288>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Refactor optimizers
   `#285 <https://github.com/mlbench/mlbench-core/pull/285>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump isort from 5.5.4 to 5.6.4
   `#283 <https://github.com/mlbench/mlbench-core/pull/283>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Bump sphinx-autoapi from 1.5.0 to 1.5.1
   `#280 <https://github.com/mlbench/mlbench-core/pull/280>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Add gpu functionality on AWS
   `#278 <https://github.com/mlbench/mlbench-core/pull/278>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Catch exceptions when creating/deleting clusters
   `#276 <https://github.com/mlbench/mlbench-core/pull/276>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Fix doc `#275 <https://github.com/mlbench/mlbench-core/pull/275>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Fix AWS deployment
   `#274 <https://github.com/mlbench/mlbench-core/pull/274>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Create dependabot.yml
   `#260 <https://github.com/mlbench/mlbench-core/pull/260>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Merge requirements & Update doc
   `#259 <https://github.com/mlbench/mlbench-core/pull/259>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump google-api-python-client from 1.9.3 to 1.12.1
   `#246 <https://github.com/mlbench/mlbench-core/pull/246>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump numpy from 1.19.0 to 1.19.2
   `#245 <https://github.com/mlbench/mlbench-core/pull/245>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump boto3 from 1.14.6 to 1.14.50
   `#234 <https://github.com/mlbench/mlbench-core/pull/234>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Fix isort errors
   `#233 <https://github.com/mlbench/mlbench-core/pull/233>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Bump pytest-mock from 3.1.1 to 3.3.1
   `#231 <https://github.com/mlbench/mlbench-core/pull/231>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump isort from 4.3.21 to 5.4.2
   `#221 <https://github.com/mlbench/mlbench-core/pull/221>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinx from 3.0.4 to 3.2.1
   `#220 <https://github.com/mlbench/mlbench-core/pull/220>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump grpcio from 1.29.0 to 1.31.0
   `#207 <https://github.com/mlbench/mlbench-core/pull/207>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump spacy from 2.3.0 to 2.3.2
   `#182 <https://github.com/mlbench/mlbench-core/pull/182>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Downgrade Sphinx
   `#162 <https://github.com/mlbench/mlbench-core/pull/162>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add developer docs
   `#161 <https://github.com/mlbench/mlbench-core/pull/161>`__
   (`Panaetius <https://github.com/Panaetius>`__)
-  Fp optimizer changes
   `#160 <https://github.com/mlbench/mlbench-core/pull/160>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump wcwidth from 0.1.9 to 0.2.5
   `#156 <https://github.com/mlbench/mlbench-core/pull/156>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump all versions and add doc test
   `#152 <https://github.com/mlbench/mlbench-core/pull/152>`__
   (`Panaetius <https://github.com/Panaetius>`__)
-  Bump torchvision from 0.6.0 to 0.6.1
   `#151 <https://github.com/mlbench/mlbench-core/pull/151>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump numpy from 1.18.5 to 1.19.0
   `#150 <https://github.com/mlbench/mlbench-core/pull/150>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump torch from 1.5.0 to 1.5.1
   `#148 <https://github.com/mlbench/mlbench-core/pull/148>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump google-auth from 1.17.2 to 1.18.0
   `#147 <https://github.com/mlbench/mlbench-core/pull/147>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinx-rtd-theme from 0.4.3 to 0.5.0
   `#144 <https://github.com/mlbench/mlbench-core/pull/144>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump spacy from 2.2.4 to 2.3.0
   `#142 <https://github.com/mlbench/mlbench-core/pull/142>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinx from 3.1.0 to 3.1.1
   `#140 <https://github.com/mlbench/mlbench-core/pull/140>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump dill from 0.3.1.1 to 0.3.2
   `#138 <https://github.com/mlbench/mlbench-core/pull/138>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Update dependencies
   `#137 <https://github.com/mlbench/mlbench-core/pull/137>`__
   (`Panaetius <https://github.com/Panaetius>`__)
-  Bump spacy from 2.2.3 to 2.2.4
   `#135 <https://github.com/mlbench/mlbench-core/pull/135>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump numpy from 1.16.6 to 1.18.5
   `#133 <https://github.com/mlbench/mlbench-core/pull/133>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump freezegun from 0.3.12 to 0.3.15
   `#129 <https://github.com/mlbench/mlbench-core/pull/129>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump tabulate from 0.8.6 to 0.8.7
   `#128 <https://github.com/mlbench/mlbench-core/pull/128>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump deprecation from 2.0.6 to 2.1.0
   `#125 <https://github.com/mlbench/mlbench-core/pull/125>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump pytest-black from 0.3.8 to 0.3.9
   `#124 <https://github.com/mlbench/mlbench-core/pull/124>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinx-rtd-theme from 0.4.2 to 0.4.3
   `#123 <https://github.com/mlbench/mlbench-core/pull/123>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinx from 1.8.1 to 3.1.0
   `#121 <https://github.com/mlbench/mlbench-core/pull/121>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump pytest-mock from 1.10.0 to 3.1.1
   `#120 <https://github.com/mlbench/mlbench-core/pull/120>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump torchtext from 0.5.0 to 0.6.0
   `#118 <https://github.com/mlbench/mlbench-core/pull/118>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump torchvision from 0.5.0 to 0.6.0
   `#117 <https://github.com/mlbench/mlbench-core/pull/117>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Adds support for multiple clusters
   `#115 <https://github.com/mlbench/mlbench-core/pull/115>`__
   (`Panaetius <https://github.com/Panaetius>`__)
-  Bump click from 7.0 to 7.1.2
   `#114 <https://github.com/mlbench/mlbench-core/pull/114>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump google-cloud-container from 0.3.0 to 0.5.0
   `#113 <https://github.com/mlbench/mlbench-core/pull/113>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump appdirs from 1.4.3 to 1.4.4
   `#112 <https://github.com/mlbench/mlbench-core/pull/112>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinxcontrib-bibtex from 0.4.0 to 1.0.0
   `#111 <https://github.com/mlbench/mlbench-core/pull/111>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinx-autoapi from 1.3.0 to 1.4.0
   `#110 <https://github.com/mlbench/mlbench-core/pull/110>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Remove unused arguments in create\_aws
   `#109 <https://github.com/mlbench/mlbench-core/pull/109>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Fix Random seeds, Add new tracker stats
   `#107 <https://github.com/mlbench/mlbench-core/pull/107>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add return\_code check in test\_cli
   `#106 <https://github.com/mlbench/mlbench-core/pull/106>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Add AWS support in CLI
   `#103 <https://github.com/mlbench/mlbench-core/pull/103>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Update test\_cli.py
   `#100 <https://github.com/mlbench/mlbench-core/pull/100>`__
   (`giorgiosav <https://github.com/giorgiosav>`__)
-  Adds a chart command to cli
   `#95 <https://github.com/mlbench/mlbench-core/pull/95>`__
   (`Panaetius <https://github.com/Panaetius>`__)
-  Add support for kind cluster creation in the CLI
   `#93 <https://github.com/mlbench/mlbench-core/pull/93>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)


v2.4.0
""""""

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
""""""

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
""""""

`2.3.1 <https://github.com/mlbench/mlbench-core/tree/2.3.1>`__ (2020-03-09)
---------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.3.0...2.3.1>`__

**Implemented enhancements:**

-  Customize Communication Scheme For
   Sparsified/Quantizatized/Decentralized scenarios
   `#12 <https://github.com/mlbench/mlbench-core/issues/12>`__

v2.3.0
""""""

`v2.3.0 <https://github.com/mlbench/mlbench-core/tree/v2.3.0>`__ (2019-12-23)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.2.1...v2.3.0>`__

v2.2.1
""""""

`v2.2.1 <https://github.com/mlbench/mlbench-core/tree/v2.2.1>`__ (2019-12-16)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.2.0...v2.2.1>`__

v2.2.0
""""""

`v2.2.0 <https://github.com/mlbench/mlbench-core/tree/v2.2.0>`__ (2019-11-11)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.1.0...v2.1.1>`__

**Implemented enhancements:** - ``initialize_backends`` can now be
called as context manager - Improved CLI to run multiple runs in
parallel

v2.1.1
""""""

`v2.1.1 <https://github.com/mlbench/mlbench-core/tree/v2.1.1>`__ (2019-11-11)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.1.0...v2.1.1>`__

v2.1.0
""""""

`v2.1.0 <https://github.com/mlbench/mlbench-core/tree/v2.1.0>`__ (2019-11-4)
----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v2.0.0...v2.1.0>`__

**Implemented enhancements:**

-  Added CLI for MLBench runs

v2.0.0
""""""

`v2.0.0 <https://github.com/mlbench/mlbench-core/tree/v2.0.0>`__ (2019-06-13)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.4...v2.0.0>`__

v1.4.4
""""""

`v1.4.4 <https://github.com/mlbench/mlbench-core/tree/v1.4.4>`__ (2019-05-28)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.3...v1.4.4>`__

v1.4.3
""""""

`v1.4.3 <https://github.com/mlbench/mlbench-core/tree/v1.4.3>`__ (2019-05-23)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.2...v1.4.3>`__

v1.4.2
""""""

`v1.4.2 <https://github.com/mlbench/mlbench-core/tree/v1.4.2>`__ (2019-05-21)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.1...v1.4.2>`__

v1.4.1
""""""

`v1.4.1 <https://github.com/mlbench/mlbench-core/tree/v1.4.1>`__ (2019-05-16)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.4.0...v1.4.1>`__

v1.4.0
""""""

`v1.4.0 <https://github.com/mlbench/mlbench-core/tree/v1.4.0>`__ (2019-05-02)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.4...v1.4.0>`__

**Implemented enhancements:**

-  Split Train and Validation in Tensorflow
   `#22 <https://github.com/mlbench/mlbench-core/issues/22>`__


v1.3.4
""""""

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
""""""

`v1.3.3 <https://github.com/mlbench/mlbench-core/tree/v1.3.3>`__ (2019-02-26)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.2...v1.3.3>`__

v1.3.2
""""""

`v1.3.2 <https://github.com/mlbench/mlbench-core/tree/v1.3.2>`__ (2019-02-13)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.1...v1.3.2>`__

v1.3.1
""""""

`v1.3.1 <https://github.com/mlbench/mlbench-core/tree/v1.3.1>`__ (2019-02-13)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.3.0...v1.3.1>`__

v1.3.0
""""""

`v1.3.0 <https://github.com/mlbench/mlbench-core/tree/v1.3.0>`__ (2019-02-12)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.2.1...v1.3.0>`__

v1.2.1
""""""

`v1.2.1 <https://github.com/mlbench/mlbench-core/tree/v1.2.1>`__ (2019-01-31)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.2.0...v1.2.1>`__

v1.2.0
""""""

`v1.2.0 <https://github.com/mlbench/mlbench-core/tree/v1.2.0>`__ (2019-01-30)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.1.1...v1.2.0>`__

v1.1.1
""""""

`v1.1.1 <https://github.com/mlbench/mlbench-core/tree/v1.1.1>`__ (2019-01-09)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-core/compare/v1.1.0...v1.1.1>`__

v1.1.0
""""""

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

v1.0.0
""""""

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


MLBench Helm
^^^^^^^^^^^^

v3.0.0
""""""

`v3.0.0 <https://github.com/mlbench/mlbench-helm/tree/v3.0.0>`__ (2020-12-07)
-----------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-helm/compare/v2.0.0...v3.0.0>`__

**Implemented enhancements:**

-  Add DIND Setup Script
   `#4 <https://github.com/mlbench/mlbench-helm/issues/4>`__
-  Add Amazon Cloud setup script
   `#3 <https://github.com/mlbench/mlbench-helm/issues/3>`__

**Closed issues:**

-  Add integration tests for newer versions of Kubernetes
   `#23 <https://github.com/mlbench/mlbench-helm/issues/23>`__
-  Add deployment on KIND rather than Minikube
   `#21 <https://github.com/mlbench/mlbench-helm/issues/21>`__
-  Use of GCloud script
   `#19 <https://github.com/mlbench/mlbench-helm/issues/19>`__
-  Can not configure NVIDIA on AWS
   `#17 <https://github.com/mlbench/mlbench-helm/issues/17>`__
-  Migrate to Kubernetes API v1
   `#15 <https://github.com/mlbench/mlbench-helm/issues/15>`__
-  Deployment on minikube requires kubernetes 1.15
   `#13 <https://github.com/mlbench/mlbench-helm/issues/13>`__
-  Remove obsolete info in ``values.yaml``
   `#12 <https://github.com/mlbench/mlbench-helm/issues/12>`__
-  mlbench worker pods not created
   `#11 <https://github.com/mlbench/mlbench-helm/issues/11>`__

**Merged pull requests:**

-  Add workflow
   `#25 <https://github.com/mlbench/mlbench-helm/pull/25>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Update to v1
   `#24 <https://github.com/mlbench/mlbench-helm/pull/24>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Update doc requirements
   `#22 <https://github.com/mlbench/mlbench-helm/pull/22>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Remove AWS and GCloud scripts
   `#20 <https://github.com/mlbench/mlbench-helm/pull/20>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Removes unused entries from values.yaml
   `#18 <https://github.com/mlbench/mlbench-helm/pull/18>`__
   (`Panaetius <https://github.com/Panaetius>`__)
-  Switch to eksctl for aws deployment
   `#16 <https://github.com/mlbench/mlbench-helm/pull/16>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Add setup script for kind with local registry
   `#14 <https://github.com/mlbench/mlbench-helm/pull/14>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)

v2.0.0
""""""

**Implemented enhancements:**

- Added GKE and AWS Setup Scripts


MLBench Dashboard
^^^^^^^^^^^^^^^^^

v3.0.0
""""""

`v3.0.0 <https://github.com/mlbench/mlbench-dashboard/tree/v3.0.0>`__ (2020-12-07)
----------------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-dashboard/compare/v2.4.1...v3.0.0>`__

**Implemented enhancements:**

-  Allow running of custom code
   `#9 <https://github.com/mlbench/mlbench-dashboard/issues/9>`__
-  Define Job resource for mpirun execution
   `#2 <https://github.com/mlbench/mlbench-dashboard/issues/2>`__
-  Create Kubernetes Job to execute mpirun
   `#1 <https://github.com/mlbench/mlbench-dashboard/issues/1>`__

**Closed issues:**

-  Add integration tests
   `#86 <https://github.com/mlbench/mlbench-dashboard/issues/86>`__
-  Dependabot couldn't authenticate with https://pypi.python.org/simple/
   `#74 <https://github.com/mlbench/mlbench-dashboard/issues/74>`__
-  Fix dashboard scheduling
   `#49 <https://github.com/mlbench/mlbench-dashboard/issues/49>`__
-  Add ability to stop run before end
   `#48 <https://github.com/mlbench/mlbench-dashboard/issues/48>`__
-  Make sure all results are well zipped
   `#44 <https://github.com/mlbench/mlbench-dashboard/issues/44>`__
-  Prevent user from inserting invalid run names
   `#28 <https://github.com/mlbench/mlbench-dashboard/issues/28>`__
-  Travis tests run only for Python 3.6
   `#24 <https://github.com/mlbench/mlbench-dashboard/issues/24>`__
-  Remove stale branches
   `#23 <https://github.com/mlbench/mlbench-dashboard/issues/23>`__

**Merged pull requests:**

-  Switch to actions
   `#121 <https://github.com/mlbench/mlbench-dashboard/pull/121>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump sphinx from 3.3.0 to 3.3.1 in /docs
   `#120 <https://github.com/mlbench/mlbench-dashboard/pull/120>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Fix stream disconnection
   `#115 <https://github.com/mlbench/mlbench-dashboard/pull/115>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Update images
   `#114 <https://github.com/mlbench/mlbench-dashboard/pull/114>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Fix integration tests
   `#113 <https://github.com/mlbench/mlbench-dashboard/pull/113>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump rq-scheduler from 0.8.3 to 0.10.0
   `#109 <https://github.com/mlbench/mlbench-dashboard/pull/109>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Bump sphinx from 3.2.1 to 3.3.0 in /docs
   `#108 <https://github.com/mlbench/mlbench-dashboard/pull/108>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Bump fakeredis from 1.4.3 to 1.4.4
   `#102 <https://github.com/mlbench/mlbench-dashboard/pull/102>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump pytest from 6.0.2 to 6.1.2
   `#101 <https://github.com/mlbench/mlbench-dashboard/pull/101>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump pytest-django from 3.10.0 to 4.1.0
   `#100 <https://github.com/mlbench/mlbench-dashboard/pull/100>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump tox from 3.20.0 to 3.20.1
   `#96 <https://github.com/mlbench/mlbench-dashboard/pull/96>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Change 'Benchmarks' to 'Benchmark Implementations'
   `#93 <https://github.com/mlbench/mlbench-dashboard/pull/93>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add integration tests
   `#91 <https://github.com/mlbench/mlbench-dashboard/pull/91>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump pytest-kind from 20.5.3 to 20.10.0
   `#89 <https://github.com/mlbench/mlbench-dashboard/pull/89>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Add tests
   `#75 <https://github.com/mlbench/mlbench-dashboard/pull/75>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bugfix `#60 <https://github.com/mlbench/mlbench-dashboard/pull/60>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Bump watchdog from 0.8.3 to 0.10.3
   `#58 <https://github.com/mlbench/mlbench-dashboard/pull/58>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump uwsgi from 2.0.17 to 2.0.19.1
   `#57 <https://github.com/mlbench/mlbench-dashboard/pull/57>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinx from 1.7.1 to 3.1.1
   `#52 <https://github.com/mlbench/mlbench-dashboard/pull/52>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump tox from 2.9.1 to 3.15.2
   `#46 <https://github.com/mlbench/mlbench-dashboard/pull/46>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump sphinx-rtd-theme from 0.4.0 to 0.4.3
   `#45 <https://github.com/mlbench/mlbench-dashboard/pull/45>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump django-constance from 2.2.0 to 2.6.0
   `#43 <https://github.com/mlbench/mlbench-dashboard/pull/43>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump pytest-black from 0.3.8 to 0.3.9
   `#42 <https://github.com/mlbench/mlbench-dashboard/pull/42>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump flake8 from 3.5.0 to 3.8.3
   `#40 <https://github.com/mlbench/mlbench-dashboard/pull/40>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump redis from 2.10.6 to 3.5.3
   `#38 <https://github.com/mlbench/mlbench-dashboard/pull/38>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump pip from 10.0.1 to 20.1.1
   `#37 <https://github.com/mlbench/mlbench-dashboard/pull/37>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump bumpversion from 0.5.3 to 0.6.0
   `#34 <https://github.com/mlbench/mlbench-dashboard/pull/34>`__
   (`dependabot-preview[bot] <https://github.com/apps/dependabot-preview>`__)
-  Bump django from 2.2.12 to 2.2.13
   `#33 <https://github.com/mlbench/mlbench-dashboard/pull/33>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Bump django from 2.2.12 to 2.2.13 in /Docker
   `#32 <https://github.com/mlbench/mlbench-dashboard/pull/32>`__
   (`dependabot[bot] <https://github.com/apps/dependabot>`__)
-  Add backend benchmark
   `#31 <https://github.com/mlbench/mlbench-dashboard/pull/31>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add transformer image
   `#30 <https://github.com/mlbench/mlbench-dashboard/pull/30>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)

v2.0.0
""""""

**Implemented enhancements:**

- Added Download of Task Goals
- Fixed some performance issues

v1.1.0
""""""

**Implemented enhancements:**

- Added new Tensorflow Benchmark Image
- Remove Bandwidth limiting
- Added ability to run custom images in dashboard


MLBench Benchmarks
^^^^^^^^^^^^^^^^^^

v3.0.0
""""""

`v3.0.0 <https://github.com/mlbench/mlbench-benchmarks/tree/v3.0.0>`__ (2020-12-07)
-----------------------------------------------------------------------------------

`Full
Changelog <https://github.com/mlbench/mlbench-benchmarks/compare/v2.0.0...v3.0.0>`__

**Implemented enhancements:**

-  Update PyTorch base to 1.7
   `#64 <https://github.com/mlbench/mlbench-benchmarks/issues/64>`__
-  Add NLP/machine translation Transformer benchmark task
   `#33 <https://github.com/mlbench/mlbench-benchmarks/issues/33>`__
-  Repair Logistic regression Model
   `#30 <https://github.com/mlbench/mlbench-benchmarks/issues/30>`__
-  Add NLP/machine translation RNN benchmark task
   `#27 <https://github.com/mlbench/mlbench-benchmarks/issues/27>`__
-  Add NLP benchmark images & task
   `#24 <https://github.com/mlbench/mlbench-benchmarks/issues/24>`__
-  Add Gloo support to PyTorch images
   `#23 <https://github.com/mlbench/mlbench-benchmarks/issues/23>`__
-  Add NCCL support to PyTorch images
   `#22 <https://github.com/mlbench/mlbench-benchmarks/issues/22>`__
-  documentation: clearly link ref code to benchmark tasks
   `#14 <https://github.com/mlbench/mlbench-benchmarks/issues/14>`__
-  Add time-to-accuracy speedup plot
   `#7 <https://github.com/mlbench/mlbench-benchmarks/issues/7>`__
-  Update GKE documentation to use kubernetes version 1.10.9
   `#4 <https://github.com/mlbench/mlbench-benchmarks/issues/4>`__
-  Add tensorflow cifar10 benchmark
   `#3 <https://github.com/mlbench/mlbench-benchmarks/issues/3>`__
-  Transformer language translation
   `#51 <https://github.com/mlbench/mlbench-benchmarks/pull/51>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)

**Fixed bugs:**

-  Change Tensorflow Benchmark to use OpenMPI
   `#8 <https://github.com/mlbench/mlbench-benchmarks/issues/8>`__

**Closed issues:**

-  Clean-up tasks
   `#63 <https://github.com/mlbench/mlbench-benchmarks/issues/63>`__
-  Support for local run
   `#59 <https://github.com/mlbench/mlbench-benchmarks/issues/59>`__
-  task implementations: delete choco, name tasks nlp/language-model and
   nlp/translation
   `#55 <https://github.com/mlbench/mlbench-benchmarks/issues/55>`__
-  remove open/closed division distinction
   `#47 <https://github.com/mlbench/mlbench-benchmarks/issues/47>`__
-  [Not an Issue] Comparing 3 backends on multi-node single-gpu env
   `#44 <https://github.com/mlbench/mlbench-benchmarks/issues/44>`__
-  Create light version of the base image for development
   `#43 <https://github.com/mlbench/mlbench-benchmarks/issues/43>`__
-  No unit tests
   `#40 <https://github.com/mlbench/mlbench-benchmarks/issues/40>`__
-  Remove stale branches
   `#39 <https://github.com/mlbench/mlbench-benchmarks/issues/39>`__
-  Remove Communication backend from image name
   `#36 <https://github.com/mlbench/mlbench-benchmarks/issues/36>`__
-  pytorch 1.4
   `#34 <https://github.com/mlbench/mlbench-benchmarks/issues/34>`__
-  create light version (in addition to full) for resource heavy
   benchmark tasks
   `#19 <https://github.com/mlbench/mlbench-benchmarks/issues/19>`__
-  add script to compute official results from raw results (time to acc
   for example)
   `#18 <https://github.com/mlbench/mlbench-benchmarks/issues/18>`__

**Merged pull requests:**

-  Add workflow
   `#68 <https://github.com/mlbench/mlbench-benchmarks/pull/68>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Fix rnn language model
   `#67 <https://github.com/mlbench/mlbench-benchmarks/pull/67>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Update pytorch
   `#65 <https://github.com/mlbench/mlbench-benchmarks/pull/65>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Adapt optimizer imports
   `#62 <https://github.com/mlbench/mlbench-benchmarks/pull/62>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Translation changes
   `#61 <https://github.com/mlbench/mlbench-benchmarks/pull/61>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Change 'Benchmarks' to 'Benchmark Implementations'
   `#60 <https://github.com/mlbench/mlbench-benchmarks/pull/60>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add generic worker
   `#58 <https://github.com/mlbench/mlbench-benchmarks/pull/58>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Rename tasks
   `#57 <https://github.com/mlbench/mlbench-benchmarks/pull/57>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add link to task description
   `#56 <https://github.com/mlbench/mlbench-benchmarks/pull/56>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Fix tasks
   `#54 <https://github.com/mlbench/mlbench-benchmarks/pull/54>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add backend benchmark code and image
   `#53 <https://github.com/mlbench/mlbench-benchmarks/pull/53>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Update nccl
   `#52 <https://github.com/mlbench/mlbench-benchmarks/pull/52>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Remove open/closed division from benchmarks
   `#49 <https://github.com/mlbench/mlbench-benchmarks/pull/49>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Pytorch 1.5.0
   `#48 <https://github.com/mlbench/mlbench-benchmarks/pull/48>`__
   (`giorgiosav <https://github.com/giorgiosav>`__)
-  Refactor controlflow
   `#46 <https://github.com/mlbench/mlbench-benchmarks/pull/46>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add Image Recognition Benchmark with DistributedDataParallel
   `#42 <https://github.com/mlbench/mlbench-benchmarks/pull/42>`__
   (`mmilenkoski <https://github.com/mmilenkoski>`__)
-  Pytorch v1.4.0
   `#41 <https://github.com/mlbench/mlbench-benchmarks/pull/41>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add aggregation by model
   `#38 <https://github.com/mlbench/mlbench-benchmarks/pull/38>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Add NCCL & GLOO support to images
   `#35 <https://github.com/mlbench/mlbench-benchmarks/pull/35>`__
   (`giorgiosav <https://github.com/giorgiosav>`__)
-  Rnn language translation
   `#32 <https://github.com/mlbench/mlbench-benchmarks/pull/32>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Linear model
   `#28 <https://github.com/mlbench/mlbench-benchmarks/pull/28>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  Fix ci
   `#26 <https://github.com/mlbench/mlbench-benchmarks/pull/26>`__
   (`ehoelzl <https://github.com/ehoelzl>`__)
-  [WIP]Add LSTM language model
   `#25 <https://github.com/mlbench/mlbench-benchmarks/pull/25>`__
   (`Panaetius <https://github.com/Panaetius>`__)


v2.0.0
""""""

**Implemented enhancements:**

- Added Goals to PyTorch Benchmark
- Updated PyTorch Tutorial code
- Changed all images to newest ``mlbench-core`` version.

v1.1.0
""""""

**Implemented enhancements:**

-  Added Tensorflow Benchmark




