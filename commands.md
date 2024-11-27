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
> For commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.
>
> For commands that accept commit hash(es) (or [HEAD](./terminology.md#head)) you can use `<commit hash>~<number>` to go back a `<number>` of commits from `<commit hash>` or the shorthand `<commit hash>~` to go back one.

> [!NOTE]
> Commands in this section are in alphabetical order.

## Essential Commands

### Git Add

[Official Git Add Documentation](https://git-scm.com/docs/git-add).

Moves all [untracked](./terminology.md#untracked-change) & [unstaged](./terminology.md#unstaged-change) changes in added [untracked](./terminology.md#untracked) & [modified](./terminology.md#modified) files to the list of [staged](./terminology.md#staged-change) changes in preparation for the next [commit command](#git-commit).

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

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

### Git Diff

[Official Git Diff Documentation](https://git-scm.com/docs/git-diff).

Used to display changed lines in [modified](./terminology.md#modified) (use `--staged` for [staged](./terminology.md#staged)) files.

> [!TIP]
> For Git commands that accept file(s), you can specify them with spaces between them `file1.txt temp/file2.txt`, with wildcards `**/*.txt`, or add full directories `temp/`.

```bash
git diff [<path to file(s)>]
```
- `[<path to file(s)>]` you wish diff (default: diff all files).
- `[--staged]` display [staged](./terminology.md#staged) changes instead of [modified](./terminology.md#modified) changes.
    - **Alias(es)** `--cached`.

### Git Fetch

[Official Git Fetch Documentation](https://git-scm.com/docs/git-fetch).

Updates its information (branches, commits, etc.) of the remote repository your local repository is connected to.

```bash
git fetch
```
- `[--prune]` In addition to getting missing information it also removes local information (branches, commits, etc.) about items removed from the remote repository.
    - **Alias(es)** `-p`.
    - **Note**: I always want my `git fetch` to prune deleted information, so I used `git config fetch.prune true` to make that happen without needing to type `-p` every time.

### Git Init

[Official Git Init Documentation](https://git-scm.com/docs/git-init).

Used to turn a local directory into a Git repository.

> [!WARNING]
> This turns the current directory into a repository. If you want a subdirectory, then create it, move into it, and run the command there.

```bash
git init
```

### Git Log

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

### Git Checkout

This command had many different uses depending on its context. I recommend using the below alternatives that specialize in specific
- Use the [switch command](#git-switch) to change branches.
- TODO: What else was added to replace this?

### Git Move

### Git Remove

### Git Reset

### Git Restore
