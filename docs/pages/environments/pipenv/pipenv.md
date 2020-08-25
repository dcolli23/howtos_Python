---
title: Pipenv and Pew
nav_order: 1
parent: Environment Management
---

# Pipenv And Pew
{:.no_toc}

* TOC
{:toc}

## Overview

This goes over the basics of how I use `pipenv` and `pew` to manage Python environments for my projects/applications. I've collated most of this information from:
  + [The official `pipenv` documentation](https://pipenv-fork.readthedocs.io/en/latest/) 
  + [https://realpython.com/pipenv-guide/](https://realpython.com/pipenv-guide/).

`pipenv` is used for the bulk of environment creation/management here and `pew` is used primarily for activating Python environments from anywhere in the system. `pipenv` also has the added bonus of Visual Studio Code integration as well! Visual Studio Code automatically detects environments created with `pipenv` and allows you to use them from within Visual Studio Code's integrated terminal.

## Installing `pipenv` and `pew`

To install `pipenv` and `pew`, it's as simple as going through your current `pip` installation. 

1. Execute the following in a terminal:
    ```
    pip install pipenv
    pip install pew
    ```
2. Follow the instructions [here](https://github.com/berdario/pew#display-the-environment-name-in-the-terminal-prompt) to get `pew` to display the virtual environment name in the terminal prompt. 
    + Tip: If you don't know which shell type you're using, it's probably bash if using a Linux machine and it's powershell if you're using a Windows machine.

## Getting Started With Environments

This section covers what you need to know to get up and running with `pipenv` environments.

### Creating A New Environment

In a directory that does not have a Pipfile in it, execute the following to create an environment for the project in the directory:

```
pipenv shell
```

This launches a new shell session that:
  1. Creates a Pipfile
  2. Creates the associated environment and environment directory in your `~/.local/share/virtualenvs/` directory.
      + Note: The environment is name `<the current directory name>-<hash>` where `<hash>` is a unique hash to the current directory. This is to avoid name conflicts if you have multiple environments with the same name directory. This would occur if you had multiple clones of the same repository, for example.

### Creating An Environment From An Existing Pipfile

`pipenv` is really great for creating environments from Pipfiles. To do this:

1. Navigate to the directory containing the Pipfile for the environment you're wanting to use/create.
2. Execute:
    ```
    pipenv install
    ```

## Using Environments

This section covers how to actually use environments.

### General Workflow

The general workflow for using an environment is to:

1. Create the environment, either from [scratch](#creating-a-new-environment) or [based off an existing environment](#creating-an-environment-from-an-existing-pipfile).
2. Activate the environment by following [these instructions](#activating-an-environment).
3. Do whatever you would like to do with Python.
4. Deactivate the environment by [exiting the shell session](#exiting-an-environment-session).

### Activating An Environment

You can activate environments in two seperate ways:

+ By using `pipenv` in the project directory that contains the Pipfile.
+ By using `pew` anywhere in your system.

#### Activating An Environment Using `pipenv`

To activate an environment using `pipenv`:

1. Navigate to the directory of your project/application containing the Pipfile.
2. Kick up a new shell session of your environment by typing:
    ```
    pipenv shell
    ```

#### Activating An Environment Using `pew`

To activate an environment from anywhere in your system, use `pew` in the following way:

1. List all of your virtual environments with:
    ```
    pew workon
    ```
    or
    ```
    pew ls
    ```
2. Activate the environment that you wish to work on with:
    ```
    pew workon <environment name> -n
    ```
    Be sure to include the full name (with the unique hash at the end of the human-readable name) to activate the environment in this way. The `-n` flag is so `pew` doesn't change your current directory to the directory the project associated with the environment is in.

### Exiting An Environment Session

Since `pipenv` and `pew` start a new shell session with the `virtualenv` pathing instead of changing the pathing in the current shell, you have to actually exit the shell by using the `exit` command or by typing <kbd>Ctrl-d</kbd> to deactivate the environment.

### Executing Python Files

There are several ways that you can execute Python files using `pipenv` environments.

#### From Within The Environment

You can execute whatever Python file that you're wanting to execute from *within* your environment doing the following:

1. Kick up a shell session with your active environment by following [these instructions](#activating-an-environment).
2. Execute your python file normally (using `python <my file name>.py`).

#### From Outside The Environment

You can execute a Python file *outside* of your environment by doing the following:

1. Navigate to the directory containing the Pipfile of the environment you're wanting to use.
2. Execute the instruction set for what you're wanting to do with `pipenv run` prepended to the command. 
    + For example, if you're wanting to print "Hello, World!" out using your custom environment, you'd navigate to the directory containing the Pipfile for that custom environment and do the following:
        ```
        pipenv run python -c "print('Hello, World!)"
        ```
    + Note: you can do some pretty cool stuff with [custom script shortcuts](https://pipenv-fork.readthedocs.io/en/latest/advanced.html#custom-script-shortcuts) using `pipenv`.

### Developing With Environments

When developing a project or application that uses `pipenv`, you'll want to be sure to `git add` and `git commit` your Pipfile anytime that you add or update packages using `pipenv install <package name>`.

#### Installing New Packages

When developing Python applications, it is inevitable that you'll need to install a package to help you along the way, like Jupyter Notebooks, NumPy, SciPy, OpenCV, or even the Python Trello API interface. When this becomes necessary:

1. Search for the package using the [Python Package Index](https://pypi.org). 
2. Navigate to the directory containing the Pipfile of the environment you are wishing to install the package to.
3. Execute the following to install the package:
    ```
    pipenv install <package name>
    ```
    `pipenv` automatically installs the package and resolves any dependency issues for you (through the `pip` backend) and also updates your Pipfile and Pipfile.lock files for you! Be sure to `git add` and `git commit` the changes to the Pipfile and Pipfile.lock files once you're sure that you've downloaded the correct package.

## Miscellaneous Tips and Tricks

### Scripting With `pipenv`

[https://pipenv-fork.readthedocs.io/en/latest/advanced.html#custom-script-shortcuts](https://pipenv-fork.readthedocs.io/en/latest/advanced.html#custom-script-shortcuts)

I'd use this to, for example, avoid having to type:

```
pipenv run python myTrello.py daily
```

and could instead run:

```
pipenv run daily
```

by modifying my Pipfile.


### Using `pew` with `pipenv`

Pipenv is a great way to set up environments and export them as determinate environments, locking the environment in a state that is known to work. However, I kind of hate that you can only activate the environment from the directory that contains the `Pipfile`. To prevent this, you can install `pew` using your `pip` installation.

I love that in Anaconda you can activate a Python environment from anywhere and use that environment for anything that you need. I wanted the same functionality out of `pipenv`.
  + Revisiting this, I'm not quite sure if this is best practice sort of behavior. Either way, I'm keeping this up here for my own reference.

#### Listing Environments

```
pew workon
```

This lists all of the environments available to you.

#### Activating an Environment

```
pew workon <environment name>
```

This activates the environment from anywhere in your system. You can then run your `pipenv run` commands (you can learn how to create these in the "scripting" section) from anywhere in the system.