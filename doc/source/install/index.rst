.. _install:

Install
=======

CVXPY supports Python 3 on Linux, macOS, and Windows. You can use
pip or conda for installation. You may want to isolate
your installation in a `virtualenv <https://virtualenv.pypa.io/en/stable/>`_,
or a conda environment.

pip
---

(Windows only) Download the Visual Studio build tools for Python 3
(`download <https://visualstudio.microsoft .com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16>`_,
`install instructions <https://drive.google.com/file/d/0B4GsMXCRaSSIOWpYQkstajlYZ0tPVkNQSElmTWh1dXFaYkJr/view?usp=sharing>`_).

(macOS only) Install the Xcode command line tools.

(optional) Create and activate a virtual environment

1. Install ``cvxpy``.
  ::

      pip install cvxpy

2. Test the installation with ``pytest``.
  ::

      pip install pytest
      pytest cvxpy/tests

.. _conda-installation:

conda
-----

`conda`_ is a system for package and environment management.

(Windows only) Download the `Visual Studio build tools for Python 3 <https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16>`_.

1. Install `conda`_.

2. Create a new conda environment,
  ::

      conda create --name cvxpy_env
      conda activate cvxpy_env

 or activate an existing one

3. Install ``cvxpy`` from `conda-forge <https://conda-forge.org/>`_
   ::

      conda install -c conda-forge cvxpy

4. Test the installation with ``pytest``.
  ::

       conda install pytest
       pytest cvxpy/tests

.. _install_from_source:

Install from source
-------------------

We strongly recommend using a fresh virtual environment (virtualenv or conda) when installing CVXPY from source.

CVXPY has the following dependencies:

 * Python >= 3.6
 * `OSQP`_ >= 0.4.1
 * `ECOS`_ >= 2
 * `SCS`_ >= 1.1.6
 * `NumPy`_ >= 1.15
 * `SciPy`_ >= 1.1.0

To test the CVXPY installation, you additionally need `pytest`_.

CVXPY automatically installs `OSQP`_, `ECOS`_, `SCS`_. `NumPy`_ and
`SciPy`_ will need to be installed manually,
as will `Swig`_ . Once you’ve installed these dependencies, perform the following steps:

 1. Clone the official `CVXPY git repository`_, or a newly minted fork of the CVXPY repository.
 2. Navigate to the top-level of the cloned directory.
 3. If you want to use CVXPY with edited source code, run
    ::

        pip install -e .

    otherwise, run
    ::

        pip install .

Install with CVXOPT and GLPK support
------------------------------------

CVXPY supports the `CVXOPT`_ solver.
Additionally, through CVXOPT, CVXPY supports the `GLPK`_ solver. On `most
platforms <http://cvxopt.org/install/index.html#installing-a-pre-built-package>`_,
`CVXOPT`_ comes with GLPK bundled. On such platforms, installing CVXOPT with

  ::

      pip install cvxopt

should suffice to get support for both CVXOPT and GLPK.

On other platforms, to install CVXPY and its dependencies with GLPK support, follow these instructions:

1. Install `GLPK <https://www.gnu.org/software/glpk/>`_. We recommend either installing the latest GLPK from source or using a package manager such as apt-get on Ubuntu and homebrew on OS X.

2. Install `CVXOPT`_ with GLPK bindings.

    ::

      CVXOPT_BUILD_GLPK=1
      CVXOPT_GLPK_LIB_DIR=/path/to/glpk-X.X/lib
      CVXOPT_GLPK_INC_DIR=/path/to/glpk-X.X/include
      pip install cvxopt

3. Follow the standard installation procedure to install CVXPY and its remaining dependencies.

Install with GUROBI support
---------------------------

CVXPY supports the GUROBI solver.
Install GUROBI version 7.5.2 or greater such that you can ``import gurobipy`` in Python.
See the `GUROBI <http://www.gurobi.com/>`_ website for installation instructions.

Install with MOSEK support
---------------------------

CVXPY supports the MOSEK solver.
Simply install MOSEK such that you can ``import mosek`` in Python.
See the `MOSEK <https://www.mosek.com/>`_ website for installation instructions.

Install with XPRESS support
---------------------------

CVXPY supports the FICO Xpress solver.
Simply install XPRESS such that you can ``import xpress`` in Python.
See the `Xpress Python documentation <https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/python/HTML/GUID-616C323F-05D8-3460-B0D7-80F77DA7D046.html>`_ pages for installation instructions.

Install with Cbc (Clp, Cgl) support
-----------------------------------
CVXPY supports the `Cbc <https://projects.coin-or.org/Cbc>`_ solver (which includes Clp and Cgl) with the help of `cylp <https://github.com/coin-or/CyLP>`_.
Simply install cylp (you will need the Cbc sources which includes `Cgl <https://projects.coin-or.org/Cbc>`_) such you can import this library in Python.
See the `cylp documentation <https://github.com/coin-or/CyLP>`_ for installation instructions.

Install with CPLEX support
--------------------------

CVXPY supports the CPLEX solver.
Simply install CPLEX such that you can ``import cplex`` in Python.
See the `CPLEX <https://www.ibm.com/support/knowledgecenter/SSSA5P>`_ website for installation instructions.

Install with SDPT3 support
--------------------------

The `sdpt3glue package <https://github.com/TrishGillett/pysdpt3glue>`_ allows you to model problems with CVXPY and solve them with SDPT3.

Install with NAG support
------------------------

CVXPY supports the NAG solver.
Simply install NAG such that you can ``import naginterfaces`` in Python.
See the `NAG <https://www.nag.co.uk/nag-library-python>`_ website for installation instructions.

Install with SCIP support
-------------------------

CVXPY supports the SCIP solver.
Simply install SCIP such that you can ``from pyscipopt.scip import Model`` in Python.
See the `PySCIPOpt <https://github.com/SCIP-Interfaces/PySCIPOpt#installation>`_ github for installation instructions.

CVXPY's SCIP interface does not reliably recover dual variables for constraints. If you require dual variables for a continuous problem, you will need to use another solver. We welcome additional contributions to the SCIP interface, to recover dual variables for constraints in continuous problems.

Install with SCIPY support
-------------------------

CVXPY supports the SCIPY solver for LPs.
This requires the `SciPy`_ package in Python which should already be installed as it is a requirement for CVXPY. `SciPy`_'s "interior-point" and "revised-simplex" implementations are written in python and are always available however the main advantage of this solver, is its ability to use the `HiGHS`_ LP solvers (which are written in C++) that comes bundled with `SciPy`_ version 1.6.1 and higher.


.. _Anaconda: https://store.continuum.io/cshop/anaconda/
.. _website: https://store.continuum.io/cshop/anaconda/
.. _conda: https://docs.conda.io/en/latest/
.. _setuptools: https://pypi.python.org/pypi/setuptools
.. _CVXOPT: http://cvxopt.org/
.. _OSQP: https://osqp.org/
.. _ECOS: http://github.com/ifa-ethz/ecos
.. _SCS: http://github.com/cvxgrp/scs
.. _NumPy: http://www.numpy.org/
.. _SciPy: http://www.scipy.org/
.. _pytest: https://docs.pytest.org/en/latest/
.. _CVXPY git repository: https://github.com/cvxgrp/cvxpy
.. _Swig: http://www.swig.org/
.. _pip: https://pip.pypa.io/
.. _GLPK: https://www.gnu.org/software/glpk/
.. _HiGHS: https://www.maths.ed.ac.uk/hall/HiGHS/#guide
