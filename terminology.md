# Terminology

Anytime I say the following terms, this is what I mean.

- "Change" is an addition, deletion, or modification to file(s).
- "Client" is the tool used to run Git commands. This can be a command line or graphical interface. Below are some of the many options to use as clients in the order I recommend them in.
    1. [Sublime Merge](https://www.sublimemerge.com/).
    2. [Git CLI](https://git-scm.com/downloads).
    3. [Built-in VS Code collaboration tools](https://code.visualstudio.com/).
- "Directory" is a "folder" that you use to store files in.
- "Head" is the currently checked out version of a repository.
- "Local" refers to directories, files, & repositories stored on the computer you develop on opposed to "Remote".
- "Remote" refers to a server that can serve as the common source of truth for the Git repository that you and your team are working on.

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
