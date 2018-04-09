## Normal flow
<!-- .slide: id="normal" -->

1. Update repo
2. Make a branch and switch to it
3. Do some work
4. Stage and commit work
5. Merge branch back to master
6. Delete the working branch.

~~~

### First time setup

Create the repo:
```bash
mkdir ${repositoryDirectory}
cd ${repositoryDirectory}
echo "# ${repositoryName}" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/${username}/${repositoryName}.git
git push -u origin master
```

Now create a `feature_branch` that you will work on:
```bash
git checkout -b ${feature_branch}
```

~~~

### Update repo (beginning of day)

Suppose you are doing work on `feature_branch`.

To get the latest version of your repo, do
```bash
git checkout master # go to the master branch
git pull            # pull the most recent version from GH
git merge feature_branch  
``` 
The last line moves your work in `feature_branch` into your own branch.

Get ready to do more work by checking out `feature_branch` again:
```bash
git checkout feature_branch # no -b this time, branch exists!
```

~~~

### Make a branch and switch to it
<!-- .slide: id="normal-make-branch" -->

When starting a new feature, you probably want to isolate it on its own branch.

```bash
# creates a different "feature_branch" and puts you on it
git checkout -b different_feature_branch
```

Each person or feature should be on its own sensibly named branch.

~~~

### Commiting (throughout the day)

When you have fixed a small issue, **stage** and **commit** your changes:
```bash
# stage al changes
git add .
git commit -m "description of changes made"
```

You should commit if you it would be a sensible place to "start over". 

~~~

### Putting your work on GitHub (end of day)

The process of putting your work on GitHub is called *pushing*.

The following command will push the current commit:
```bash
git push
```

Important: This will *not* push all your files onto GitHub, it will only push a _commit_ onto GitHub. Use `git status` to check that all your changes have been committed.

~~~

### Finished

That is the normal GitHub workflow. 

Problems can occur, especially if there are mutiple people writing to the same file. Press "Escape" to view the layout of this presentation, and look for commands that solve commonly occuring problems.
