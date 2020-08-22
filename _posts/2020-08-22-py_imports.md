---
layout: post
title: Python Imports
---

I currently use spacemacs as a development environment.  I open a .py file, then `run-python` to startup an interactive shell.  In spacemacs, the shell's pwd is assocaited to the where `run-python` was executed. So, if it was executed in the .py file, the pwd would be the files subdirectory, rather than the projects root.

With data science development, csv's live in a data folder accessible from the top level of the directory.  `project_directory/data`. If the Python file I am using is in `project/src`, if I wanted to read in a csv from the data folder I would use the relative path `pd.read_csv('../data/target_csv')`. This will only work if the interpreter's pwd is the src directory.

To fix this problem, I included the following code at the top of my .py file:

```python   
import os  
  
cur_dir = os.getcwd()  
root = cur_dir.split('project_directory')[0]  

```

This retrieves the absolute file path to the project root, and assigns it to the root variable.  Then, when loading csv, I concatenate root with the path from the top level of the directory, like so:

```python
df = pd.read_csv(root+'project_directory/data/target.csv')
```
