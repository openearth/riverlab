Model downloading and uploading
===========================

:Authors:
    Aukje Spruyt
:Version: 1.0 of 24/01/2019

In this tutorial we describe how you can download a model and upload changes.

First steps: downloading and uploading a model
===========================
All models within the RiverLab are available via `OpenEarth models <https://publicwiki.deltares.nl/display/OET/>`_. This means that the models are stored in a Subversion system (repository), and everyone can download, adapt and upload them in such a way that all steps are traceable (and reversible). This is analogue to the way the open source software is maintained and developed. You only need to subscribe once. Here is exactly described which steps you have to take to download, adapt and upload the models.

Request your username and password first
---------------------------
To join the OpenEarth community request a free username and password by signing up at http://oss.deltares.nl (link in upper right corner). You only need a valid email address.

Follow this five step guideline to making your first contribution
---------------------------
1. Install TortoiseSVN to your computer
  - Download open source Subversion (SVN) client: `TortoiseSVN <https://tortoisesvn.net/downloads.html>`_ 
  - Install TortoiseSVN to your PC (you must reboot before proceeding).
2. Create local folder on your PC for (all) your repository **checkouts**
  - Create a source code checkout directory on your PC. For instance: D:\\checkouts\\RiverLab\\
  - In any file explorer (Total Commander recommended) right-click (hold for 1 second) and select *SVNCheckout*
  - Enter the url of the (OpenEarth) repository you want to use. You can find the url you want by **browsing** the repository with a regular web-browser, and copying the url from the address bar. e.g. 
   - <https://svn.oss.deltares.nl/repos/openearthmodels/trunk/riverlab>
    - For checkout-depth choose 'fully recursive' for a specific model.
    - Choose **HEAD revision** (this is the main RiverLab trunk that is continuously being improved, so please stay updated).
3. Enter your subversion username and password
4. Perform an SVN **update** regularly to benefit from updates by co-developers.
  - Right-mouse click on the root directory of your check-out, and choose 'SVN Update'.
  - There is a separate `tutorial <https://tortoisesvn.net/docs/nightly/TortoiseSVN_en/tsvn-qs-basics.html>`_ for dealing with Subversion
5. Commit your updates to the repository regularly. 
  - Right-mouse click on the root directory of your check-out, and choose 'SVN commit ...'.
  - Do not commit all your updates at once. Commit only one coherent subset at a time, and provide a concise one-line description, to make clear to co-developers what you did. You can see where commits are required where the file/dir icons display a red !-mark, rather then a green v-mark. Note: these handy icons only show up after enabling "Show overlay icons", see above.
  - Do not commit models that are partly finished, only commit working models, because the RiverLab should always consists of models that can be run.
  - Right-mouse click on the root directory of your check-out, and choose 'TortoiseSVN >' and then choose from the sub-menu for more advanced options.
  - Adding/removing/deleting complete files or directories needs to be done via SVN and **NOT** via your file browser as TotalCommander.

Do's and don'ts
===========================
1. When adding a new model, please obey the **naming conventions**, see <https://svn.oss.deltares.nl/repos/openearthmodels/trunk/riverlab/Naming_convention.txt>.
2. **Clean up** your model before committing it in Subversion.
3. Only add the **inputfiles** from the model itself and not the generated outputfiles from a computation.
4. Provide a **clear description** of the model in a seperate document (in the directory 'doc'). For a real world model this should at least contain:
  - Description of the area that is covered by the model (including xy-coordinates combined with a coordinate system)
  - Version number of the software that is suitable to run the model.
  - Intended use of the model (hydrodynamics, morpholgy, short-term/long term etc.)
  For a schematic case this should be the validation document.
