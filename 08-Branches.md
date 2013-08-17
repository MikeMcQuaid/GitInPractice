# Branches
Dealing with local and remote branches and tags. Describe how branching is useful, how to create and checkout local and remote branches and tags.

Relies on Git's commit and history concepts from previous chapters.

## Why is branching useful?
(Difficulty: 5)

## Restore a file to its last committed state
(Difficulty: 3)

## Create a new local branch from the current branch
(Difficulty: 5)

### Commands
`git branch $BRANCH`

### Walkthrough
![Before `git branch testing`](screenshots/git-branch-before.png)

To create a new local branch "testing" from your current branch:

1. Run `git branch testing`
2. You have now created the "testing" branch.

![After `git branch testing`](screenshots/git-branch-after.png)

Branches have some restrictions to their naming. For example, branches cannot have two consecutive dots (..) anywhere in their name so "testing..dot" would be an invalid name and `git branch` will refuse to create it.

`git branch` merely creates a local branch, it does not change to it. For that we will use `git checkout`.

### Explanation
![Branch pointers](diagrams/branches.png)

Creating a branch in Git is a very quick and efficient process (particularly compared to some other version control systems). When Git creates a branch it is not duplicating and data but simply adding another pointer for the branch. Branch pointers point to the "top" (i.e. most recent) commit in their current branch so as you make more commits the branch pointer will follow your these.

## Checkout a local branch
(Difficulty: 4)

### Commands
`git checkout $BRANCH`

### Walkthrough
To change from your current "master" branch to a local branch "testing":

1. Run `git status` to ensure you have no modified and uncommitted files (as Git will refuse to check out in that case without the `--force` parameter).
2. Run `git checkout testing`.
3. You are now on the "testing" branch.

![After `git checkout testing`](screenshots/git-checkout-after.png)

### Explanation
`git checkout` has slightly different naming to what you may expect. In Subversion, for example, checkout is used to "check out" a repository from a remote server (similarly to how we would use `git clone`). In Git it appears to be changing branches. What's going on here?

![Git workflow](diagrams/workflow.png)

Git clones the entire history of a repository and stores that on your local machine. As a result of this, what is happening here is not too dissimilar to Subversion; you are checking out the contents of a repository into the working tree (i.e. everything that isn't under a `.git` directory). In this case we're requesting the checkout of a particular branch so the state of that branch is checked out into the working tree. Additionally, after that has happened the HEAD pointer is updated to point to this branch.

![HEAD pointer](diagrams/HEAD.png)

The HEAD pointer is used to track which Git revision you have currently checked out. After a successful checkout it is moved from pointing to your previous state (i.e. here your previous branch) to the branch `$BRANCH`. If you moved
back to the previous branch then HEAD would be updated to point to that instead

## Checkout a remote branch
(Difficulty: 6)

### Commands
`git checkout $REMOTE/$BRANCH`

### Walkthrough
To change from your current "master" branch to a branch "testing" on the remote "origin":

1. Run `git branch testing origin/testing` to create the local "testing" branch tracking the branch "testing" on the remote "origin".
2. Run `git status` to ensure you have no modified and uncommitted files (as Git will refuse to check out in that case without the `--force` parameter).
3. Run `git checkout testing`.
3. You are now on the "testing" branch tracking the remote "origin".

![After `git checkout testing`](screenshots/git-checkout-remote-after.png)

### Explanation
Remote branches are branches which exist on a "remote" (that is another Git repository Git knows about; typically on a remote machine). They are downloaded with `git fetch` but do not have any connection with local branches unless manually specified. You can still view the differences between a local branch and a remote branch or history of a remote branch without creating a local branch but if you wish to add commits to it (and push them) then a local branch must be created.

When you specify a local branch should default to pushing to and pulling from a remote branch then the local branch is said to be "tracking" the remote branch.

## Create a new branch from another local or remote branch
(Difficulty: 7)

## List local branches
(Difficulty: 4)

## List all local and remote branches
(Difficulty: 6)

## List what branches contain a commit
(Difficulty: 10)

## Create a tag
(Difficulty: 5)

## Describe the current state of a commit based on previous tags
(Difficulty: 6)
