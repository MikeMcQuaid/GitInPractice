# Introduction to local Git
With the basic concepts explained provide a practical walkthrough to how to get Git installed on their machine and get some Git hosting on the internet. Suggest some large Git projects to examine if curious and to indicate that Git is widely used. Point out other sources of help beyond this book.

## Why do programmers use Git?
## Installation
## Creating a repository

### Commands
`git init $REPOSITORY_DIRECTORY`

### Walkthrough
Starting with a new local repository is good for learning and testing purposes before dealing with existing repositories stored in other locations. When using an existing remote Git repository typically `git clone` is used instead of `git init`.

To create a new local Git repository in a new subdirectory named "git-testing":

1. Run `git init git-testing`
2. A new local Git repository has been created in a new subdirectory named "git-testing".

### Explanation
Initializing a Git repository is the first thing that needs to be done before any files can be added, commits made or pushed elsewhere. When `git init` is run it creates a named directory (if passed; otherwise uses the current directory). Under this directory a subdirectory named `.git` is created with various files and subdirectories under it:

```
git-testing/.git/config
git-testing/.git/description
git-testing/.git/HEAD
git-testing/.git/hooks/applypatch-msg.sample
git-testing/.git/hooks/commit-msg.sample
git-testing/.git/hooks/post-update.sample
git-testing/.git/hooks/pre-applypatch.sample
git-testing/.git/hooks/pre-commit.sample
git-testing/.git/hooks/pre-push.sample
git-testing/.git/hooks/pre-rebase.sample
git-testing/.git/hooks/prepare-commit-msg.sample
git-testing/.git/hooks/update.sample
git-testing/.git/info/exclude
git-testing/.git/objects/info
git-testing/.git/objects/pack
git-testing/.git/refs/heads
git-testing/.git/refs/tags
```

The purpose of some of these files may be obvious given prior experience of version control. Git has created here files for configuration, description (typically only used on repositories created for use on a server), various sample hooks (scripts run on defined events) and directories used for object storage and reference. There's a few other files that will be discussed later.

Without an advanced understanding of Git it is wise to never edit any of these files directly (although it is always safe to read them) as Git's commands may read, edit and write these files through interaction with the repository.

## Committing
### Add a file to be committed

#### Commands
`git add $FILE`

#### Walkthrough
![Git workflow](diagrams/workflow.png)

Git's index is a staging area used to build up new commits. Rather than requiring all changes in the working tree make up the next commit Git allows files (and even lines within files) to be added incrementally to the index.

Git does not add anything to the index without user instruction. As a result, the first thing we have to do with a file we want to include in a Git repository is add it to the index.

To add an existing file 'README.md' to the index:

1. Change directory to the Git repository (e.g. `cd ~/git-testing/`)
2. Ensure the file 'README.md' is in the current directory.
2. Run `git add README.md`
3. The file 'README.md' has been added to the index.

#### Explanation
When a file is added to the index a file named `.git/index` is created (if it does not already exist). The added file contents and metadata are then added to the index file. Two things have been signaled to Git here: the intent for Git to track the contents of the file as it changes (this is not done without an explicit `git add`) and the contents of the file at the time `git add` was run should be added to the index, ready to create the next commit.

Note that as the file is changed the contents of the commit will not be updated to reflect these changes without another `git add`. This may appear somewhat user hostile; later in the book this approach of incrementally and explicitly constructing new commits will be used to create a more readable version control history.
## History
## Diffs
