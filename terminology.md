# Terminology

## General

### Directory

This concept is basically the same as the one you think of when you think of a "folder" to store files in.

> [!NOTE]
> To see why I prefer this term over "folder", read the [folder metaphor on Wikipedia](https://en.wikipedia.org/wiki/Directory_%28computing%29#Folder_metaphor).

### Change

An addition, deletion, or modification to file(s) in the repository.

> [!NOTE]
> You can not save an empty directory. You add files which will bring their directories if they are nested in them.

### Commit

A saved state of files in the repository including auxiliary information like author & date of the save.

### Head

The currently checked out (loaded) version (save) of a repository.

### Local

Refers to directories, files, & repositories stored on the computer you develop on opposed to [remote](#remote).

### Remote

Refers to a server that can serve as the common source of truth for the Git repository that you (and your team, if applicable) are working on [locally](#local).

### Client

The tool used to run Git commands. This can be a command line or graphical user interface.

Below are some of the many options to use as clients in order of how much I like them.
1. [Sublime Merge](https://www.sublimemerge.com/).
2. [Git CLI](https://git-scm.com/downloads).
3. [Built-in VS Code collaboration tools](https://code.visualstudio.com/).

## Version Control

A system to track different versions of files. Specifically, Git makes the below tasks relatively easy.

- [Undo a specific change or all changes back to a prior version](./problems-and-solutions.md#undo-changes).
- [Handle non-linear development](./problems-and-solutions.md#non-linear-development).
- [Collaborate with your team without copy/pasting files](./problems-and-solutions.md#collaborate).
- [Audit who modified code and when they did it](./problems-and-solutions.md#audit-code).
- [Keep history on each machine in case the server hosting the code dies](./problems-and-solutions.md#migration).

## Four States Of Files

> [!IMPORTANT]
> A "Staged" file can be "Modified" at the same time if it has unstaged changes.
> This happens when a "Staged" file is modfied after being staged or if you state specific sections with a tool like VS Code or Sublime Merge.

![600](https://git-scm.com/book/en/v2/images/lifecycle.png)

### Untracked

Git has not been told to track the file.

> [!IMPORTANT]
> Untracked files do not display in `git status` if they match a path in `.gitignore`.

### Unmodified

No changes have been made since the last commit/stage.

> [!IMPORTANT]
> Unmodified files do not display in `git status`.

### Modified

File has changes that will not go into the next commit.

### Staged

Change that will go into the next commit.

### Ignored

[Git .gitignore Documentation](https://git-scm.com/docs/gitignore).

Ignored files are [untracked](#untracked) and match a patern in the `.gitignore` which tells Git to hide them from the [status command](commands.md#git-status) instead of showing them as [untracked](#untracked).

In addition (pun intended), [add command](commands.md#git-add) will not add ignored files unless you specifically add them and use a flag to force the matter.

See [ignoring untracked files](./problems-and-solutions.md#ignoring-untracked-files) for more information on using `.gitignore`.

> [!IMPORTANT]
> `.gitignore` only works on [untracked](#untracked) files. If you already [staged](#staged) or [committed](#commit) a file you wish to ignore, then follow the "[ignoring committed/staged files](./problems-and-solutions.md#ignoring-committedstaged-files)" solution.
