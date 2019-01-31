===========================
Compiling the source code
===========================

:Authors:
    Aukje Spruyt
:Version: 1.0 of 31/01/2019

In this tutorial we describe how you can actually compile the D-Flow FM source code.

Checkout the source code
---------------------------
Use your favourite SVN client to checkout the main development line (trunk) or your own branch to your local machine. 
This can be done in a similar way as checking out a model, see `Model management </tutorials/model_testing.rst>`_  

Compiling the source code
---------------------------
At this point, we assume you already have the source locally from the `Checkout the source code`_. To be able to compile and modify the source code, you will need to set up a development environment. It highly depends on your operating system (Windows, Linux or macOS) and available software what is best for you. The best place to start is ``src/readme``. Other resources are the `online boards <https://oss.deltares.nl/web/delft3dfm/home/-/message_boards/category/217304/maximized>`_ and workshops during the `Delft Software Days <https://softwaredays.deltares.nl>`_. 

For this example, we will compile the Delft3D FM source (revision 62958) with `Visual Studio 2012 <https://visualstudio.microsoft.com/vs/older-downloads/>`_ and `Intel Parellel Studio XE 2013 SP 1 <https://software.intel.com/en-us/intel-parallel-studio-xe-compilers-required-microsoft-visual-studio>`_, which includes C++ and Fortran compilers on Windows 7. 
Following the README we create 'solution files' for Visual Studio by running ``src/prepare_sln.py``. Note that need Python installed (and, available in your PATH variable) to run this script. We then open 'dflowfm_open.sln' with Visual Studio.

In the solution explorer, we first change the build configuration (right click on ``solution 'dflowfm_open'`` and choose ``configuration manager``) to ``release`` and ``x64``. Next,s we are going to build ``dflowfm-cli``. This builds the command line interface, including ``dflowfm-cli.exe``. We need this executable to be able to run our actual models. Note that this does not include a graphical user interface. 

.. image:: img/vs_sln_dflowfm-cli.png

To start building is as simple as -rightlick, -build, however we were not succesful to build without errors straight away. Inspection of the errors showed multiple errors related to the ``petsc`` module:

.. image:: img/vs_petsc_errors.png

`PETSc <https://www.mcs.anl.gov/petsc/>`_ is a third party application that provides an optional solver, but we cannot build this on Windows (`PETSc might be Linux only <https://oss.deltares.nl/web/delft3dfm/home/-/message_boards/category/877671/maximized>`_). To circumvent this we need to take the following steps. First, we ``unload`` it from the solution:

.. image:: img/vs_petsc_unload.png

Next, we change the configuration from ``release`` to ``debug``. This prevents the precompiler to throw many errors regarding the omission of PETSc. With these changes, we were able to successfully build ``dflowfm-cli``. The resulting libraries (``*.dll``) and executable (``dflowfm-cli.exe``) can be found under ``src/bin/x64/Debug/dflowfm``.

Test your build (Riverlab models)
---------------------------
Before modifying anything it is good practice to test your build first. We assume you already have all testmodels available in RiverLab (`Checkout the testmodels`_). We're going to try to run the test ``c01_mc_sediment_transport_Engelund_Hansen``. Navigate to this test. In this directory, open a command window and type::

	[PATH_TO_FM]/dflowfm-cli.exe --autostartstop -t 1 c01.mdu 

Depending on your computer, the model should be evaluated in about 10-15 seconds. We used the following flags: ``--autostartstop`` starts the model run and exits after completion, ``-t 1`` specifies that model should be run in a single thread and ``c01.mdu`` is the model configuration file. After the model has run, you should be able to see the ``dflowfmoutput`` folder. You can inspect the output (``*.nc`` files).
