Model execution
===========================

:Authors:
    Aukje Spruyt
:Version: 1.0 of 25/01/2019

In this tutorial we describe how you can actually run your D-Flow FM 1D model.

Obtaining the software
=============================
Obtain the appropriate software version to run the model. 
This can be done by downloading the source code and `compiling </tutorials/compile_sourcecode.rst>`_ it.

Running the model
=============================
Navigate to the directory with the .mdu-file of your model. In this directory, open a command window and type::

	[PATH_TO_FM]/dflowfm-cli.exe --autostartstop -t 1 c01.mdu > output.log

We used the following flags: ``--autostartstop`` starts the model run and exits after completion, 
``-t 1`` specifies that model should be run in a single thread, 
``c01.mdu`` is the model configuration file and ``output.log`` the file to which logging information is written. 
After the model has run, you should be able to see the ``dflowfmoutput`` folder. You can inspect the output (``*.nc`` files).
