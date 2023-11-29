# LIM-pylim


A python package bundling processing functions and tools for the atmospheric radiation working group at the Leipzig Institute for Meteorology, Germany.

Documentation: https://radiation-lim.github.io/LIM-pylim/

# Installation instructions:

## Installing and using pylim from GitHub
If you only want to use the functions available and install pylim like a normal python package this is all you need to do:

1. On your machine open a terminal
2. Activate the [conda environment](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) you want to install pylim to
	`conda activate environment_name`
3. Install pylim from GitHub
	`python -m pip install git+https://github.com/radiation-lim/LIM-pylim.git`

## Contributing to pylim from within the group

1. Get a GitHub Account and get added to the organization 
2. Download [GitHub Desktop](https://desktop.github.com/)
3. On GitHub click the green Code button and click Open in GitHub Desktop
4. Select where you want to save the repository (e.g. .../PyCharmProjects/LIM-pylim)
5. In GitHub Desktop go to File/Options and under Accounts sign in to GitHub

Under current branch create a new branch (e.g. jr-dev). The new branch will now be checked out and all changes happen on this branch.
You can publish the branch to GitHub now.

To immediately make use of changes you introduce to pylim you need to install in editable mode (-e) in your conda environment. Make sure you have your development branch checked out!

1. Activate your environment: `conda activate environment_name`
2. Install your pylim version in editable mode: `python -m pip install -e <path>`
	`<path>` is the same path that you used to save the repository to (see step 4. above)

All changes in pylim are now available with a simple restart of your python console. No need to reinstall pylim each time you change something.


Documentation can be found at

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
