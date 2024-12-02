# Commands

[Click here for the official command documentation](https://git-scm.com/docs/git#_git_commands), but the minimal set of commands below has been enough for me since I started using Git in 2018 (or earlier).

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
> Some commands, such as [git diff](#git-diff) need some parameters in a specific order (`[<commit>]` must come before `[<path to file(s)>]` if both are specified).
> In such cases, I list them in their required order below the command.
>
> For commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.
>
> For commands that accept commit hash(es) (or [HEAD](./terminology.md#head)) you can use `<commit hash>~<number>` to go back a `<number>` of commits from `<commit hash>` or the shorthand `<commit hash>~` to go back one.

> [!NOTE]
> Commands in this section are in alphabetical order.

## Essential Commands

These are the commands that you need to know how to use in order to get the most out of your use of Git.

### Git Add

[Official Git Add Documentation](https://git-scm.com/docs/git-add).

Moves all [untracked](./terminology.md#untracked-change) & [unstaged](./terminology.md#unstaged-change) changes in added [untracked](./terminology.md#untracked) & [modified](./terminology.md#modified) files to the list of [staged](./terminology.md#staged-change) changes in preparation for the next [commit command](#git-commit).

> [!WARNING]
> You can pass "\*" as `<path to file(s)>` in the below command to stage all files, but I recommend against it because you are likely to stage unintended changes.

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

> [!TIP]
> To undo staging changes, use [git restore](#git-restore) with the `--staged` flag.

```bash
git add <path to file(s)>
```
- `<path to file(s)>` you wish to [stage](./terminology.md#staged).

### Git Branch

[Official Git Branch Documentation](https://git-scm.com/docs/git-branch).

Used to display the list of local or remote (see `--remote`) branches.

```bash
git branch
```
- `[--remote]` displays branches on all remote repositories that your local repository is connected to.
    - **Alias(es)** `-r`.
    - **Note**: This list is based on the last time your local repository got information from the remote repository. If you want an updated list, use [fetch command](#git-fetch) or [pull command](#git-pull) before running this command.

### Git Cherry Pick

### Git Clone

[Official Git Clone Documentation](https://git-scm.com/docs/git-clone).

Used to clone/copy/download an existing codebase from a server hosting a Git repository.

```bash
git clone <repository url> [<directory name>]
```
- `<repository url>` where the git repository is stored.
- `[<directory name>]` (optional) to place the cloned repository into.
    - **Note**: Defaults to `<repository name>` if not provided.

### Git Commit

[Official Git Commit Documentation](https://git-scm.com/docs/git-commit).

Used to put all [staged changes](./terminology.md#staged-change) into a [committed](./terminology.md#committed-change) state.

> [!TIP]
> The commit command only [commits](./terminology.md#committed-change) [staged changes](./terminology.md#staged-change), so make sure to use the [add command](#git-add) before using it.

```bash
git commit
```
- `[--message="<message>"]` adds a line to the commit message instead of bringing the editor up.
    - **Alias(es)**: `-m "<message>"`.
    - **Note**: Technically the quotes are not required, but I recommend always adding them to keep messages with spaces together.
- `[--all]` [commits](./terminology.md#committed-change) all [unstaged changes](./terminology.md#unstaged-change) (but not [untracked changes](./terminology.md#untracked-change)) in additon to [staged changes](./terminology.md#staged-change).
    - **Alias(es)**: `-a`.
    - **Note**: I recommend against use of this flag. Most people regularly commit unintended changes due to using it.

### Git Diff

[Official Git Diff Documentation](https://git-scm.com/docs/git-diff).

Used to display changed lines in [modified](./terminology.md#modified) (use `--staged` for [staged](./terminology.md#staged)) files.

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

```bash
git diff [<commit>] [<path to file(s)>]
```
- `[--staged]` display [staged](./terminology.md#staged) changes instead of [modified](./terminology.md#modified) changes.
    - **Alias(es)** `--cached`.
    - **Note**: Not compatible with `[<commit>]`.
- `[<commit>]` You can pass various configurations of commit hashes (IDs) to display changes relative to those commits.
    - **Note**: Not compatible with `[--staged]`.
    - Use `<commit hash>` to display all changes since (but not including) the provided commit including your uncommitted work.
    - Use `<commit hash>~` to display all changes in and since the provided commit including your uncommitted work.
    - Use `<commit hash>~ <commit hash>` to display all changes in the provided commit.
    - Use `<start commit hash>~ <end commit hash>` to display all changes in the commit with `<start commit hash>`, the commit with `<end commit hash>` and all commits between them.
- `[<path to file(s)>]` you wish diff (default: diff all files).

### Git Init

[Official Git Init Documentation](https://git-scm.com/docs/git-init).

Used to turn a local directory into a Git repository.

> [!WARNING]
> This turns the current directory into a repository. If you want a subdirectory, then create it, move into it, and run the command there.

```bash
git init
```

### Git Log

[Official Git Log Documentation](https://git-scm.com/docs/git-log).

This command displays information about [commits](./terminology.md#commit) from newest to oldest commit.

Some information includes their message, author, & date as well as commit hashes which other commands like [git diff](#git-diff) can use to identify them.

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

### Git Pull

### Git Push

### Git Rebase

### Git Revert

### Git Stash

### Git Status

[Official Git Status Documentation](https://git-scm.com/docs/git-status).

Used to display general information about your state in the current repository.

It will display the current branch, how many commits ahead and/or behind the remote branch your local branch is, and your [untracked](./terminology.md#untracked), [modified](./terminology.md#modified), & [staged](./terminology.md#staged) file(s).

```bash
git status
```

### Git Switch

## Extra Commands

These commands could come in handy in specific situations, but are unlikely to to be needed in regular workflows.

### Git Fetch

[Official Git Fetch Documentation](https://git-scm.com/docs/git-fetch).

Updates its information (branches, commits, etc.) of the remote repository your local repository is connected to.

```bash
git fetch
```
- `[--prune]` In addition to getting missing information it also removes local information (branches, commits, etc.) about items removed from the remote repository.
    - **Alias(es)** `-p`.
    - **Note**: I always want my `git fetch` to prune deleted information, so I used `git config fetch.prune true` to make that happen without needing to type `-p` every time.

## Unneeded Commands

The below commands have alternatives that I would recommend using instead.

### Git Checkout

> [!CAUTION]
> This command can undo changes before they are committed which makes them impossible to recover.
> If you may want the changes back later, first [save them](./problems-and-solutions.md#save-changes), then undo the changes in a second commit.

This command had different uses depending on its context. I recommend using the below alternatives that specialize in specific uses which makes what you are using them for more clear.
- Use [git restore](#git-restore) to undo [unstaged changes](./terminology.md#unstaged-change).
- Use [git switch](#git-switch) to change [branches](./terminology.md#branch).

### Git Move

> [!IMPORTANT]
> Git does not directly track file movement (renaming is just moving) as you do it. Instead it looks at the content of added/deleted files in a commit to decide which ones match close enough for it to consider them a move/rename instead of a separate add change & delete change.
>
> This means that if you make many changes to a file's contents at the same time as you move it, it will be counted as adding a new file and will lose its history. Instead, move the file without changing its contents, [save your changes](./problems-and-solutions.md#save-changes), modify its contents, then [save your changes](./problems-and-solutions.md#save-changes) again.

> [!NOTE]
> To see why this command is not essential read the [moving/renaming a file solution](./problems-and-solutions.md#moving-renaming-a-file).

```bash
git mv <path to file> <new path to file>
```
- `<path to file>` you wish to move/rename.
- `<new path to file>` you wish to create & [stage](./terminology.md#staged).

### Git Remove

[Official Git Remove Documentation](https://git-scm.com/docs/git-rm).

Used to delete file(s) & [stage](./terminology.md#staged) them with a single command.

> [!NOTE]
> To see why this command is not essential read the [deleting files solution](./problems-and-solutions.md#deleting-files).

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

```bash
git rm <path to file(s)>
```
- `<path to file(s)>` you wish to delete & [stage](./terminology.md#staged).

### Git Reset

### Git Restore
