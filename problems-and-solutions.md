# Problems & Solutions

> [!IMPORTANT]
> Commands use `<>` to wrap sections of code that you should replace and `[]` to denote optional segments.
>
> Shorthand aliases (one "-" instead of "--") require a space instead of an equal sign when they accept values.
> Some commands (such as [git log](#git-log)) accept an even shorter alias where you can pass the value directly after a single "-" without a space.
>
> For example, all of the below commands log up to 3 of the last commits.
> ```bash
> git log --max-count=3
> git log -n 3
> git log -3
> ```
>
> For commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.
>
> For commands that accept commit hash(es) (or [HEAD](./terminology.md#head)) you can use `<commit hash>~<number>` to go back a `<number>` of commits from `<commit hash>` or the shorthand `<commit hash>~` to go back one.

> [!NOTE]
> Most of the below problems/solutions assume you have a local repository already with the exception of [Create Git Repository](#create-git-repository) which helps you create a local repository.
>
> Solutions are roughly in the order I would expect you to run into the problems, but this is difficult to fully predict.

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

### List Commits

Use [git log](./commands.md#git-log) to display [commits](./terminology.md#commit) that exist on the current branch/[HEAD](./terminology.md#head).

I primarily use this command to display commit hashes for other commands or messages, authors, & dates to make sure my history looks like I expect it to.

```bash
git log
```
- `[--graph]` Displays an ASCII graph of branch & merge history.
    - `[--pretty=oneline]` pairs nicely with this command.
- `[--max-count=<number>]` Limit the max number of commits displayed.
    - **Alias(es)** `-n <number>`, `-<number>`.
- `[--patch]` Used to display a diff with commit information, but I generally use [git diff](#git-diff) instead.
- `[--pretty=<format>]` Used to change the amount & format of information displayed for each commit.
    - **Note**: See [git log pretty formats](https://git-scm.com/docs/git-log#_pretty_formats) for official documentation on supported formats.
    - Use `oneline` Displays the hash, branches pointing at the commit, & first line of message for each commit.
    - Use `format:"%H %s"` Display the hash & first line of message for each commit.

### Display Changes

#### Display Unstaged Changes

Use [git diff](./commands.md#git-diff) to display changed lines in [modified](./terminology.md#modified) files.

Optionally, pass file(s) as a final parameter to limit output to changes made in those files.

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

```bash
git diff [<path to file(s)>]
```
- `[<path to file(s)>]` you wish diff (default: diff all files).

#### Display Staged Changes

Use [git diff](./commands.md#git-diff) with the `--staged` flag to display changed lines in [staged](./terminology.md#staged) files.

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

```bash
git diff --staged [<path to file(s)>]
```
- `[<path to file(s)>]` you wish diff (default: diff all files).
- `[--staged]` display [staged](./terminology.md#staged) changes instead of [modified](./terminology.md#modified) changes.
    - **Alias(es)** `--cached`.

#### Display Committed Changes

Use [git diff](./commands.md#git-diff) with the `[<commit>]` parameter to display [committed changes](./terminology.md#committed-change).

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

> [!TIP]
> For Git commands that accept commit hash(es) (or [HEAD](./terminology.md#head)) you can use `<commit hash>~<number>` to go back a `<number>` of commits from `<commit hash>` or the shorthand `<commit hash>~` to go back one.

```bash
git diff <commit> [<path to file(s)>]
```
- `[<commit>]` You can pass various configurations of commit hashes (IDs) to display changes relative to those commits.
    - Use `<commit hash>` to display all changes since (but not including) the provided commit including your uncommitted work.
    - Use `<commit hash>~` to display all changes in and since the provided commit including your uncommitted work.
    - Use `<commit hash>~ <commit hash>` to display all changes in the provided commit.
    - Use `<start commit hash>~ <end commit hash>` to display all changes in the commit with `<start commit hash>`, the commit with `<end commit hash>` and all commits between them.
- `[<path to file(s)>]` you wish diff (default: diff all files).

## Add Files To Repository

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

Use [git add](./commands.md#git-add) to move the [untracked](./terminology.md#untracked) changes of adding the file(s) to [staged](./terminology.md#staged) for the next time you [save your changes](./problems-and-solutions.md#save-changes).

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
> `.gitignore` only works on [untracked](./terminology.md#untracked) files. If you already [staged](./terminology.md#staged-change) and/or [committed](./terminology.md#committed-change) changes in a file you wish to ignore, then follow the [ignoring committed/staged files solution](./problems-and-solutions.md#ignoring-committedstaged-files).

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

2. Use [git add](./commands.md#git-add) to move the [untracked](./terminology.md#untracked) changes of removing the file(s) (not adding the temporary file(s)) to [staged](./terminology.md#staged).

```bash
git add <path to file(s)>
```

3. Rename the file(s) back to the original name(s).

4. Now that you have staged their deletions, the files will show up as [untracked](./terminology.md#untracked) which means you can use the [ignoring untracked files solution](./problems-and-solutions.md#ignoring-untracked-files).

## Save Changes

To save a change, you must first use [git add](./commands.md#git-add) to move the [untracked](./terminology.md#untracked-change) or [unstaged](./terminology.md#unstaged-change) change to the [staged](./terminology.md#staged-change) state.

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

```bash
git add <path to file(s)>
```
- `<path to file(s)>` you wish to [stage](./terminology.md#staged).

Then use [git commit](./commands.md#git-commit) move the changes to a [committed](./terminology.md#committed-change) state.

```bash
git commit -m "<message>"
```
- `[--message="<message>"]` adds a line to the commit message instead of bringing the editor up.
    - **Alias(es)**: `-m "<message>"`.
    - **Note**: Technically the quotes are not required, but I recommend always adding them to keep messages with spaces together.

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
