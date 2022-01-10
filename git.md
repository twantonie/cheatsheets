[Drop commit but keep changes](https://stackoverflow.com/questions/15772134/can-i-delete-a-git-commit-but-keep-the-changes):

    git reset HEAD^


Remove local branches that have been removed upstream

    git fetch --prune

Delete upstream branch

    git push -d <remote_name> <branch_name>

Delete local branch

    git branch -D <branch_name>

Squash feature into master

    git checkout master
    git merge --squash feature
    git commit

Update date of a commit, useful after rebasing/amending multiple commits into one

    git commit --amend --date="$(date -R)"

Update commit author

    git commit --amend --author="Twan Spil <t.spil@chronoptics.com>" --no-edit

Generate patches

    git format-patch <branch>

Remove old branches

    git branch -vv | awk '/: gone]/{print $1}' | xargs git branch -d

Remove untracked files

    # List files
    git clean -n -d 
    # Remove files
    git clean -f
    # Remove directories
    git clean -fd

## Undo git rebase
There are two options here, you can either use reflog or ORIG_HEAD. ORIG_HEAD is created before a reset, rebase and merge so if you try to undo after any of those operations you have to use reflog. In reflog you go back to the first commit before the rebase started.

    git reflog
    git reset --hard HEAD@{5}

    git reset --hard ORIG_HEAD

    