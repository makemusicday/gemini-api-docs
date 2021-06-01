Contributing
============

Anyone is welcome to contribute fixes and enhancements to this project. We use:

- tox_ to run the test suite and linters for the Python API

  - for Python testing, we use pytest_

  - for Python linting, we use pylint_

Any pull request that modifies module code and has new functionality that does
not include tests will be blocked until tests have been written for it.


Help Wanted
-----------

The following areas are where help is currently needed:

- Creating a test suite for the React frontend

- Filling out the test suite for the Python API to get near total coverage


Contributors
------------

A big "Thank You!" to all those who have contributed to `Gemini`_ and to the
`Gemini Documentation`_.


Testing Python
--------------

Once you have written your new feature into the API, and have created a test for it,
please run the test suite and fix any lint. In order to run tests, you must have
tox_ installed::

     pip install tox

Then you can run both the tests and the linting by simply typing from the
``<gemini-repo>/src/api`` directory::

     tox

Tox will create a virtual environment specifically for testing, so if you have added
requirements, ensure that they are listed in the ``<gemini-repo>/src/api/requirements.txt``
file.

If it is a requirement only for testing, it should be listed in the appropriate section
of the ``<gemini-repo>/src/api/tox.ini`` file.

.. note:: Please, ensure that your tests pass before submitting a PR.


Documentation
-------------

You do *not* need to create a virtual environment with all of the Gemini dependencies
to update this documentation. Install the requirements listed in the
``<docs-repo>/requirements-docs.txt`` file, and make your documentation changes. To preview
the documentation, run::

    make html

and then open the index file at ``<docs-repo>/_build/index.html`` in a browser to verify that
your changes are working before you submit a PR for this documentation.


.. _tox: https://tox.readthedocs.io/en/latest/
.. _pytest: https://docs.pytest.org/en/latest/
.. _pylint: https://pylint.readthedocs.io/en/latest/
.. _XY Feng: https://github.com/xyfeng
.. _Delmar: https://github.com/delmar
.. _Jared McKnight: https://github.com/jnhmcknight
.. _Gemini: https://github.com/makemusicday/gemini/graphs/contributors
.. _Gemini Documentation: https://github.com/makemusicday/gemini-api-docs/graphs/contributors
