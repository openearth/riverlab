===========================
Feature development
===========================
:Authors:
    Koen D. Berends
:Version: 1.0 of 16/01/2019


In this tutorial we are going to add the roughness formula of Järvelä (2004) and Västilä & Järvelä (2017) to the Delft3D FM source code. We will then build a model which is subsequently tested against experimental data, to test whether our implementation was done correctly. Finally, we prepare a validation document detailing both our proposed new feature and validation results, which will be submitted for review by Deltares. 
If the new feature was correctly implemented, does not break other functionality and is well validated, the new feature will be considered for implementation in the trunk (i.e., staged for release). 


Ingredients
===========================

- version control (see ...)
- Tools necessary to build & modify code (i.e. an IDE, compiler). 
- an oss.deltares.nl account (see ...)

Overview of steps and resources
===========================

.. image:: img/workflow_newfeature.png


First steps: preparation
===========================

Requesting a new branch of the source code
---------------------------

In this walkthrough we're going to make modification to the source code. Within the Riverlab framework, you can request a new branch in which you can safely commit your changes. If your are unfamiliar with terms like *branch* or *commit*, now is a good time to read up on the basics of (SVN) version control.

You can request a new branch by sending an email to `riverlab@deltares.nl <mailto:riverlab@deltares.nl>`_. In your email, include the following information: name of your institution and name of the project. From the project name it should be clear what you intend to modify. In our case, the institution is "Aalto University" and project is "Jarvela_vegetation". Our branch is: "https://svn.oss.deltares.nl/repos/delft3d/branches/research/Aalto University/20190111_Jarvela_vegetation". 

Important to know about this branch

 - Everyone with an oss.deltares.nl account has read-access to this branch by default. 
 - Only you will have write-access


Checking out the source code
---------------------------
Use your favourite SVN client to checkout your branch to your local machine. 


Checkout the testmodels
---------------------------
An overview of test models is available from the `Riverlab website <https://oss.deltares.nl/web/riverlab-models/models>`_. All models, including the testmodels, are under version control at the following SVN server: https://svn.oss.deltares.nl/repos/openearthmodels/trunk/riverlab/testcases/


[Optional] add a new testmodel
---------------------------
Often when you implement new functionality, existing test models will not be sufficient to validate your implementation. In such cases, you need to build a new test model. Just as with the source code, you can take advantage of version control for model development. If you followed the previous steps, you already checked out the existing riverlab testmodels to your local machine. To add a new test model, you may add a new folder and commit your files to this folder. It is important to follow the naming conventions:

:: 
	\testcases

This is the top directory

:: 
	\testcases\f[#]_[name]	

These folders contain testcases for specific functionality. If you add a new one, replace # with the next number in the folder (e.g. if the previous was names 'f20_openchannelflow' then yours will begin with 'f21_...'). Use a descriptive name. 

In our case, the previous testcase was [f29_mor1d2d_morfologie] and we will add functionality regarding a vegetation model. Therefore, we name add the folder [f30_aalto_vegetation_models].

::
	\testcases\f[#]_[name]\c[#]_name

These folders contain testcases. Each testcase should have at least the following data: the Delft3D FM model files (input only, no output!) and the validation document. All model files are stored in this directory

::
	\testcases\f[#]_[name]\c[#]_name\doc

This directory contains the source code (LaTeX) of the validation document. Each testcase validates a certain claim about (a newly implemented part of) the software. For example, in our case we will claim that the numerical model is able to reproduce laboratory experiments under a set of given conditions. The validation document details the purpose of this testcase, the linked claims, the test approach, model setup, results and conclusions. 

Sometimes you will have multiple testcases that are very similar, e.g. the same experimental setup but with different boundary conditions. In such cases, you may bundle your results in one validation document. In this case, include a readme.txt which includes the location of the bundled validation document. 
	

Test-driven development
===========================
Once your 




