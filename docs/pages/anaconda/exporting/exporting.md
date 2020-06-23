---
title: Exporting an Environment
nav_order: 1
parent: Anaconda Environment Management
---

# Exporting an Environment

Congratulations! You’ve had a paper accepted and it’s time to publish the repository to the greater scientific community. Follow these steps to create an environment YAML file that will be added to the repository.
1.	Ensure that the repository on your local machine matches the repository in GitHub.
2.	With the proper environment activated (using `conda activate myenv` where `myenv` is the name of the environment), type the following in the Anaconda Prompt: `conda env export  > environment.yml`.
3.	Place the `environment.yml` file in the proper place in the repository. This means placing it in a location where it will be easily discoverable by the end-user. Don’t stick it in a folder that has a million files where it will likely get lost.
4.	Update the documentation for the repository to note where to find the `environment.yml` file and how to create an Anaconda environment from this file. You can just use a slightly modified version of the instructions found in the Using an Existing Environment section.
5.	Add the `environment.yml` file to the repository, commit, and push changes to GitHub.