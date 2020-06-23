---
title: Documentation Best Practices
nav_order: 4
has_children: true
---

# Documentation Best Practices
{:.no_toc}

* TOC
{:toc}

## Overview

These pages discuss some of the best practices and style guides we at the Campbell Muscle Lab use.

We largely follow the [NumPy docstring standards](https://numpydoc.readthedocs.io/en/latest/format.html).

## Summary of Official Format

The most important standards to follow for the NumPy documentation format are as follows.

### Docstrings

1. Directly below function and class definitions, begin the documentation with a triple quote, `"""`. This is called a "docstring" and is shown below:
    ```python
    def dummy_function():
    """This is a contrived function for example purposes"""
    return
    ```
    Note that this is the **bare minimum** of what a docstring should be. Unless the function is *extremely* simple and self-explanatory, the docstring should be more robust than a one line explanation.
    + The first portion of the docstring should be a single line summary of what the function or class does.
        + If more explanation is required, there should still be a one line summary followed by a multi-line summary below the one line summary, separated by a blank line. Ex:
            ```python
            def another_dummy_function():
                """Another contrived function

                This is another contrived function for the use of documentation.
                This is a very long-winded explanation.
                """
                return
            ```
2. docstrings for functions should follow this format:
    ```python
    def fully_documented_function(first_param, second_param, third_param="optional"):
        """[one line summary]

        [multiple line summary]

        Parameters
        ----------
        first_param : [type of first_param]
            [description]
        second_param : [type of second_param]
            [description]
        third_param : [type of third_param], optional
            [description], by default [PUT DEFAULT VALUE HERE]
        
        Returns
        -------
        [NAME OF RETURNED VARIABLE] : [type of returned value]
            [description]

        Raises
        ------
        [EXCEPTION THIS FUNCTION RAISES]
            [Why this function raises the exception]
    ```
    where the brackets indicate information you should fill out.

    We break down the sections below:
    + The *one line summary* is required for all functions.
    + The *multiple line summary* is not required if the function is sufficiently summarized in the one line summary.
    + The `Parameters` section is very important and should be included any time parameters are passed to the function.
        + Document *all* parameters in this section with the following format:
            ```python
            """
            Parameters
            ----------
            [parameter name] : [parameter type]
                [parameter description]
            """
            ```
        + If a parameter is optional, it should be added with this format:
            ```python
            """
            Parameters
            ----------
            [parameter name] : [parameter type], optional
                [description], by default [default value]
            """
            ```
            where you give the default value in `[default value]`.
    + The `Returns` section is for documenting what the function returns.
        + If the function doesn't return anything, don't add a `Returns` section.
    + The `Raises` section is for documenting any errors the function might raise if any problems are encountered during its executation.
        + If the function doesn't raise any errors, don't add the `Raises` section.
3. docstrings for classes should follow this format:
    ```python
    class ClassName(BaseClassName):
        """[one line summary]

        [multiple line summary if needed]
        """
        def __init__(self, first_param, second_param):
        """[one line summary]

        [multiple line summary if needed]

        Parameters
        ----------
        [first param name] : [type]
            [description]
        [second param name] : [type]
            [description]
        [repeat for all parameters in the init function]

        Raises
        ------
        [EXCEPTION THIS FUNCTION RAISES]
            [Why this function raises the exception]
        """
    ```
    where the brackets indicate information you should fill out.

    We break down the sections below:
    + The *one line summary* is required for all classes and their `__init__` functions.
    + The *multiple line summary* is not required if the class or `__init__` function is sufficiently summarized in the one line summary.
    + The `Parameters` section:
        + Is not required for the class description.
        + Is required for the `__init__` function.
            + Don't include the `self` parameter, though.
    + The `Raises` section:
        + Is not required for the class description.
        + Is required for the `__init__` function if there are `assert`s for handling errors.

See the [Visual Studio Code Docstring Extension](vscode_docstring_extension/vscode_docstring_extension.md) page for a tool that helps with creating docstrings in visual studio code.
