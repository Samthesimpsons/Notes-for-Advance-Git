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
```

To commit locally

```bash
git commit -m "Added index.html" -m "Some Description"
```

Now to push:

1. To push to an empty remote repository, after add and commit

    ```bash
    git remote add origin https://github.com/Samthesimpsons/git-demo.git
    git branch -M main
    ```
2. 