# jupyter-git-tutorial

The goal of this tutorial is to show how to use Git with Jupyter notebooks.  The primary audience for this tutorial are data scientists and data analysts who have some experience with Jupyter notebooks but little to no experience with Git or the command line.  To that end, this tutorial uses JupyterLab and the [JupyterLab Git extension](https://github.com/jupyterlab/jupyterlab-git) but also provides the equivalent `git` commands, for the curious.

This tutorial is inspired by the [Katacoda Git tutorial](https://katacoda.com/courses/git/) in that it follows the same basic flow of introducing Git commands but applied to Jupyter notebooks.  The actual notebook used here is from this [Google Colab notebook](https://colab.research.google.com/notebooks/mlcc/intro_to_pandas.ipynb) for teaching the pandas Python library.

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
1. Open <https://github.com/hahns0lo/jupyter-git-tutorial. in a browser
1. In the upper right-hand corner, click `Fork`
1. Select your user

## Setup SSH key

To allow you to push and pull commits without being prompted for a password, you must setup your GitHub account with an SSH key.  The following instructions describe how to do this in your JupyterLab instance.  More detailed instructions can be found

1. Open JupyterLab
1. Open a terminal from the JupyterLab launcher
1. Create an SSH key by following the Linux instructions [here](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
1. Add the SSH key to your GitHub account the Linux instructions [here](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account).
   1. For step 1, use the following command instead: `cat ~/.ssh/id_ed25519.pub`

## Setup ReviewNB

[ReviewNB](https://www.reviewnb.com/) is a GitHub Marketplace app that provides visual diffs for Jupyter notebooks on GitHub.  The following instructions describe how to setup ReviewNB with your fork.

1. Open <https://github.com/marketplace/review-notebook-app>
1. Under Pricing and setup, select Free and click `Install it for free`
1. Click `Complete order and begin installation`
1. Select `Only select repositories`, select `[username]/jupyter-git-tutorial`, and click `Install`
1. Click `Authorize Review Notebook App` and you will be redirected to <https://app.reviewnb.com/>

## Scenario 1

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
      1. Copy and paste `intro_to_pandas.ipynb` into `tutorial`
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

## Scenario 2

1. Open `intro_to_pandas.ipynb` in the `jupyter-git-tutorial/tutorial` folder, run it, and save
1. Check Git status
   1. Using the Git extension
      1. `intro_to_pandas.ipynb` should be listed under Changed
   1. Using the command line
      1. `cd ~/jupyter-git-tutorial`
      1. `git status`
      1. `tutorial/intro_to_pandas.ipynb` should be listed as `modified` under `Changes not staged for commit`
1. Look at the changes
   1. Using the Git extension
      1. Under Changed, select `intro_to_pandas.ipynb` and click the icon with a `+` and `-`
      1. Only outputs should have changed
   1. Using the command line
      1. `git diff`
      1. Keep pressing space to scroll down or `q` to quit
      1. `git difftool`
      1. Use the up/down keys to scroll or the following sequence twice to quit
         1. `:q`
         1. Enter
1. Stage the changes and view the changes again
   1. Using the Git extension
      1. Under Changed, select `intro_to_pandas.ipynb` and click `+`
      1. Under Staged, select `intro_to_pandas.ipynb` and click the icon with a `+` and `-`
   1. Using the command line
      1. `git status`
      1. `git add tutorial/intro_to_pandas.ipynb`
      1. `git status`
      1. `git diff` Nothing should happen!
      1. `git diff --staged`
      1. `git difftool --staged`
1. Commit the changes
   1. Using the Git extension
      1. Summary: Ran notebook
      1. Click `Commit`
      1. Enter your name and email
   1. Using the command line
      1. `git commit -m "Ran notebook"`
      1. `git status`
1. Look at the log
   1. Using the Git extension
      1. Click the History tab
   1. Using the command line
      1. `git log`
      1. `git log --pretty=format:"%h %an %ar - %s"`
1. Look at the last commit
   1. Using the Git extension
      1. Click the History tab
      1. Click on the "Ran notebook" commit to expand
      1. Click on `intro_to_pandas.ipynb`
   1. Using the command line
      1. Copy the long string of numbers and text after `commit`. This is called the commit hash or commit SHA.
      1. `git show [commit hash]`

## Scenario 3

1. Open `intro_to_pandas.ipynb` in the `jupyter-git-tutorial/tutorial` folder
1. Modify the notebook
   1. Find and replace the following
      1. `Sacramento` to `Los Angeles`
      1. `485199` to `3792621`
      1. `97.92` to `468.97`
   1. Run the notebook and save
1. Look at the changes
   1. Using the Git extension
      1. Look at the output after the `pd.Series(['San Francisco', 'San Jose', 'Los Angeles'])` cell
      1. Hover over the red/green boxes under "Outputs changed" and click `Show source`
   1. Using the command line
      1. `git diff`
      1. `git difftool`
   1. Note that may appear that all outputs have changed, even if you don't see any differences.  This is because if the cell numbers differ, that counts as a change.
   1. Try Run->Restart Kernel and Run All Cells... to reset cell numbering and look at the diff again
1. Stage and commit the changes
   1. Summary: "Replaced Sacramento with Los Angeles"
1. Look at information about the remote repository
   1. The Git extension does not have this feature
   1. Using the command line
      1. `cd ~/jupyter-git-tutorial`
      1. `git remote`
      1. `git remote show origin`
1. Open <https://github.com/[username]/jupyter-git-tutorial> in a browser
   1. Click on the `N commits` link next to the icon of a watch.  It should not contain any of your commits.
1. Push your commits
   1. Using the Git extension
      1. Click the cloud icon with an up arrow
      1. Enter GitHub username and password
   1. Using the command line
      1. `git push`
1. Look at the log
1. Open <https://github.com/[username]/jupyter-git-tutorial> in a browser
   1. Click on the `N commits` link again.  The value of `N` should be larger and it should match the log history.

### Bonus: ReviewNB