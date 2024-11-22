# Commands

Commands in this section are in alphabetical order and will use `<>` to wrap sections of code that you should replace and `[]` to denote optional segments.

[Click here for in-dept command documentation](https://git-scm.com/docs/git#_git_commands), but the minimal set of commands below has been enough for me over the past 8 years.

## Essential Commands

### Git Add

### Git Branch

[Git Branch Documentation](https://git-scm.com/docs/git-branch).

Used to display the list of local or remote (see `--remote`) branches.

`git branch [--remote]`
- `[--remote]` (`-r`) displays branches on all remote repositories that your local repository is connected to.
    - **Note**: This list is based on the last time your local repository got information from the remote repository. If you want an updated list, use [fetch](#git-fetch) or [pull](#git-pull) before running this command.

### Git Cherry Pick

### Git Clone

[Git Clone Documentation](https://git-scm.com/docs/git-clone).

Used to clone/copy/download an existing codebase from a server hosting a Git repository.

`git clone <repository url> [<directory name>]`.
- `<repository url>` where the git repository is stored.
- `[<directory name>]` (optional) to place the cloned repository into.
    - **Note**: Defaults to `<repository name>` if not provided.

### Git Commit

### Git Diff

### Git Fetch

[Git Fetch Documentation](https://git-scm.com/docs/git-fetch).

Updates its information (branches, commits, etc.) of the remote repository your local repository is connected to.

`git fetch [--prune]`
- `[--prune]` (`-p`) In addition to getting missing information it also removes local information (branches, commits, etc.) about items removed from the remote repository.
    - **Note**: I always want my `git fetch` to prune deleted information, so I used `git config fetch.prune true` to make that happen without needing to type `-p` every time.

### Git Init

[Git Init Documentation](https://git-scm.com/docs/git-init).

Used to turn a local directory into a Git repository.

> [!WARNING]
> This turns the current directory into a repository. If you want a subdirectory, then create it, move into it, and run the command there.

`git init`.

### Git Log

### Git Pull

### Git Push

### Git Rebase

### Git Revert

### Git Stash

### Git Status

### Git Switch

## Extra Commands

### Git Checkout

This command had many different uses depending on its context. I recommend using the below alternatives that specialize in specific
- Use [git switch](#git-switch) to change branches.
- TODO: What else was added to replace this?

### Git Move

### Git Remove

### Git Reset

### Git Restore
