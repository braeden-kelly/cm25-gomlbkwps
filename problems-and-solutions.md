# Problems & Solutions

> [!IMPORTANT]
> Most of the below problems/solutions assume you have a local repository already with the exception of [Create Git Repository](#create-git-repository) which helps you create a local repository.

## Create Git Repository

A Git repository (often called a repo), looks like a normal directory with a `.git` subdirectory in it. How you go about initializing your repository depends on whether you want to base it off from an existing codebase or a local directory.

### Clone An Existing Codebase

Cloning a Git repository from a remote server can be done using the [git clone command](./commands.md#git-clone).

This will create a new directory with the same name as the repository and place the contents in the directory.

```bash
git clone git@github.com:DustinMEastway/git-on-my-level.git
```

### Initialize From A Local Directory

Creating a Git repostiroy from a local directory (even if it is empty) can be done using the [git init command](./commands.md#git-init).

```bash
git init
```

## Get Status Of A Repository

Use the [git status command](./commands.md#git-status) to see the state of your local repository.

This will tell you the current branch, how many commits ahead and/or behind it you are, and your uncommitted changes.

```bash
git status
```

### List Branches In Repository

#### List Local Branches

Use the [git branch command](./commands.md#git-branch) to display a list of branches on the local branches and display the branch you are currently on.

```bash
git branch
```

#### List Remote Branches

Use the [git branch command](./commands.md#git-branch) with the `--remote` (or `-r`) flag to display remote branches that existed last time you fetched information from the remote repositories.

> [!TIP]
> Use the [git fetch command](./commands.md#git-fetch) before the below command to get updated information.
> ```bash
> git fetch
> ```

```bash
git branch --remote
```

## Handle Untracked Files

### Add Files To Repository

### Ignore Files From Repository

## Undo Changes

### Undo Committed Changes

### Undo Unstaged Changes

### Undo Staged Changes

## Non-Linear Development

## Collaborate

### Use Code From Others

## Audit Code

### Figure Out Who Modified Code Last

## Migration

### Moving Repositoy To A New Server

![400](https://git-scm.com/book/en/v2/images/distributed.png)
