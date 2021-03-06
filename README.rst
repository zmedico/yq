yq: Command-line YAML processor - jq wrapper for YAML documents
===============================================================

Installation
------------
::

    pip install yq

Before using ``yq``, you also have to install its dependency, ``jq``. See the `jq installation instructions
<https://stedolan.github.io/jq/download/>`_ for details and directions specific to your platform.

Synopsis
--------

``yq``'s mode of operation is simple: it transcodes YAML on standard input to JSON (using ``yaml.safe_load`` to avoid
dangerous vulnerabilities in YAML/PyYAML design) and pipes it to ``jq``::

    cat input.yml | yq .foo.bar

Or specify the filename directly::

    yq .foo.bar input.yml

By default, no transcoding of ``jq`` output is done. Specify the ``--yaml-output``/``-y`` option to transcode it back
into YAML (using ``yaml.safe_dump``)::

    cat input.yml | yq -y .foo.bar

Use the ``--width``/``-w`` argument to pass the line wrap width for string literals.

All other command line arguments are forwarded to ``jq``. ``yq`` forwards the exit code ``jq`` produced,
unless there was an error in YAML parsing, in which case the exit code is 1. See the `jq manual
<https://stedolan.github.io/jq/manual/>`_ for more details on ``jq`` features and options.

.. admonition:: Compatibility note

 This package's release series available on PyPI begins with version 2.0.0. Versions of ``yq`` prior to 2.0.0 are
 distributed by https://github.com/abesto/yq and are not related to this package. No guarantees of compatibility are
 made between abesto/yq and kislyuk/yq. This package follows the `Semantic Versioning 2.0.0 <http://semver.org/>`_
 standard. To ensure proper operation, declare dependency version ranges according to SemVer.

Authors
-------
* Andrey Kislyuk

Links
-----
* `Project home page (GitHub) <https://github.com/kislyuk/yq>`_
* `Documentation (Read the Docs) <https://yq.readthedocs.io/en/latest/>`_
* `Package distribution (PyPI) <https://pypi.python.org/pypi/yq>`_
* `Change log <https://github.com/kislyuk/yq/blob/master/Changes.rst>`_

Bugs
~~~~
Please report bugs, issues, feature requests, etc. on `GitHub <https://github.com/kislyuk/yq/issues>`_.

License
-------
Licensed under the terms of the `Apache License, Version 2.0 <http://www.apache.org/licenses/LICENSE-2.0>`_.

.. image:: https://img.shields.io/travis/kislyuk/yq.svg
        :target: https://travis-ci.org/kislyuk/yq
.. image:: https://codecov.io/github/kislyuk/yq/coverage.svg?branch=master
        :target: https://codecov.io/github/kislyuk/yq?branch=master
.. image:: https://img.shields.io/pypi/v/yq.svg
        :target: https://pypi.python.org/pypi/yq
.. image:: https://img.shields.io/pypi/l/yq.svg
        :target: https://pypi.python.org/pypi/yq
.. image:: https://readthedocs.org/projects/yq/badge/?version=latest
        :target: https://yq.readthedocs.io/
