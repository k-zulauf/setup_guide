# Local Python Scripting Setup Guide


## Introduction
This guide will cover the basics of setting up Python scripts and running them locally, written for KWL employees new to scripting. I've made this repository public on my personal GitHub account so that it can be easily accessed without a GitHub account, but you will need to create a GitHub account to access the [KWL repositories](https://github.com/orgs/KerrWoodLeidal/repositories) and collaborate on scripts.

It is assumed that you have never used Python / VS Code / git before. If you have run scripts before, you may already have some or all of the required components on your computer. 

---

## Getting Started

1. **Create a [GitHub account](https://github.com/signup?source=form-home-signup&user_email=)** if you don't already have one
   1. Contact Luis Galindo to be given access to the [KWL repositories](https://github.com/orgs/KerrWoodLeidal/repositories) you will be working with

2. **Ensure you have a compatible version of Python installed**
   1. Most scripts should work with Python 3.10 or later (the latest version I have installed is  [Python 3.13.3](https://www.python.org/downloads/release/python-3133/))
   2. However, if you intend to use `pyswmm` to run SWMM models, you should download [Python 3.11.9](https://www.python.org/downloads/release/python-3119/) to ensure compatibility with `pyswmm` (as of June 2025, the latest version of `pyswmm` is 2.0.1, which is not compatible with Python 3.12 or later)
   3. You can have multiple versions of Python installed on your computer, and specify which version to use when creating a virtual environment (see the [Terminal Actions](#terminal-actions) section below for more details)

3. **Download [VS Code](https://code.visualstudio.com/download)** (if not already installed)
   1. When installing VS Code, you can leave all the options set to the defaults
   2. The user installer should be fine for most users

4. **Download [git](https://git-scm.com/downloads)** (if not already installed)
   1. When installing git, you may want to make the following changes to the default options:
      1. Set the **default editor** to VS Code
      2. Override the **default branch name** for new repositories to "main" instead of "master" for consistency with KWL repositories

5. **Create a folder on your computer** where you will keep the local versions of the repositories you will be working with
   1. On my computer, I keep all my local repositories in a folder on my C drive (C:\Repos), but this is up to you

---

## Basic Actions Explained
### VS Code Actions
- **Open a folder:** *File>Open Folder*, or Ctrl+K Ctrl+O
- **Start a new terminal:** *Terminal>New Terminal*, or Ctrl+Shift+\`
- **Save:** *File>Save*, or Ctrl+S
  - A file has unsaved changes when there is a dot (instead of an x) on the file's tab in the file editor.
- **Create a file:** Go to the file explorer in VS Code (the top button on the left bar), hover over the main directory name at the top, and click the "new file" button. Enter a name and an extension (or just an extension, for files like ".env", ".gitignore", etc.)
  - Alternatively: *File>New File...*, or Ctrl+Alt+Win+N and follow the prompts
  <!-- - ![Explorer](images\file_explorer_button.png "Explorer") -->
- **Comment / Uncomment:** Ctrl+/
  - In .py files and .yml files, a comment is anything (in that line) after a pound sign: # (and in some instances, anything inside quotation marks or triple quotations)

### Terminal Actions
- **Navigate to a sub-folder in the current directory:** `cd folder_name`
  - You can start typing the sub-folder name and hit tab and it will autocomplete if there is only one option that starts with the charcters you have typed
- **Navigate back a folder:** `cd ..`
- **Create a virtual environment:** `py -m venv venv` or `python -m venv venv`
  - Whether you use `py` or `python` depends on how you installed Python and if you added Python to PATH or installed the py launcher
  - To create a virtual environment using a <u>specific version of Python</u> (if you have multiple versions installed), add the version as an agrument, e.g. `py -3.11 -m venv venv` would create a virtual environment with Python 3.11
- **Activate the virtual environment:** `source venv/Scripts/activate`
- **Install requirements:** `pip install -r requirements.txt` to install all requirements listed in the requirements.txt file
  - To install individual requirements not listed in the requirements.txt file: `pip install pandas` or `pip install pandas==2.3.1` to specify a version (this is an example using pandas, you would replace 'pandas' with the specific package you need)
- **Run a Python script:** `py script_name.py`
- **Check Python version:** `py --version` 
  - Check all versions of Python installed: `py -0` or `py -0p` (to list with location of each version)

---

## Useful Git Commands
These commands are run in the terminal just like the commands listed above, and you should be in the local repository folder to run them (you can use the `cd` command to navigate to the correct folder in the terminal). 

For complete steps to get started with git, see the guide written by Luis Galindo: [GitWithIt](https://github.com/KerrWoodLeidal/03GitWithIt/tree/master) (I've also downloaded the HTML to the network [here](\\kwlstoreasy2\users\BBY\KZulauf\Scripting_ref\gitWithIt.html)). The commands listed below are just a few of the most common git commands that you will likely use. Another more complete resource for common git commands that is linked in GitWithIt is [Basic Git Commands](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html). 

- Clone an existing KWL repository: `git clone https://github.com/KerrWoodLeidal/REPO_NAME.git`
  - Before running this command, make sure you are in the folder where you want the new repository folder to be created (e.g. if you want the new repository to be in C:\Repos, make sure you have navigated to C:\Repos in the terminal before running the clone command)
  - For repositories with a lot of history, it may be helpful to do a shallow clone (only copy the latest commit): `git clone REPO_URL --shallow`

- Checkout an existing branch: `git checkout BRANCH_NAME`
  - Create a new branch and switch to it: `git checkout -b NEW_BRANCH_NAME`

- Pull any changes made to the remote branch to your local branch: `git pull`

- Check the status of your local branch: `git status`

- See the commit history: `git log` 
  - You can add `--oneline` to see a more condensed version of the commit history, or `git log --all --graph --decorate` to see a visual representation of the commit history and branches (this can also be seen in VS Code's Source Control tab)

> [!NOTE]
> Before committing and pushing changes to the remote repository, make sure you have set up git with your name and email (if you haven't already) using the following commands: `git config --global user.name "YOUR_USERNAME"` and `git config --global user.email "YOUR_EMAIL"` as described in the [GitWithIt guide](\\kwlstoreasy2\users\BBY\KZulauf\Scripting_ref\gitWithIt.html).

- Add changes to be committed: `git add -A` to add all changes, or `git add FILE_NAME` to add specific files

- Commit changes: `git commit -m "COMMIT_MESSAGE"`

- Push changes to the remote repository: `git push` (if you are on a branch that tracks a remote branch, otherwise you may need to specify the remote and branch: `git push origin BRANCH_NAME`)

---

#### Author(s):
Kira Zulauf

#### Last Updated:
June 2026

> [!NOTE]
> This guide is adapted from the guide I wrote for the hydrometric monitoring project, which can be found in the [README file of the hydrometric monitoring repository](https://github.com/KerrWoodLeidal/hydrometric_monitoring). 
> 
> The Conventional Commits formatting guidelines in the next section have also been taken from the hydrometric monitoring repository, and are left as an example of the preferred general format for commit messages when collaborating on scripts in KWL repositories.
> 
> For other repositories, the Approved Scopes and Examples should be modified to fit the specific repository and project.

---

## Conventional Commits: Formatting

This section follows the [Conventional Commits](https://www.conventionalcommits.org/) formatting guidelines and has been adapted from other KWL repositories.

### ✅ Allowed Commit Types

Use one of the following types as a prefix in your commit messages:

- `feat` — for new features or functionality
- `fix` — for bug fixes or patches
- `docs` — for changes to documentation only
- `chore` — for routine tasks like setup, config, or tooling

### 🔍 Approved Scopes

Scopes help specify the area of the codebase being affected. Use one of the following scopes:

- `flowworks` — tasks involving FlowWorks integration, data sync, or parsing
- `hydrologic` — commits related to the calculation of the prescribed hydrologic indicators
- `automation` — changes related to script scheduling, automation, or logic

### ✏️ Commit Message Format

```bash
<type>(<scope>): <short description>
```

#### Examples:
```bash
feat(automation): add support for monthy automatic runs
fix(flowworks): handle missing rainfall data gracefully
docs(hydrologic): explain baseflow calculation method
chore(automation): add run logging text file
```


<!-- 4. Use git to clone the repository
   1. In VS Code, open the local folder you'd like the repo to go in, start a new terminal, and run `git clone https://github.com/KerrWoodLeidal/hydrometric_monitoring.git`
1. Set up the virtual environment
   1. Navigate to the new folder that was created when you cloned the repo
      1. Either open the folder in VS Code and then start a new terminal, or navigate in the terminal to the new folder
   2. Create the virtual environment
   3. Activate the virtual environment
   4. Install the project requirements from the requirements.txt file
2. Create a .env file and add your FlowWorks username and password, following the format of the lines below:<br>
   USERNAME=*your_FlowWorks_username*<br>
   PASSWORD=*your_FlowWorks_password*
3. Open the "inputs.yml" file and change the inputs as needed, following the existing format (see [How to enter inputs: inputs.yml](#how-to-enter-inputs-inputsyml) below and refer to the "inputs.yml" file for example inputs)
   1. Save the file
4. Run the main script by entering the following command in the terminal: `py main.py` -->