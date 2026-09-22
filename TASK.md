# this is my own area#
# Phase 1 - Task 2: Python Package Setup
## pyproject.toml
Created:
- build system configuration
- project metadata
- package information
Explanation
[build-system]
This tells Python:
"How should this package be built?"
We use:
setuptools
because it is a common Python packaging tool.
[project]
This describes your software.
name
name = "dataset-tool"
Package identity.
Later:
pip install dataset-tool
version
version = "0.1.0"
Current development stage.
Meaning:
0 → not stable yet
1 → first stable release
description
description = "A CLI tool for preparing machine learning datasets"
Explains the purpose.
requires-python
requires-python = ">=3.10"
Means:
"This project requires Python 3.10 or newer."
Why?
Because some Python features depend on version.
after that, in the integreated terminal,
write "pip install ." and you can install your first own created package.
now we create :
src/
└── dataset_tool/
    └── __init__.py
Why?
Because Python needs a package.
__init__.py tells Python:
"This folder is a Python package."
commands:
mkdir -p src/dataset_tool
touch src/dataset_tool/__init__.py
then press this :
"find src -type f"
 to see what src contains
after that
*.egg-info/ => in gitignore
currently pyproject.toml does not know  where yr package lives, so we need to tell setup:
"Look inside src/ for packages."
[tool.setuptools.packages.find]
where = ["src"]
so, we need to add this in the .toml file below.
now uninstall the previous package , then install it again. this time, it'll install the updated version.
so now, before commit it into github, first write two command.
1. git status --ignored
2.find . -maxdepth 3 -type f
normal "git status" shows , modified files, stages files, untracked files, but it doen't shows ignored files. so number 1 is showing the the files what git is ignoring.
*"find . -maxdepth 3 -type f"
This command is not a Git command.
It is a Linux/macOS filesystem command.
Let's break it down.
Why use it here?
Because we want to inspect the project structure before committing.
We want to answer:
"Am I accidentally committing something I don't want?
this command will show f for files, and maximum 3 depth of the directories.
Now we can safely prepare the second commit.
Before that, one small task:
Run:
git add .
Then:
git status
Before committing, one final professional check
Run:
git diff --cached
Why?
Because git status only tells us which files changed.
git diff --cached tells us what actually changed inside those files.
Example:
git status:
modified: README.md
but maybe the change is:
+ deleted entire documentation
The difference matters.