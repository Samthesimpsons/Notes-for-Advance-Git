# Git Cheatsheet

**Tutorials**

- Basics: https://www.youtube.com/watch?v=RGOj5yH7evk
- Basics/Intermediate: https://www.youtube.com/watch?v=Uszj_k0DGsg&t=411s
- Advanced:

## Basics

```bash
# To view hidden files too in directory
ls -la

# To init a local git repo
git init

# To see commit status
git status

# . period is to track all files
git add .

# Or specify the files e.g. index.html
git add index.html

# To see all branches (curr branch we will tagged by *)
git branch

# To rename the current branch e.g. to main
git branch -M main

# To create a new branch
git checkout -b feature_branch

# To switch branch (e.g. to main)
git checkout main

# To commit locally
git commit -m "Added index.html" -m "Some Description"

# To view all remotes
git remote -v
```

## Git Pushing

1. To push to an empty remote repository, after adds and commits

   Note that `origin` is the standard naming convention of the remote repository ID we are linking to. We can even add multiple remotes.

   ```bash
   # Adding the remote repository with an ID called origin
   git remote add origin https://github.com/Samthesimpsons/git-demo.git

   # Rename the current default branch name of master to main
   git branch -M main

   # Push to remote repository the local main branch
   # -u sets upstream, such that in the future we will push to the origin main just by saying git push
   # The remote repository branch name will be called main too
   git push -u origin main
   ```

2. If we cloned from a remote repository and want to commit from our local machine for the first time, after adds and commits

   ```bash
   # Since we cloned from the remote repository, the remote with the default naming convention of origin is setup
   # Hence all we need to do is just set the upstream for easier future pushes from main to origin/main
   # The local repository branch name will be called main since the remote repository branch we cloned from is called main too
   git push -u origin main
   ```

## Feature Branching

If we created a new feature branch and edited files on, add and commit there. Now if we switch back to main branch, the changes are not there.

If we are done with the feature branch

```bash
# Assuming feature branch name is feature_branch
# Note the -u to set a new upstream
git push -u origin feature_branch

# After pull request, merge and deleted on remote repository. Time to update local main
git checkout main
git pull

# Then next to delete the local feature branch
git branch -D feature_branch
```

## Git Merge Conflicts

As changes are made to main by other developers, we do not want to be behind too much. So we want to keep our local main up to date, and then also use merge to keep our feature_branch up to date. Yet, there might be merge conflicts between your local feature branch and the updated local main with the other developers edits.

```bash
# Updating our main branch
git checkout main
git pull

git checkout feature_branch
# Shortcut if the file is the only modified
# And am inside feature_branch to commit our changes inside the feature branch
git commit -am "update index.html"
git merge main

# However there will be conflicts which will be shown in the file itself
# <<< HEAD (crrrent branch)
# ...
# =======
# ...
# >>> main (branch we are merging into)
# So make the edits and then commit them
git commit -am "Settled merge conflicts"
```

So now the local main branch should be up to date with the remote one, and our local feature branch is updated with the changes from the local updated main branch too, plus our edits in the merge conflict.

Sometimes we can undo it and start fresh instead of solving the merge conflict

```bash
#...
git merge main

# Now after the conflict
git merge --abort
```

## Git Undoing

1. To undo stages (e.g. we added index.html)

   ```bash
   git reset index.html
   ```

2. What if we want to unstage the changes from the most recent commit instead

   ```bash
   # HEAD is the current commit, 1 means to reset back to 1 commit before the HEAD
   git reset HEAD~1
   ```

3. What if we want to unstage the changes from a commit further back instead.

   ```bash
   # To see all the commits
   git log
   # Can use hash key instead of the HEAD~INDEX
   git reset <HASH KEY>
   ```

4. BUT our changes to index.html till now is still here, the above steps simple unstage any commits to index.html (aka not saved to git). If we want to not only unstage the changes, but completely remove the changes

   ```bash
   git reset --hard <HASH KEY>
   ```

## Git Perfect Commit and Branching

Using patch, git goes through each chunk of change for us to choose (Y for Yes, N for No, etc.)

```bash
git add -p index.html
```

The perfect commit message:

1. Subject: Concise summary
2. Body: More details (AS-IS)

_Note using git commit, after the first line, the second line after the newline is the body_

For branching understand the business what they are using, etc GitFlow, GithubFlow

## Git Forking

Create a fork is our own copy of the original repository and allows pull request to the main open repository for the main contributor to review.

## Git Rebase

Do not use Rebase on commits that are already pushed to remote repository. Use it for cleaning up local commit history. 

https://www.atlassian.com/git/tutorials/merging-vs-rebasing

