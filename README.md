# Git Cheatsheet


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

# To commit locally
git commit -m "Added index.html" -m "Some Description"

# To view all remotes
git remote -v
```

Now to push:

1. To push to an empty remote repository, after add and commit

    Note that ```origin``` is the standard naming convention of the remote repository ID we are linking to. We can even add multiple remotes.

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
2. If we cloned from a remote repository and want to commit from our local machine for the first time

    