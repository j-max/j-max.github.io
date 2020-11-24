---
layout: post
title: Tensorflow Dead Kernel
---

I recently had a frustrating experience trying to debug a Tensorflow error in a Jupyter Notebook.  After building the model architecture and compiling it, running fit_generator crashed the kernel with no output.  After going down many dead end solutions, the solution turned out to be updating Numpy: `pip install -U numpy`.  Thanks to this [thread](https://github.com/tensorflow/tensorflow/issues/9829) for the solution.
