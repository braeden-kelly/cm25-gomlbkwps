# Git On My Level: Bridging Knowledge with Practical Solutions

If you write code, you're likely using Git. If not, you probably should be—unless you enjoy the thrill of losing track of your work and spending hours hunting down bugs. But don’t worry, this talk isn't about convincing you why Git is a must; there are plenty of resources for that. Instead, we’ll address why many developers feel uneasy about performing complex operations with Git. Although there are numerous resources available to learn Git, I believe a major reason for the unease is the traditional method of teaching—introducing one command or term at a time, often without practical examples of how to use them.

In this session, we’ll bridge that gap. We’ll tackle common Git challenges, dive into practical solutions, and dissect the mechanics behind each approach. You'll learn the pros and cons of different strategies and gain actionable insights to resolve frequent issues faced by you and your team during collaboration.

By the end of this session, you'll be equipped with the skills and confidence to handle Git more effectively and improve your development workflow.

## Introduction

Most of the information used in this presentation was found in the [Pro Git book](https://git-scm.com/book/en/v2).

I will start with quickly running through [prerequisite knowledge](#prerequisite-knowledge) for 15 minutes for those with shaky Git foundations.

Next, we can use that knowledge to work through [problems & solutions](#problems--solutions) for 35 minutes.

Finally, I will leave 10 minutes open at the end for questions.

## Prerequisite Knowledge

### Definitions

Anytime I say the following terms, this is what I mean.

- "Change" is an addition, deletion, or modification to file(s).
- "Client" is the tool used to run Git commands. This can be a command line or graphical interface. Below are some of the many options to use as clients in the order I recommend them in.
    1. [Sublime Merge](https://www.sublimemerge.com/).
    2. [Git CLI](https://git-scm.com/downloads).
    3. [Built-in VS Code collaboration tools](https://code.visualstudio.com/).
- "Directory" is a "folder" that you use to store files in.
- "Head" is the currently checked out version of a repository.
- "Local" refers to directories, files, & repositories stored on your computer opposed to "Remote".
- "Remote" refers to directories, files, & repositories stored on a server.

#### Version Control

A system to track different versions of files. Specifically, Git makes the below tasks relatively easy.

- [Undo a specific change or all changes back to a prior version](#undo-changes).
- [Handle non-linear development](#non-linear-development).
- [Collaborate with your team without copy/pasting files](#collaborate).
- [Audit who modified code and when they did it](#audit-code).
- [Keep history on each machine in case the server hosting the code dies](#migration).

#### Four States Of Files

> [!WARNING]
> A "Staged" file can be "Modified" at the same time if it has unstaged changes.
> This happens when a "Staged" file is modfied after being staged or if you state specific sections with a tool like VS Code or Sublime Merge.

![600](https://git-scm.com/book/en/v2/images/lifecycle.png)

##### Untracked

Git has not been told to track the file.

> [!NOTE]
> Untracked files do not display in `git status` if they match a path in `.gitignore`.

##### Unmodified

No changes have been made since the last commit/stage.

> [!NOTE]
> Unmodified files do not display in `git status`.

##### Modified

File has changes that will not go into the next commit.

##### Staged

Change that will go into the next commit.

### Commands

Commands in this section are in alphabetical order and will use `<>` to wrap sections of code that you should replace and `[<>]` to denote optional parameters.

[Click here for in-dept command documentation](https://git-scm.com/docs/git#_git_commands), but the minimal set of commands below has been enough for me over the past 8 years.

#### Git Clone

[Git Clone Documentation](https://git-scm.com/docs/git-clone).

Used to clone/copy/download an existing codebase from a server hosting a Git repository.

`git clone <repository url> [<directory name>]`.
- `<repository url>` where the git repository is stored.
- `[<directory name>]` (optional) to place the cloned repository into.
    - **Note**: Defaults to `<repository name>` if not provided.

#### Git Init

[Git Init Documentation](https://git-scm.com/docs/git-init).

Used to turn a local directory into a Git repository.

> [!WARNING]
> This turns the current directory into a repository. If you want a subdirectory, then create it, move into it, and run the command there.

`git init`.

## Problems & Solutions

### Create Git Repository

A Git repository (often called a repo), looks like a normal directory with a `.git` subdirectory in it. How you go about initializing your repository depends on whether you want to base it off from an existing codebase or a local directory.

#### Clone An Existing Codebase

Cloning a Git repository from a remote server can be done using the [git clone command](#git-clone).

This will create a new directory with the same name as the repository and place the contents in the directory.

```bash
git clone git@github.com:DustinMEastway/git-on-my-level.git
```

#### Initialize From A Directory

Creating a Git repostiroy from a local directory (even if it is empty) can be done using the [git init command](#git-init).

```bash
git init
```

### Undo Changes

### Non-Linear Development

### Collaborate


### Audit Code

### Migration
