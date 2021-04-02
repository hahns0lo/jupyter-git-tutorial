# jupyter-git-tutorial

A tutorial for using Git with Jupyter notebooks

## Setting up Jupyter

This tutorial uses JupyterLab using Google Cloud Platform's [AI Platform Notebooks](https://cloud.google.com/ai-platform-notebooks).  The following instructions describe how to create a notebook instance.  More detailed instructions can be found [here](https://cloud.google.com/ai-platform/notebooks/docs/create-new).

1. Open the [AI Platform Notebooks console](https://console.cloud.google.com/ai-platform/notebooks)
1. Click `+NEW INSTANCE` and select "Python 3"
   1. Instance name: git-tutorial-python
   1. Region: us-east1 (South Carolina)
   1. Zone: us-east1-b
   1. Instance properties: use all defaults
   1. Click `CREATE`
1. Click `OPEN JUPYTERLAB`

## Forking this repo

To allow you to push and pull commits to and from this repo, you must create your own copy of it, known as creating a fork.  The following instructions describe how to fork this repo.  More detailed instructions can be found [here](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo).

1. [Create a GitHub account](https://github.com/join), if you don't have one
1. Open https://github.com/hahns0lo/jupyter-git-tutorial in a browser
1. In the upper right-hand corner, click `Fork`
1. Select your user

## Scenario 1

1. Open JupyterLab
1. Clone your fork of this repo
   1. Using the Git extension
      1. On the left-hand side, click the [Git icon](https://git-scm.com/) to open the Git extension.
      1. Click `Clone a Repository`
      1. Copy and paste the URL to your fork, e.g. <https://github.com/[username]/jupyter-git-tutorial>
   1. Using the command line
      1. Open a terminal from the JupyterLab launcher
      1. `git clone https://github.com/[username]/jupyter-git-tutorial`
1. Make a copy of the tutorial notebook
   1. Using JupyterLab
      1. Open `jupyter-git-tutorial`
      1. Create a new folder called `tutorial`
      1. Copy and paste `intro_to_pandas.ipynb` into `tutorial
   1. Using the command line
      1. `cd jupyter-git-tutorial`
      1. `mkdir tutorial`
      1. `cp intro_to_pandas.ipynb tutorial`
1. Stage the notebook
   1. Using the Git extension
      1. Under Untracked, select `intro_to_pandas.ipynb` and click `+`
   1. Using the command line
      1. `git status`
      1. `git add intro_to_pandas.ipynb`
      1. `git status`
1. Commit the notebook
   1. Using the Git extension
      1. Summary: Adding copy of notebook
      1. Click `Commit`
      1. Enter your name and email
   1. Using the command line
      1. `git commit -m "Adding copy of notebook"`
      1. `git status`
1. Ignore Jupyter checkpoints
   1. Open `intro_to_pandas.ipynb`
   1. Create a new text file in the `jupyter-git-tutorial` folder called `.gitignore` and add the following:

      ```
      .ipynb_checkpoints
      ```

   1. Stage and commit `.gitignore`
      1. Using the Git extension
         1. Under Untracked, select `.gitignore` and click `+`
         1. Summary: Ignoring checkpoints
         1. Click `Commit`
      1. Using the command line
         1. `git status`
         1. `git add .gitignore`
         1. `git commit -m "Ignoring checkpoints"`
         1. `git status`
