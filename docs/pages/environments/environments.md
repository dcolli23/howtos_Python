---
title: Environment Management
nav_order: 2
has_children: true
---

# Environment Management
{:.no_toc}

* TOC
{:toc}

## Why Use Python Environments?

That's a great question! An important part of science, especially computational science, is reproducibility. Being able to do an experiment on your own is great but it's important to be able to regenerate figures, expand upon existing experiments in the future, and make the tools available to the broader research community. A major barrier to reproducibility in the world of computational science is package dependencies. Packages used within computer code can change over time and old code can break or the behavior can be modified in negative ways thanks to those changes. When sharing code, we want to be able to setup a computer ecosystem that is exactly the same as when we were developing the code. We want a *deterministic* snapshot of our development dependencies. To do this, we use 'virtual environments.'

Note: Environments are meant to serve as a way to ensure that Python package installations on separate systems are the same. Environments are not like GitHub repositories in the sense that they take a “snapshot” of the folder you are working in. If you accidentally delete a file that is not version controlled through software like Git, you can’t recover it with environments!

## What Tools Are Available For This?

There are lots of tools available for using virtual environments. Personally, I've used Anaconda a lot but have experienced some issues with the scalability of it. It becomes a bit of a rat's nest when multiple versions of Python or vastly different environments are involved.

I'm now moving onto using `pipenv`. Regardless, I've written up my experience with and some tutorials on how I use both Anaconda and `pipenv`.