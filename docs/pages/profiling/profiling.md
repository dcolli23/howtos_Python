---
title: Profiling
nav_order: 6
---

# Profiling

I routinely have to search around for what profiling tool I enjoy using and I've found that I enjoy using `gprof2dot` along with the standard library's `cProfile`.

This page is derived from this [StackOverflow answer](https://stackoverflow.com/a/7693928/12526968).

```
pip install gprof2dot
python -m cProfile -o profile.pstats <script_name>.py
gprof2dot -f pstats profile.pstats | dot -Tsvg -o profile_results.svg
```

And you can easily visualize the output by doing:

```
eog profile_results.svg
```

Quick and easy profiling, the way it should be.