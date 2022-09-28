# Framework

## Introduction

The T&E Framework Infrastructure connects the various components and toolboxes being developed for the Trusted AI project together into a single coherent system.
The system provides standardized methods for storage and version control of code, data and documentation.
There is a minimum viable vocabulary to describe experiments, as well as metadata and storage criterion for model/data outputs such as Neural Network weights.
Preference is given to Open Source Software and Tools that can either be integrated into the Framework or modified by our software development teams with possible contribution back to their parent project.

This document provides information on how to set up and use the framework.

## Overview

Trust is ... and comes from details that are in each step in the machine learning cycle.
The cycle is the loop of steps *Development*, *Use*, *Analysis*, and *Re-Design* that is the basis of improving models over time.

<!-- AI models are rarely created and then used with no further adjustments.
Usually the performance of the model is evaluated and then fed back into an improvement of the model,
whether that is through more comprehensive training data, adjustments of the encoding/decoding layers, or
even changes to the model architecture.
-->

This diagram shows the feedback loop along with the six dimensions of trust in the center, as they apply
to all the steps.

![Circular diagram visualizing the relationship of the components](/static/graphic_concept-5.png)

Six dimensions of Trust are...


The word "framework" is applied to two different concepts here.
First, it is used to describe the conceptual understanding of what is needed to provide trusted AI.
Second it is used to refer to the specific software tools used to implement parts of the conceptual framework.

these are tools that we chose based on criteria:

The core of the framework is the version control system [Git] and the storage overlay provided by the [Data Version Control][dvc] (DVC) project.
All model code, data preperation code, and training workflows are tracked in as a Git Repository.
Training data, generated models, and analytics are tracked by DVC.
DVC provides a way to track file versions in Git, but store the contents elseware.
This is useful since training data and models tend to be large and numerious, both things that become a liability when stored directly in a Git repository.

  [git]: https://git-scm.com/
  [dvc]: https://dvc.org/

The workflow steps are

1. Initially, either find an existing project or [create a new project repository](#set-up-repository). Then set up DVC with the correct remote storage locations.
(The location may be, among other things, a local drive, a mounted AFS share, or cloud storage)
2. Add or update data files, and download existing data files.
3. Adjust your model code to use DVC parameters
4. Set up processing workflows
5. Update code, run experiments
6. Check in changes to both code and data



## Trusted Storage






## Installation and Set Up

The framework requires [Python] to operate.
If you don't have a recent version of python installed, see the section [Installing Python](#installing-python).
(To find the version of python you have installed run `python3 -V`. The output should be at least 3.10)

Next, make sure [Git] is installed and [set up your git project](#set-up-repository).




### Installing Python

Python is installed differently depending on the operating system on your computer.

 * **MacOS** Easist way is with [Homebrew].
    ```
    $ brew install pyenv
    $ pyenv install 3.10.6
    ```
 * **Linux**...how?
 * **Windows**...no idea


### Set Up Repository

All AI projects are expected to be in a Git repository.
If there isn't already one set up, make a new one by creating a new directory, installing PDM, and then using `git init` to initialize a new git repository. The detailed steps follows.
There are also many guides online if you want more information, especially on [using Git][github-git].

1. Create a new directory for the project  `mkdir my-ai-project`
2. Enter the directory `cd my-ai-project`
3. Set up [PDM] `pip install --user pdm`
4. Initialize PDM
    ```$ pdm init
    Creating a pyproject.toml for PDM...
    Please enter the Python interpreter to use
    0. /opt/homebrew/opt/python@3.10/bin/python3.10 (3.10)
    1. /opt/homebrew/opt/python@3.10/bin/python3.10 (3.10)
    2. /opt/homebrew/opt/python@3.9/bin/python3.9 (3.9)
    3. /Users/dbrower/.pyenv/versions/3.9.10/bin/python3.9 (3.9)
    4. /Library/Developer/CommandLineTools/usr/bin/python3 (3.9)
    Please select (0): 0
    Using Python interpreter: /opt/homebrew/opt/python@3.10/bin/python3.10 (3.10)
    Would you like to create a virtualenv with /opt/homebrew/opt/python@3.10/bin/python3.10? [y/n] (y): y
    Virtualenv is created successfully at ./my-ai-ptoject/.venv
    Is the project a library that will be uploaded to PyPI [y/n] (n): n
    License(SPDX name) (MIT):
    Author name (Jane Doe):
    Author email (jdoe@example.com):
    Python requires('*' to allow any) (>=3.10):
    Changes are written to pyproject.toml.
    ```
5. Set up the Git repo
    ```$ git init
    Initialized empty Git repository in /my-ai-ptoject/.git/
    ```
6. Make the first commit
    ```
    $ git add pyproject.toml
    $ git commit -m "Initial Commit"
    [main (root-commit) 7fc208a] Initial Commit
     1 file changed, 14 insertions(+)
     create mode 100644 pyproject.toml
    ```

### Install DVC

Since the [PDM] pacakge manager is installed, we can use that to install DVC:

```
$ pdm add dvc
Adding packages to default dependencies: dvc
🔒 Lock successful
Changes are written to pdm.lock.
Changes are written to pyproject.toml.
Synchronizing working set with lock file: 85 to add, 0 to update, 0 to remove

🎉 All complete!
```



Configure DVC with remotes.


  [python]: https://www.python.org/
  [pyenv]: https://github.com/pyenv/pyenv
  [pdm]: https://pdm.fming.dev/latest/
  [homebrew]: https://brew.sh/
  [github-git]: https://github.com/git-guides


## Common Tasks

### Download a dataset

### Add or Update a dataset

### Create a Workflow




## Projects
* [Maintenance Operators Ontology](https://nd-crane.github.io/moo)
* [Paper Analytical Devices](https://nd-crane.github.io/paper-analytical-devices)



## Tutorial


This tutorial will gide you with setting up the framework and running a simple model.
Begin by [installing Git](#) and [installing Python](#), if needed.
Using the command line, type the following to create a new directory for the new project:

    mkdir ai-tutorial

Enter the new directory and initialize PDM. (Don't type the `$` character—it is used to indicate what you should type into the command prompt)

    $ cd ai-tutorial
    $ pdm init
    Creating a pyproject.toml for PDM...
    Please enter the Python interpreter to use
    0. /opt/homebrew/opt/python@3.10/bin/python3.10 (3.10)
    1. /opt/homebrew/opt/python@3.10/bin/python3.10 (3.10)
    2. /opt/homebrew/opt/python@3.9/bin/python3.9 (3.9)
    3. /Users/dbrower/.pyenv/versions/3.9.10/bin/python3.9 (3.9)
    4. /Library/Developer/CommandLineTools/usr/bin/python3 (3.9)
    Please select (0): 0
    Using Python interpreter: /opt/homebrew/opt/python@3.10/bin/python3.10 (3.10)
    Would you like to create a virtualenv with /opt/homebrew/opt/python@3.10/bin/python3.10? [y/n] (y): y
    Virtualenv is created successfully at ./ai-tutorial/.venv
    Is the project a library that will be uploaded to PyPI [y/n] (n): n
    License(SPDX name) (MIT):
    Author name (Jane Doe):
    Author email (jdoe@example.com):
    Python requires('*' to allow any) (>=3.10):
    Changes are written to pyproject.toml.

PDM has a few prompts.
You can see the answers in the text above.
For the python version, use the one that you had previously installed—usually the first option. So we chose `0`.
Then type `y` to set up a virtualenv.
Then type `n` since this is not going to be a PyPI library.
For the next four options, press Enter to choose the defaults.

Now lets create a machine learning model.
Open a text editor and save the following as the file `model.py`

```python
#!/bin/env python

# enter simple pytorch model
```

Lets create a new git repository for this model.

    $ git init
    Initialized empty Git repository in /ai-tutorial/.git/
    $ git add pyproject.toml model.py
    $ git commit -m "Initial Commit"
    [main (root-commit) 7fc208a] Initial Commit
     1 file changed, 14 insertions(+)
     create mode 100644 pyproject.toml
     create mode 100644 model.py
    ```

Now lets grab some training data.
(Which training data?)

Lets set up DVC and add this data to it.
(Set up a local remote.)

    pdm dvc ...


