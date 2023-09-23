# git-watch

Get a live view of a Git revision tree in the terminal.

Works on:

  * Windows (in Git Bash)
  * Linux

## Usage

There are two shell scripts in the `scripts` folder. Use them as follows (in a Git repository):

```
$ watch_git_tree_changes git_graph_crop
```

This displays a Git revision tree that gets updated whenever there are changes in the revision history.

## How does it work?

`watch_git_tree_changes some_command`

  * Runs `some_command` whenever:
      - there are changes in the Git revision history, or
      - the size of the terminal changes.
  * Change detection happens every second and is done by looking at the timestamps of the references in the `.git` folder. This process is reasonably fast, unless the repository contains a large set of references.

`git_graph_crop`

  * Runs `git log --graph --all --oneline --decorate --color` and crops the output to fit in the current terminal window.

When combining the two commands, we also get responsitivity with respect to changes to the terminal size. `watch_git_tree_changes` reacts to changes to the terminal dimensions, and `git_graph_crop` adapts its output to always fit.
