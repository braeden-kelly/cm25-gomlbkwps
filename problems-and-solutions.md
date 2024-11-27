# Problems & Solutions

> [!NOTE]
> Most of the below problems/solutions assume you have a local repository already with the exception of [Create Git Repository](#create-git-repository) which helps you create a local repository.
>
> Code will use `<>` to wrap sections of code that you should replace and `[]` to denote optional segments.

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

### List Branches

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

## Add Files To Repository

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

Use [git add](https://git-scm.com/docs/git-add) to move the [untracked](./terminology.md#untracked) changes of adding the file(s) to [staged](./terminology.md#staged) for the next time you [save your changes](./problems-and-solutions.md#save-changes).

```bash
git add <path to file(s)>
```

> [!TIP]
> To undo this action see "[undo staged changes](problems-and-solutions.md#undo-staged-changes)".

## Removing Files From Repository

Sometimes you want to have files in your repository without having them checked in to share with others.

For example, environment files may contain private values that you do not want checked in.

### Ignoring Untracked Files

Create a [.gitignore file](https://git-scm.com/docs/gitignore) and add patterns that match files you wish for Git to ignore instead of displaying as [untracked](./terminology.md#untracked).

> [!IMPORTANT]
> `.gitignore` only works on [untracked](./terminology.md#untracked) files. If you already [staged](./terminology.md#staged) or [committed](./terminology.md#commit) a file you wish to ignore, then follow the "[ignoring committed/staged files](./problems-and-solutions.md#ignoring-committedstaged-files)" solution.

```bash
# Lines starting with "#" are comments.

# Use the name of a file/directory to ignore it.
# Ignore all files, nested files, & subdirectories called ".DS_Store".
.DS_Store

# Use "\" to escape special characters ("#", "*", "?") in file names.
# Ignore all files, nested files, & subdirectories called "my#special?file*".
my\#special\?file\*

# Use "/" to the end of a pattern ignores directories, but not files.
# Ignore all subdirectories named "node_modules".
node_modules/

# Use "/" to the beginning or middle of a pattern makes the path relative to the current ".gitignore" file.
# Ignore the "generated" subdirectory at the same level as the ".gitignore" file.
/generated/
```

### Ignoring Committed/Staged Files

`.gitignore` only works on [untracked](./terminology.md#untracked) files. If you already [staged](./terminology.md#staged) or [committed](./terminology.md#commit) a file then do the following.

1. Rename the file(s) to temporary name(s).

2. Use [git add](https://git-scm.com/docs/git-add) to move the [untracked](./terminology.md#untracked) changes of removing the file(s) (not adding the temporary file(s)) to [staged](./terminology.md#staged).

```bash
git add <path to file(s)>
```

3. Rename the file(s) back to the original name(s).

4. Now that you have staged their deletions, the files will show up as [untracked](./terminology.md#untracked) which means you can use the "[ignoring untracked files](./problems-and-solutions.md#ignoring-untracked-files)" solution.

## Save Changes

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
