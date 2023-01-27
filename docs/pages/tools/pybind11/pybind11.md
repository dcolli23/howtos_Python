---
title: Pybind11
nav_order: 2
parent: Tools
---

# Pybind11 And Accompanying Tools

[pybind11](https://github.com/pybind/pybind11) is a ridiculously helpful library that allows for interoperability between C++ and Python.
It "exposes C++ types in Python and vice versa."
I believe that most people think of `pybind11` as only exposing C++ types to Python and not the other way.
However, you can actually expose Python types in C++!

## Pybind11

Some uses for exposing C++ types in Python are:
- Optimizing performance critical portions of code to take advantage of C++'s speed.
- Wrapping an external C++ library for easy use in your Python package.
  - Wrapping types with `pybind` is actually pretty easy so this could be *very* helpful!

One use of doing the opposite, exposing Python types in C++ is:
- Rapid prototyping of new functionality in C++ applications.
  - C++ is great due to its speed but falls short in scripting/prototyping (development time) efficiency compared to Python. One can create a Python function wrapper in C++ and point to a quick and dirty script that is a breeze to change as long as the Python/C++ interface is relatively well defined and stable.

### Issues

There's one small problem with `pybind11` that I have and that's the fact that it doesn't play well with VS Code's intellisense engine (Pylance).
There's good security reasons for this as VS Code doesn't want to arbitrarily execute the shared library just to get some type information.
However, it's still a wee bit annoying to develop with.
Which is why [pybind11-stubgen](https://github.com/sizmailov/pybind11-stubgen) came about!

## Pybind11-stubgen

[Pybind11-stubgen](https://github.com/sizmailov/pybind11-stubgen) produces code stubs for the `pybind11`-produced wrapper.
These code stubs are `.pyi` files which are simply normal Python files that contain the same methods as your actual wrapped module, except that the `.pyi` files' methods are empty.

The reason why this is helpful is because Pylance can use these stubs - with Python type hints in them - as a way to inform the documentation/intellisense of what arguments should be what types.

### Stub Generation Example

This is the process I followed to generate stubs for the Python wrapper for CDCPD, a deformable object tracker I worked on while in the [ARM Lab](https://arm.eecs.umich.edu/):

1. Execute the following command.
    ```
    pybind11-stubgen -o /home/dylan/catkin_ws/devel/lib/python3/dist-packages/ --ignore-invalid=all pycdcpd
    ```
    - The `--ignore-invalid` flag was key to getting the stub generation to work as I had a complex custom type wrapped in a boost pointer that I didn't particularly want to write a wrapper for.
    - You'll also want to output the stubs (the `-o` flag) in the same directory where the `.so` shared library cpython file is located.
2. Once the stubs are generated, open VS Code's settings (JSON) and add the path to the `"python.autoComplete.extraPaths"` and `"python.analysis.extraPaths"` lists.