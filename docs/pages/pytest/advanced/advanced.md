---
title: Advanced PyTest Instructions
nav_order: 1
parent: PyTest
---

# Advanced PyTest Instructions

Using PyTest effectively is more than writing a simple test. One must set up the testing framework for a repository in a standardized way across all repositories in an organization.

## PyTest Directory Structure

We like to set up our test suites using the following format:

```
+- Repo_root\
    +- docs\
    +- C++_files\
    +- Matlab_files\
    +- Python_files\
        +- modules\
            +- test\
                +- unit\
                    +- test_unit_AAA.py
                    +- test_unit_BBB.py
                      .
                      .
                      .
                    +- test_unit_ZZZ.py
                +- integration\
                    +- test_integration_AAA.py
                    +- test_integration_BBB.py
                      .
                      .
                      .
                    +- test_integration_ZZZ.py
                +- data\
                    +- test_unit_AAA_data.json
                      .
                      .
                      .
                    +- test_integration_ZZZ.json
                +- output\
```

where all repository tests are included under the `Repo_root\Python_files\modules\test\` directory. Tests are split into [unit and integration](https://www.guru99.com/unit-test-vs-integration-test.html) tests, written under the `unit` and `integration` repositories, respectively.

Any data that any of the tests need, such as model files, options files, status files, etc are all stored in the `data` folder and tracked via Git.

The `output` folder is used as the location where all tests write their output. This means that any tests that run simulations or generate any sort of file as part of the test should write to the `output` folder. This folder is part of the repository's `.gitignore` file and thus is not tracked via git, so don't put anything here that you'll need to run tests on a different machine.