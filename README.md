Getting started
================

<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

<div>

![CI](https://github.com/fastai/nbdev/actions/workflows/test.yaml/badge.svg)

</div>

*NB: This is nbdev v2, a major upgrade of nbdev. Whilst the differences
to nbdev1 aren’t huge, it does require some changes. The old version
docs are at [nbdev1.fast.ai](https://nbdev1.fast.ai). You can use
version-pinning in `settings.ini` (i.e `'nbdev<2'`) to stop nbdev from
upgrading. To upgrade, follow the [migration
tutorial](https://nbdev.fast.ai/migrating.html).*

------------------------------------------------------------------------

`nbdev` is a system for *exploratory programming*. Simply write
notebooks with lightweight markup and get high-quality documentation,
tests, continuous integration, and packaging for free!

`nbdev` makes debugging and refactoring your code much easier than in
traditional programming environments since you always have live objects
at your fingertips. `nbdev` also promotes software engineering best
practices because tests and documentation are first class.

- **Documentation** is automatically generated using
  [Quarto](https://quarto.org/) and hosted on [GitHub
  Pages](https://pages.github.com/). Docs support LaTeX, are searchable,
  and are automatically hyperlinked (including out-of-the-box support
  for many packages via
  [`nbdev-index`](https://github.com/fastai/nbdev-index)). You also have
  fine-grained control over how cells are displayed.
- **Publish packages to PyPI and conda** as well as tools to simplify
  package releases. Python best practices are automatically followed,
  for example, only exported objects are included in `__all__`
- **Two-way sync between notebooks and plaintext** source code allowing
  you to use your IDE for code navigation or quick edits.
- **Tests** written as ordinary notebook cells are run in parallel with
  a single command. You have fine-grained control over which tests are
  run.
- **Continuous integration** out-of-the-box with [GitHub
  Actions](https://github.com/features/actions) that run your tests on
  each push and rebuild docs on each merge.
- **Git-friendly notebooks** with tools that clean unwanted metadata and
  render merge conflicts in a human-readable format.
- … and much more!

## Install

nbdev works on macOS, Linux, and most Unix-style operating systems. It
works on Windows under WSL, but not under cmd or Powershell.

You can install nbdev with pip:

    pip install nbdev

… or with conda (or mamba):

    conda install -c fastai nbdev

Note that `nbdev` must be installed into the same Python environment
that you use for both Jupyter and your project.

## How to use nbdev

The best way to learn to use nbdev is to complete one of these tutorials
(we suggest replicating each step to solidify your understanding):

- [Written tutorial](https://nbdev.fast.ai/tutorial.html)

**Video step-by-step walkthru** (to view full screen, click the little
square in the bottom right of the video; to view in a separate Youtube
window, click the Youtube logo):

<div>

<div>

<a href="http://www.youtube.com/watch?v=l7zS8Ld4_iA" target="_blank"
title="nbdev walkthrough"><img
src="https://github.com/fastai/logos/raw/main/nbdev_walkthrough.png" /></a>

</div>

</div>

(There’s an [alternate version of the
walkthru](https://youtu.be/67FdzLSt4aA) available with the coding
sections sped up using the `unsilence` python library – it’s 27 minutes
faster, but it’s be harder to follow along with.)

You can run `nbdev_help` from the terminal to see the full list of
available commands:

``` python
!nbdev_help
```

    nbdev_bump_version              Increment version in settings.ini by one
    nbdev_changelog                 Create a CHANGELOG.md file from closed and labeled GitHub issues
    nbdev_clean                     Clean all notebooks in `fname` to avoid merge conflicts
    nbdev_conda                     Create and upload a conda package
    nbdev_create_config             Create a config file
    nbdev_deploy                    Deploy docs to GitHub Pages
    nbdev_docs                      Generate docs
    nbdev_export                    Export notebooks in `path` to Python modules
    nbdev_filter                    A notebook filter for Quarto
    nbdev_fix                       Create working notebook from conflicted notebook `nbname`
    nbdev_ghp_deploy                Deploy docs in `doc_path` from settings.ini to GitHub Pages
    nbdev_help                      Show help for all console scripts
    nbdev_install                   Install Quarto and the current library
    nbdev_install_hooks             Install Jupyter and git hooks to automatically clean, trust, and fix merge conflicts in notebooks
    nbdev_install_quarto            Install latest Quarto on macOS or Linux, prints instructions for Windows
    nbdev_merge                     Git merge driver for notebooks
    nbdev_migrate                   Convert all directives and callouts in `fname` from v1 to v2
    nbdev_new                       Create a new project from the current git repo
    nbdev_prepare                   Export, test, and clean notebooks
    nbdev_preview                   Start a local docs webserver
    nbdev_pypi                      Create and upload Python package to PyPI
    nbdev_quarto                    Create Quarto docs and README.md
    nbdev_readme                    Render README.md from index.ipynb
    nbdev_release                   Release both conda and PyPI packages
    nbdev_release_gh                Calls `nbdev_changelog`, lets you edit the result, then pushes to git and calls `nbdev_release_git`
    nbdev_release_git               Tag and create a release in GitHub for the current version
    nbdev_sidebar                   Create sidebar.yml
    nbdev_test                      Test in parallel notebooks matching `fname`, passing along `flags`
    nbdev_trust                     Trust notebooks matching `fname`
    nbdev_update                    Propagate change in modules matching `fname` to notebooks that created them

## Installing Quarto

Note that when you setup your first project, nbdev will attempt to
automatically download and install [quarto](https://quarto.org/) for
you. This is the program that we use to create your documentation
website.

Quarto’s standard installation process requires root access, and nbdev
will therefore ask for your root password during installation. For most
people, this will work fine and everything will be handled automatically
– if so, you can skip over the rest of this section, which talks about
installing without root access.

If you need to install quarto without root access on Linux, first `cd`
to wherever you want to store it, then [download
quarto](https://quarto.org/docs/get-started/), and type:

``` bash
dpkg -x quarto*.deb .
mv opt/quarto ./
rmdir opt
mkdir -p ~/.local/bin
ln -s "$(pwd)"/quarto/bin/quarto ~/.local/bin
```

To use this non-root version of quarto, you’ll need `~/.local/bin` in
your [`PATH` environment
variable](https://linuxize.com/post/how-to-add-directory-to-path-in-linux/).
(Alternatively, change the `ln -s` step to place the symlink somewhere
else in your path.)

## FAQ

### Q: Someone told me not to use notebooks for “serious” software development!

[Watch this video](https://youtu.be/9Q6sLbz37gk). Don’t worry, we still
get this too, despite having used `nbdev` for a wide range of “very
serious” software projects over the last three years, including [deep
learning libraries](https://github.com/fastai/fastai), [API
clients](https://github.com/fastai/ghapi), [Python language
extensions](https://github.com/fastai/fastcore), [terminal user
interfaces](https://github.com/nat/ghtop), and more!

## nbdev in the wild

### fastai ecosystem

`nbdev` has been used to build innovative software in the fastai
ecosystem, including the [`fastai`](https://docs.fast.ai/) deep learning
library which implements a [unique layered API and callback
system](https://arxiv.org/abs/2002.04688), and
[`fastcore`](https://fastcore.fast.ai/), which supercharges Python
leveraging its dynamic nature. Furthermore, `nbdev` allows a very small
number of developers to maintain and grow a [large
ecosystem](https://github.com/fastai) of software engineering, data
science, machine learning, and devops tools.

## Contributing

If you want to contribute to `nbdev`, be sure to review the
[contributions
guidelines](https://github.com/fastai/nbdev/blob/master/CONTRIBUTING.md).
This project adheres to fastai’s [code of
conduct](https://github.com/fastai/nbdev/blob/master/CODE_OF_CONDUCT.md).
By participating, you are expected to uphold this code. In general, we
strive to abide by generally accepted best practices in open-source
software development.

Make sure you have `nbdev`’s git hooks installed by running
[`nbdev_install_hooks`](https://nbdev.fast.ai/clean.html#nbdev_install_hooks)
in the cloned repository.

## Copyright

Copyright © 2019 onward fast.ai, Inc. Licensed under the Apache License,
Version 2.0 (the “License”); you may not use this project’s files except
in compliance with the License. A copy of the License is provided in the
LICENSE file in this repository.
