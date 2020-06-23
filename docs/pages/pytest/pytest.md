---
title: PyTest
nav_order: 3
has_children: True
---

# PyTest

This document goes over what PyTest is, how to write tests for PyTest, and how to run test suites written in PyTest.

If you're interested in reading the source documentation, see [this link](https://docs.pytest.org/en/latest/).

## What is PyTest?

PyTest is a testing framework written in Python. PyTest makes it easy to write small, independent tests for the software you develop while being able to scale to large application-wide tests.

### Well why is testing software important?

We won't dive too far into why testing your software is important since that can be a pretty deep rabbit hole. However, it is safe to say that testing your software in a quick and automated fashion leads to far more maintainable and robust software. It ensures that what you're writing is doing what you think it should do.

If you're interested in learning more about the power of writing tests for your software, [this link](https://en.wikipedia.org/wiki/Test-driven_development) will be of interest to you.

## How to write tests for PyTest

PyTest operates on Python `assert` statements. This keeps code lightweight since it's using built-in error handling in Python instead of relying on something specific to PyTest.

The following is an example of a test that we might write using the PyTest framework:

```python
# content of test_sample.py
def inc(x):
  return x + 1

def test_answer():
  assert (inc(3) == 5)
```

## How to run tests written for PyTest

To execute the test that we wrote in the above section, we would execute the following in the directory/folder where `test_sample.py` is located.

```
$ pytest
=========================== test session starts ============================
platform linux -- Python 3.x.y, pytest-5.x.y, py-1.x.y, pluggy-0.x.y
cachedir: $PYTHON_PREFIX/.pytest_cache
rootdir: $REGENDOC_TMPDIR
collected 1 item

test_sample.py F                                                     [100%]

================================= FAILURES =================================
_______________________________ test_answer ________________________________

    def test_answer():
>       assert inc(3) == 5
E       assert 4 == 5
E        +  where 4 = inc(3)

test_sample.py:6: AssertionError
========================= short test summary info ==========================
FAILED test_sample.py::test_answer - assert 4 == 5
============================ 1 failed in 0.12s =============================
```

For an adavanced example of using PyTest to test a repository, see the link at the bottom of this page.