# precommit-make
precommit hooks for Make for Bioinformatics

## Overview

To my knowledge, I am the only bioinformatician to use Make
for bioinformatics pipelining beyond standard software compilation.
As such, I have certain enhanced formatting conventions and needs
that are not commonly used in other contexts. This pre-commit
hook set will eventually enforce these conventions on git-tracked
Makefiles.

## Format Specification: Make for Bioinformatics

### Phony Targets

All files, if they contain any rules whatsoever, should have `.PHONY` defined with at least `all` and `clean` as targets. `all` and `clean` should then be valid rules in the same file.

### Special Built-In Target Names



### Variables

### Rules


### Inherited from generalist Make

The following content is derived from [the GNU Coding Standards](https://www.gnu.org/prep/standards/html_node/Makefile-Conventions.html#Makefile-Conventions).

#### Makefile Basics

 - according to general conventions, the variable `SHELL` should be defined as `SHELL = /bin/sh`; this seems unnecessary in a bioinformatics context in which, at the least, conda is active. consider elevating this to `SHELL = /bin/bash` at the least.
 - prepending `./` or `$(srcdir)` is clearly important, but in applications there are likely multiple source directories; the `$(srcdir)` convention cannot be strictly followed or must be modified.
 - it seems like an enormous amount of infrastructure could be simplified with clever use of `VPATH = /search/dir` or `vpath %.suffix /search/dir`. it's not entirely clear whether this is an improvement over complete specification when it comes to resolving large dependency trees.

#### Utilities in Makefiles
 - evidently symlinks are not supported on some systems, and truly platform independent coding requires a fallback in all uses. that's rough though.
 - don't directly call `make`: `$(MAKE)`. this allows variables to be passed to the recursive call correctly.
 - only acceptable directly-called utilities are: `awk` `cat` `cmp` `cp` `diff` `echo` `egrep` `expr` `false` `grep` `install-info` `ln` `ls` `mkdir` `mv` `printf` `pwd` `rm` `rmdir` `sed` `sleep` `sort` `tar` `test` `touch` `tr` `true`. this is slightly wild, in both directions.
 - `mkdir -p` is not safe :(
 - investigate the use of M4sh
#### Command Variables

#### DESTDIR

#### Directory Variables

#### Standard Targets

#### Install Command Categories





## Citations

This package was created with _Cookiecutter_ and the *`audreyfeldroy/cookiecutter-pypackage`* project template.

 - Cookiecutter: https://github.com/audreyr/cookiecutter
 - `audreyfeldroy/cookiecutter-pypackage`: https://github.com/audreyfeldroy/cookiecutter-pypackage


## Version History

22 December 2020: created initial issues and milestones, started infrastructure dev

15 December 2020: drafted initial format specification
