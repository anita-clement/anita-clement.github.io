---
author: Anita Clement
title: "pre-commit"
date: 2022-03-12T18:04:41Z
draft: false
tags: [
    "pre-commit",
    "Python",
    "git",
    "commit",
    "hooks"
]
---

## Git hooks and pre-commit

Client-side git hooks are custom scripts designed to fire off when some operations happen like committing or merging.
They allow use to identify simple issues before submitting our code for review. Our code review will then be able to focus on the actual code rather than styling issues.

The limitation of hooks is that they are difficult to share across projects. You have to manually change them to make them work with your project structure. Their install is also sometimes painful as they can be written in a language different from your project. That is why **pre-commit** was created.

Pre-commit is a multi-language package manager for pre-commit hooks. It will take care of the installation of all the hooks you have listed and will execute them before every commit.

Pre-commit's documentation can be found [here](https://pre-commit.com/).

## Pre-commit install

You will first need to have the pre-commit package manager installed. \
This can be done via pip for example by running the following command:
```
pip install pre-commit
```
. \
You can also install it using conda, homebrew, ...

## Pre-commit configuration

Next step is to add a pre-commit configuration file to your repository. \
Pre-commit will look for a file called *.pre-commit-config.yaml* at the root of your repository. \
You can generate a basic configuration file for Python by running
```
pre-commit sample-config
```
. \
It should look more or less like this (it might have gotten updated since then):
```yaml
repos:
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v3.2.0
    hooks:
    -   id: trailing-whitespace
    -   id: end-of-file-fixer
    -   id: check-yaml
    -   id: check-added-large-files
```
. \
The above means that 4 of the hooks scripts defined in the linked github repository will be installed (see section on [Installing the git hook scripts](#installing-git-hook-scripts) to install the script from your config) and run each time you try to commit. \
You can check in details what each of these 4 scripts does by looking at the code in the repository. Here is a short description:
- `trailing-whitespace`: removes any trailing whitespace in code.
- `end-of-file-fixer`: ensures files end with a blank line.
- `check-yaml`: checks YAML files for valid syntax.
- `check-added-large-files`: prevents any large (500 KB+) files from entering version control.


## <a name="installing-git-hook-scripts"></a>Installing the git hook scripts 

Installing the git hook scripts is very easy. \
Once your configuration file is defined, and provided `pre-commit` is installed, you simply need to run the following command:
```
pre-commit install
```
. \
It will install pre-commit into your git hooks. \
From that point on, `pre-commit` will run automatically on `git commit`.

## Run against all the files

It can happen that you install pre-commit after having started your project or that you have updated your pre-commit config by adding a hook for example. \
In that case, you probably want to run the hooks against all your files instead of the staged ones only. \
To do so, you will need to pass the `--all-files` argument:
```
pre-commit run --all-files
```
.
