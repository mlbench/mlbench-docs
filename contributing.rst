.. highlight:: shell

============
Contributing
============

Contributions are welcome, and they are greatly appreciated! Every little bit
helps, and credit will always be given.

You can contribute in many ways:

Types of Contributions
----------------------

Report Bugs
~~~~~~~~~~~

Report bugs at https://github.com/mlbench/mlbench/issues.

If you are reporting a bug, please include:

* Your operating system name and version.
* Any details about your local setup that might be helpful in troubleshooting.
* Detailed steps to reproduce the bug.

Fix Bugs
~~~~~~~~

Look through the GitHub issues for bugs. Anything tagged with "bug" and "help
wanted" is open to whoever wants to implement it.

Implement Features
~~~~~~~~~~~~~~~~~~

Look through the GitHub issues for features. Anything tagged with "enhancement"
and "help wanted" is open to whoever wants to implement it.

Write Documentation
~~~~~~~~~~~~~~~~~~~

mlbench could always use more documentation, whether as part of the
official mlbench docs, in docstrings, or even on the web in blog posts,
articles, and such.

Submit Feedback
~~~~~~~~~~~~~~~

The best way to send feedback is to file an issue at https://github.com/mlbench/mlbench/issues.

If you are proposing a feature:

* Explain in detail how it would work.
* Keep the scope as narrow as possible, to make it easier to implement.
* Remember that this is a volunteer-driven project, and that contributions
  are welcome :)

Get Started!
------------

Ready to contribute? Here's how to set up `mlbench` for local development.

1. Install the Prerequisites;
2. Follow the installation guide;
3. Create a branch for local development::

    $ git checkout -b name-of-your-bugfix-or-feature

   Now you can make your changes locally.

5. When you're done making changes, check that your changes pass flake8 and the
   tests, including testing other Python versions with tox::

    $ flake8 mlbench tests
    $ python setup.py test or py.test
    $ tox

   To get flake8 and tox, just pip install them into your virtualenv.

6. Commit your changes and push your branch to GitHub::

    $ git add .
    $ git commit -m "Your detailed description of your changes."
    $ git push origin name-of-your-bugfix-or-feature

7. Submit a pull request through the GitHub website.

Pull Request Guidelines
-----------------------

Before you submit a pull request, check that it meets these guidelines:

1. The pull request should include tests.
2. If the pull request adds functionality, the docs should be updated. Put
   your new functionality into a function with a docstring, and add the
   feature to the list in README.rst.
3. The pull request should work for Python 2.7, 3.4, 3.5 and 3.6, and for PyPy. Check
   https://travis-ci.org/mlbench/mlbench/pull_requests
   and make sure that the tests pass for all supported Python versions.

Tips
----

To run a subset of tests::

$ py.test tests.test_mlbench


Deploying
---------

A reminder for the maintainers on how to deploy.
Make sure all your changes are committed (including an entry in HISTORY.rst).
Then run::

$ bumpversion patch # possible: major / minor / patch
$ git push
$ git push --tags

Repositories
------------
mlbench-core
~~~~~~~~~~~~

To contribute to mlbench-core, you first need to clone the mlbench-core repository, create a new branch for the feature, make the changes and then create a new local commit. For local development and testing, you do not need to push the changes to Github. You need to create a development release on PyPi with the changes. To do this, you need an account that has permission to do releases on the mlbench-core PyPi project. Then, inside the git repository you need to run::

$ bumpversion --verbose --allow-dirty --no-tag --no-commit dev

This will bump the version of the development release. You need to be aware that if someone else published a development release on PyPI since your last release, bumpversion will not take this into account. In this case, you need to manually bump the version. To do this, you first need to check what is the latest dev release on PyPI. Let us assume that the latest version on PyPI is ``2.4.0.dev240``. Now, you need to enter the version ``2.4.0-dev241`` in the files ``setup.py``, ``setup.cfg`` and ``mlbench_core/__init__.py``. You should also be careful that the formatting of the version in the files is different than on PyPI. However, the files will already contain some version, so you only need to change the numbering and not the formatting. After you have done this, you need to build and upload the release by running the following commands inside the git repository::

$ python setup.py sdist bdist_wheel
$ python -m twine upload dist/*

If everything is successful, you should be able to see your release on PyPI. Now, to test this release you need to go to the benchmark directory and locate the file requirements.txt. Inside, there should be a line for mlbench-core specifying the version. You should replace the version with the one you just released. In the previous example you would need to specify ``mlbench-core==2.4.0-dev241``. Depending on your changes, you may want to modify the code for the benchmark in the file ``main.py``. This is necessary for example when you add a new optimizer and you want to test the benchmark using it. In this case, you need to replace the previous optimizer with the new one in ``main.py``. After you are done with the changes, you need to build and push the docker image to Docker Hub. This can be done by running the ``docker build`` and ``docker push`` commands inside the benchmark repository. In order to be able to push to Docker Hub, you need to create an account and login using the command ``docker login``. Once you have the image on Docker Hub, you can use it as a custom image in MLBench when starting a run either through the CLI or the dashboard. When prompted for the image location, you only need to specify the repository and image name because MLBench automatically looks for the image on Docker Hub. You have to note that this procedure is only required when making changes that need to be tested by running a benchmark. For example, if you want to simply make changes in the CLI, you can modify the file ``cli.py`` and test it locally using::

$ python cli.py <specific-command>

mlbench-benchmarks
~~~~~~~~~~~~~~~~~~

MLBench offers a choice between different optimizers, learning rate schedulers etc, so you might be interested in modifying the existing benchmark implementations to use different components. To do this, you can follow a similar approach as described in the previous section. You have to clone the ``mlbench-benchmarks`` repository and modify the ``main.py`` file of the corresponding benchmark. You could also write your own implementations of some components and combine them with MLBench. You can find detailed description on the process of adapting existing PyTorch models to use with MLBench in the Tutorials section. The main focus here is the case where you want to try out different options which are not part of the official implementation, but are still available in mlbench-core. In addition to ``main.py``, you might need to modify the files ``requirements.txt`` if you use additional libraries, and the ``Dockerfile`` if you want to include additional files or require any additional setup. However, for most use cases, only the ``main.py`` file needs to be modified. Once you are done with the modification, you can follow the same procedure as in the previous section, to build and push the new image, and then use it as a custom image in MLBench.


mlbench-helm
~~~~~~~~~~~~

The MLBench installation through the CLI automatically uses the latest version of the master branch in the ``mlbench-helm`` repository. To test your own version of the helm chart without changing the master branch you first need to push your changes to a different branch in ``mlbench-helm``. Then, you need to change the file ``mlbench_core/cli/cli.py`` inside the ``mlbench-core`` repository. This file contains the CLI functionalities and you can test MLBench by running it locally. To use your own version of the helm chart, you need to locate the code for creating the ``ChartBuilder`` object in the function you want to use. MLBench has different functions for different cloud providers. For testing, you can pick one provider, find the function for creating a cluster on that provider and modify the ``ChartBuilder`` object to use your own branch. For example, let’s say that you have pushed your changes to the branch ``new-feature`` in the helm repository. Then, you should specify that branch using the ``source.reference`` parameter like this:

.. code-block:: python

chart = ChartBuilder(
            {
            "name": "mlbench-helm",
             "source": {
                 "type": "git",
                 "location": "https://github.com/mlbench/mlbench-helm"               
                 "reference": "new-feature"
                 },
             }
        )
        
Now, when you run the command for creating the cluster, it will install MLBench using your own helm chart instead of the default one. 

mlbench-dashboard
~~~~~~~~~~~~~~~~~
When you want to test changes to the dashboard you first need to build, tag the image and then push it to a repository on Docker Hub. Let’s say you want to push the image to the repository ``user/mlbench_master`` with the tag ``testing``. You can do that by running the following command inside the root of the ``mlbench-dashboard`` repository::

$ docker login
$ docker build -f Docker/Dockerfile -t user/mlbench_master:testing .
$ docker push user/mlbench_master:testing

Once you push the image, you can modify the file ``values.yaml`` in ``mlbench-helm`` to use your new image. You need to modify the values of ``master.image.repository`` and ``master.image.tag``. In our example, you would set the repository to ``user/mlbench_master`` and the tag to ``testing``. From there, you can use the instructions from the previous section to use the new chart with the CLI. Alternatively, you could skip the step of creating a branch on the helm repository and use the ``custom-value`` argument of the functions for creating clusters using the CLI. As an example, to customize the helm chart directly from the CLI, when creating a cluster on Google Cloud you could use the following command::

$ mlbench create-cluster gcloud 3 my-cluster --custom-value master.image.repository=user/mlbench_master --custom-value master.image.tag=testing

mlbench-docs
~~~~~~~~~~~~
To contribute to the documentation, you simply need to modify the relevant .rst file inside the repository and create a pull request. Once the pull request is accepted and merged, the changes will automatically be published on the website with the next release.






