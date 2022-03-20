---
author: Anita Clement
title: "pre-commit hooks"
date: 2022-03-12T18:04:41Z
draft: false
tags: [
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

## Pre-commit configuration

## Installing the git hook scripts 

WIP