.. _PEP-517: https://www.python.org/dev/peps/pep-0517/
.. _PEP-518: https://www.python.org/dev/peps/pep-0518/
.. _PEP-621: https://www.python.org/dev/peps/pep-0621/
.. _PEP-660: https://www.python.org/dev/peps/pep-0660/
.. _SO_660: https://stackoverflow.com/a/69711730
.. _Packaging-Guide: https://packaging.python.org/en/latest/specifications/core-metadata/#core-metadata-specifications
.. _Setuptools-Configuration: https://setuptools.pypa.io/en/latest/userguide/declarative_config.html
.. _Setuptools-Issue_Setup_cfg: https://github.com/pypa/setuptools/issues/1688

The pyproject.toml File
========================

.. post:: Feb 26, 2022
   :tags: programming, dev-environment, python
   :category:
   :author: Lukas Schütz <leschtz>

Introduction
--------------

Over the years, the ``setup.py`` added a multitude of issues with the build system of python.
``setuptools`` tried to fix such issues, however it became dominant and any project not using it had it as dependency in the end, because any requirements may have used it. 


Difference of ``pyproject.toml``, ``setup.py`` and ``setup.cfg``
----------------------------------------------------------------

To my understanding, the ``setup.cfg`` file is a configuration file defined by the setuptools project. An example can be found at Setuptools-Configuration_. PEP-518_ aimed to remove this issue, by creating a defined file format, which could be used by any other packaging tool, like flutter or poetry. With regards to setuptools compatibility, in Setuptools-Issue_Setup_cfg_ was discussed how to change to the standardized approach.


``pyproject.toml`` is similar to the non-officially standardized ``setup.cfg`` file, trying to resolve several issues of the ini file format used. In the original PEP, reasoning is given, why the file defined by the setuptools is not suitable for packaging. 

``setup.py`` was still needed to enable editable installs. There have been lengthy discussion about this. PEP-660_ aims to change this for ``pyproject.toml``. SO_660_ refers to some links about tool integration status.

Personal Notes
-----------------

For me, it looks like I can purely rely on ``pyproject.toml`` in the future. Tools like the black code formatter already support it. Therefor most configuration can be stored in a single file and my repositories do not get filled up with configuration files anymore.

Example ``pyproject.toml``
---------------------------

This example file is directly taken from PEP-621_.

.. literalinclude:: _examples/pyproject.toml
   :language: python
   :linenos:

Important Links
-----------------

PEP-517_ defines the Table name [build-system] and why it is needed.

PEP-518_ defines the ``pyproject.toml`` data format.

PEP-621_ defines the Table name [project] of ``pyproject.toml``. Its purpose is to store project metadata in the file. Such metadata is already known from ``setup.py`` keyword arguments to the function ``setup.py``

PEP-660_ defines editable installs for ``pyproject.toml`` based builds.

Packaging-Guide_ elaborates on the core metadata.