Setup
=====

Installing pylim
----------------

Installing and using pylim from GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you only want to use the functions available and install pylim like a normal python package this is all you need to do:

1. On your machine open a terminal
2. Activate the `conda environment <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html>`_ you want to install pylim to

.. code-block::

    conda activate environment_name

3. Install pylim from GitHub

.. code-block::

    python -m pip install git+https://github.com/radiation-lim/LIM-pylim.git


Contributing to pylim from within the group
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Get a GitHub Account and get added to the organization
2. Download `GitHub Desktop <https://desktop.github.com/>`_
3. On GitHub click the green Code button and click Open in GitHub Desktop
4. Select where you want to save the repository (e.g. ``.../PyCharmProjects/LIM-pylim``)
5. In GitHub Desktop go to File/Options and under Accounts sign in to GitHub

Under current branch create a new branch (e.g. jr-dev). The new branch will now be checked out and all changes happen on this branch.
You can publish the branch to GitHub now.

To immediately make use of changes you introduce to pylim you need to install install in editable mode (-e) in your conda environment. Make sure you have your development branch checked out!

1. Activate your environment:

.. code-block::

    conda activate environment_name


2. Install your pylim version in editable mode:

.. code-block::

    python -m pip install -e <path>

``<path>`` is the same path that you used to save the repository to (see step 4. above)

All changes in pylim are now available with a simple restart of your python console. No need to reinstall pylim each time you change something.

Data structure
--------------

HALO/flight campaign data is organized by flight in a flights folder, so that every flight has its own folder with subfolders for each instrument in it::

   ├── 01_Flights
   │   ├── all
   │   │   ├── BACARDI
   │   │   ├── BAHAMAS
   │   │   └── horidata
   │   ├── Flight_20210624a
   │   │   ├── BACARDI
   │   │   ├── BAHAMAS
   │   │   └── libRadtran
   │   ├── Flight_20210625a
   │   │   ├── BACARDI
   │   │   ├── BAHAMAS
   │   │   ├── horidata
   │   │   ├── libRadtran
   │   │   ├── quicklooks
   │   │   └── SMART
   ...

In order to be able to work across all flights an additional folder can be found called ``all``.
This folder contains one folder for each instrument which holds all data for the whole campaign.

This data is stored on the server but can also be stored locally.
To access it without needing to worry about changing the paths every time one switches from the server to local data, the function :py:func:`pylim.helpers.get_path` is used together with ``config.toml`` to generate the correct paths.
In the path configuration toml file the path to each instrument can be defined either as a absolute path or -to allow for easy path creation- relative to the base directory and the flight folder.
Providing :py:func:`pylim.helpers.get_path` with the instrument key (e.g. "smart"), the flight (e.g. "Flight_20210625a") and the campaign (e.g. "cirrus-hl") the correct path will then be created according to the current working directory.
Providing the key "all" requires the additional keyword instrument and will get the path to the instrument folder in the ``all`` folder.

.. attention::
    :py:func:`pylim.helpers.get_path` assumes the working directory of your python console on Linux to be in ``/mnt`` and on Windows in ``C:``. If your working directory starts with anything else the server configuration is assumed!
    Change the function accordingly if this is not true.

.. attention::
   The ``config.toml`` file has to be in the current working directory of the python console. So when you run a script in a different folder (like :file:`processing`) be sure to copy your most recent ``config.toml`` to that folder as well. Or you change into the directory with the ``config.toml`` using :py:func:`os.chdir`.

There are two ways of setting up paths to your local data source:

1. Edit the existing paths under ``jr_local`` or ``jr_ubuntu`` depending on whether you are using Windows or Linux.
2. Create a new campaign which defines the paths as you need them.

The second options is kind of hacky but would allow everyone to use the same path configuration file.
However, I don't see a merit in that so number 1 would be the preferred option.
Every user should have their own toml file.
