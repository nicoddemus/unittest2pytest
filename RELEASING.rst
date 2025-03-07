=========================
Releasing unittest2pytest
=========================

This document describes the steps to make a new ``unittest2pytest`` release.

Version
-------

``main`` should always be green and a potential release candidate. ``unittest2pytest`` follows
semantic versioning, so given that the current version is ``X.Y.Z``, to find the next version number
one needs to look at the ``CHANGELOG.rst`` file:

- If there any new feature, then we must make a new **minor** release: next
  release will be ``X.Y+1.0``.

- Otherwise it is just a **bug fix** release: ``X.Y.Z+1``.


Steps
-----

To publish a new release ``X.Y.Z``, the steps are as follows:

#. Create a new branch named ``release-X.Y.Z`` from the latest ``main``.

#. Update the version in ``unittest2pytest/__init__.py``.

#. Update the ``CHANGELOG.rst`` file with the new release information.

#. Commit and push the branch to ``upstream`` and open a PR.

#. Once the PR is **green** and **approved**, start the ``deploy`` workflow:

   .. code-block:: console

        gh workflow run deploy.yml -R pytest-dev/unittest2pytest --ref release-VERSION --field version=VERSION

   The PR will be automatically merged.

#. Update the version in ``unittest2pytest/__init__.py`` and ``CHANGELOG.rst`` for the next release (usually use "minor+1" with the ``.dev0`` suffix).

