# Commands

Commands in this section are in alphabetical order and will use `<>` to wrap sections of code that you should replace and `[]` to denote optional segments.

[Click here for in-dept command documentation](https://git-scm.com/docs/git#_git_commands), but the minimal set of commands below has been enough for me over the past 8 years.

## Git Add

`git add`.

## Git Clone

[Git Clone Documentation](https://git-scm.com/docs/git-clone).

Used to clone/copy/download an existing codebase from a server hosting a Git repository.

`git clone <repository url> [<directory name>]`.
- `<repository url>` where the git repository is stored.
- `[<directory name>]` (optional) to place the cloned repository into.
    - **Note**: Defaults to `<repository name>` if not provided.

## Git Init

[Git Init Documentation](https://git-scm.com/docs/git-init).

Used to turn a local directory into a Git repository.

> [!WARNING]
> This turns the current directory into a repository. If you want a subdirectory, then create it, move into it, and run the command there.

`git init`.

## Git Push

`git push [--force]`.
- `--force` Pushes

## Git Status

`git status`.
