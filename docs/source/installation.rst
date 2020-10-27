Installation
===================================

Installing the latest release
*****************************

Installing PyCaret is the first step towards building your first machine learning model in PyCaret. Installation is easy and takes only a few minutes. All hard dependencies are also installed with PyCaret. `Click here <https://github.com/pycaret/pycaret/blob/master/requirements.txt>`_ to see the complete list of hard dependencies. 

In order to avoid potential conflicts with other packages, it is strongly recommended to use a virtual environment, e.g. python3 virtualenv (see `python3 virtualenv documentation <https://docs.python.org/3/tutorial/venv.html>`_) or `conda environments <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html>`_. Using an isolated environment makes it possible to install a specific version of pycaret and its dependencies independently of any previously installed Python packages. See an example below of how to create a conda environment and install PyCaret. 

.. code-block:: python

    # create a conda environment
    conda create --name yourenvname python=3.6

    # activate conda environment
    conda activate yourenvname

    # install pycaret
    pip install pycaret

    # create notebook kernel connected with the conda environment
    python -m ipykernel install --user --name yourenvname --display-name "display-name"


Installing the full version 
***************************
PyCaret's default installation is a slim version of pycaret which only installs hard dependencies as `listed here <https://github.com/pycaret/pycaret/blob/master/requirements.txt>`_. To install the full version of pycaret, use the following command:

.. code-block:: python

    # install the full version of pycaret
    pip install pycaret[full]

Installing the nightly build
****************************

PyCaret is a fast-evolving machine learning library. Often, you want to have access to the latest features but want to avoid compiling PyCaret from source or waiting for the next release. Fortunately, you can now install pycaret-nightly using pip.

.. code-block:: python

    # install the nightly build
    pip install pycaret-nightly

Recommended environment for use
*******************************

You can use PyCaret in your choice of Integrated Development Environment (IDE) but since it uses html and several other interactive widgets, it is optimized for use within a notebook environment, be it `Jupyter Notebook <https://jupyter.org/>`_, `Jupyter Lab <https://jupyterlab.readthedocs.io/en/stable/>`_, `Azure Notebooks <https://notebooks.azure.com/>`_ or `Google Colab <https://colab.research.google.com/>`_.

- `Learn how to install Jupyter Notebook <https://jupyter.readthedocs.io/en/latest/install.html>`_
- `Learn how to install Jupyter Lab <https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html>`_
- `Get Started with Azure Notebooks <https://notebooks.azure.com/>`_
- `Get Started with Google Colab <https://colab.research.google.com/>`_
- `Get Started with Anaconda Distribution <https://www.anaconda.com/>`_

Run PyCaret on a Docker Container
*********************************
A Docker container runs in a virtual environment and is the easiest way to deploy applications using PyCaret. Dockerfile from base image python:3.7 and python:3.7-slim is tested for PyCaret >= 2.0.

- `python:3.7 <https://github.com/pycaret/pycaret/blob/master/docker%20python37/Dockerfile>`_
- `python:3.7-slim <https://github.com/pycaret/pycaret/blob/master/Dockerfile>`_

.. code-block:: python

    FROM python:3.7-slim

    WORKDIR /app
    
    ADD . /app

    RUN apt-get update && apt-get install -y libgomp1

    RUN pip install --trusted-host pypi.python.org -r requirements.txt

    CMD pytest #replace it with your entry point.
