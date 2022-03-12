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

# PEP 8 or How to Make your Code Readable

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

## Code Lay-out

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

# Python packages for formatting, typing and linting

## flake8

## black

## isort

## mypy

## nbqa black

## nbqa isort

## end-of-file-fixer
