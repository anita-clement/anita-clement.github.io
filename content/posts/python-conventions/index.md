---
author: Anita Clement
title: "Python Conventions"
date: 2022-03-04T13:33:41Z
draft: false
tags: [
    "Python",
    "PEP8",
    "flake8",
    "black",
    "isort",
    "mypy",
    "nbqa black",
    "nbqa isort",
    "end-of-file-fixer"
]
---

## PEP 8 or How to Make your Code Readable

Why is code readability and consistency that important?

Because "Code is read much more often than it is written.” as Guido van Rossum (creator of the Python programming language) said. Usually you write a piece of code once and never touch it again. But you’ll probably get back to it several times since it’s now part of your project and each time you will have to remember how it works and what it does. That’s when readability really matters.

*PEP8* is a document designed to provide guidelines and best practices on how to write Python code.
It is now considered as the reference style guide for Python code and can be found [here](https://www.python.org/dev/peps/pep-0008/). \
A package has also been developed to allow you to check your Python code against some of the PEP8 conventions (project description [here](https://pypi.org/project/pep8/)). To install it using pip, run:
```
pip install pep8
```
. 

We've only decided to list below the guidelines linked to code layout as there are many guidelines and the official guide is very clear and easy to read.

### Code Lay-out

**Indentation** 

4 spaces per indentation level.

In case of line continuations (to keep lines to under *79* characters), there are two styles of indentation you can use: 

- align the indented block with the opening delimiter
- add 4 spaces (an extra level of indentation) to distinguish arguments from the rest

```python
# Aligned with opening delimiter
foo = long_function_name(var_one, var_two,
                         var_three, var_four)
```
```python
# Add 4 spaces (an extra level of indentation) to distinguish arguments from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)
```
```python
# Hanging indents (=every line but the first in a paragraph 
# or statement is indented) should add a level.
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)
```

The closing brace/bracket/parenthesis on multiline constructs may either:

- line up under the first non-whitespace character of the last line of list
- be lined up under the first character of the line that starts the multiline construct

```python
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )
```
```python
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

**Tabs or spaces?**

Spaces

**Maximum line length**

79 (72 for comments/docstrings)

**Should a line break before or after a binary operator?**

Before

```python
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

**Blank lines**

- top-level functions and class definitions: 2 lines above and below
- method definitions inside a class: 1 line above and below

**Imports**

- imports should always be on separate lines
- imports are always put at the top of the file, just after any module comments and docstrings, and before module globals and constants.

Imports should be grouped in the following order:

1. Standard library imports.
2. Related third party imports.
3. Local application/library specific imports.

You should put a blank line between each group of imports.

- absolute imports are recommended
```python
import mypkg.sibling
from mypkg import sibling
from mypkg.sibling import example
```
- wildcard imports (`from module import *`) should be avoided

## Python packages for formatting, typing and linting

### flake8

Flake8 is a Python library wrapping around the 3 following tools:
- PyFlakes
- pycodestyle
- Ned Batchelder’s McCabe script
.

It mainly checks your code against most of PEP8's conventions but also programming errors like unused imports or undefined names. It also checks the level of complexity in your code using Thomas J. McCabe's cyclomatic complexity metric.

To install flake8 using pip, run
```
pip install flake8
```
.

You can then launch the `flake8` command to check your whole project directory or you can pass a file or a directory:
```
flake8 my_dir/my_subdir/
```
.

#### Error and warning codes

- `E***`/`W***`: [pep8 errors and warnings](https://pycodestyle.pycqa.org/en/latest/intro.html#error-codes)
- `F***`: [PyFlakes codes](https://flake8.pycqa.org/en/2.6.0/warnings.html)
- `C9**`: McCabe complexity plugin [mccabe](https://github.com/PyCQA/mccabe)
- `N8**`: Naming Conventions plugin [pep8-naming](https://github.com/flintwork/pep8-naming)

#### Skip line or file

If you want Flake8 to skip a file, add the following comment at the top:
```python
# flake8: noqa
```
.

If you just want to skip a line, add a `# noqa` comment at the end of it. 
You can also ignore a spefic error by providing its error code like this: `# noqa: <error>`, e.g., `# noqa: E101`.

### black

Black is a PEP8 compliant code formatter. It reformats entire files in place. \
The current code style can be found [here](https://black.readthedocs.io/en/stable/the_black_code_style/current_style.html).

To install black using pip, run
```
pip install black
```
.

You can then launch the `black` command to reformat your whole project directory or you can pass a file or a directory:
```
black my_dir/my_subdir/
```
.

#### Skip block or line

Black won't reformat blocks that start with `# fmt: off` and end with `# fmt: on`. \
It also won't reformat lines that ends with `# fmt: skip`.

### isort

isort is a Python library that sorts your imports alphabetically, and automatically separate them into sections and by type. \
The full documentation can be found [here](https://pycqa.github.io/isort/).

To install isort using pip, run
```
pip install isort
```
.

You can then launch the `isort` command to reformat your whole project directory or you can pass several files:
```
isort myscript.py myscript2.py
```
.

Below is an example before/after isort is run.

Before: 
```python
from my_lib import Object

import os

from my_lib import Object3

from my_lib import Object2

import sys

from third_party import lib15, lib1, lib2, lib3, lib4, lib5, lib6, lib7, lib8, lib9, lib10, lib11, lib12, lib13, lib14

import sys

from __future__ import absolute_import

from third_party import lib3
```

After:
```python
from __future__ import absolute_import

import os
import sys

from third_party import (lib1, lib2, lib3, lib4, lib5, lib6, lib7, lib8,
                         lib9, lib10, lib11, lib12, lib13, lib14, lib15)

from my_lib import Object, Object2, Object3
```

#### Skip import or file

If you want isort to skip a file, add `isort:skip_file` to the docstring:
```python
""" my_module.py
    Best module ever

   isort:skip_file
"""
```
.

If you just want to skip an import, add a `# isort:skip` comment at the end of the corresponding line.

### mypy

Mypy is a static type checker. \
Once you have annotated your code, mypy will help you check the code for common errors. \
Based on your type hints, mypy will be able to tell you that you are using the wrong type. \
The full documentation can be found [here](https://mypy.readthedocs.io/en/stable/).

To install isort using mypy, run
```
pip install mypy
```
.

You can then launch the `mypy` command to type check your whole project directory or you can pass one or several files:
```
mypy myscript.py myscript2.py
```
.

#### Skip line or file

You can ignore typing errors in an entire script by adding a `# type: ignore` or a `# mypy: ignore-errors` comment at the beginning of the file.

If you want mypy to skip a line only, add a `# type: ignore` comment at the end of the corresponding line.

### nbqa black

### nbqa isort

### end-of-file-fixer
