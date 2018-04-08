# Github helper

## Story mode: 
[git guide](http://rogerdudler.github.io/git-guide/)

Variables:
* ${repositoryDirectory}
* ${repositoryName}
* ${username}
* ${existing_branch_name}

---

## Normal flow

1. Get repo (done once)
2. Make a branch and switch to it
3. Do some work
4. Stage and commit work
5. Merge branch back to master
6. Delete the working branch.

---

## Making a new repository
<!-- .slide: id="new-repo" -->

```
mkdir ${repositoryDirectory}
cd ${repositoryDirectory}
echo "# ${repositoryName}" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/${username}/${repositoryName}.git
git push -u origin master
```

---

## Putting work on Github
<!-- .slide: id="push-overview" -->
3 steps to move work from your machine onto GitHub:
1. [Stage](#/push-stage) your local work
1. [Commit](#/push-commit) files you staged
1. [Push](#/push-all) a local commit to GitHub

A minimal example to add file `${file}`
```
git add ${file}
git commit -m "Message about why you made the change"
git push
```
To save all changes, see [this slide](#/push-all).

Details about each step below.

~~~ 

### Stage work
<!-- .slide: id="push-stage" -->
<small>
Git allows you to group and upload the files that are ready, while still keeping changes for things that you are still working on.
</small>

* Staged files are ready to join the next commit.
* They are not commited until you [commit](#/push-commit) them

To stage a file, run
```bash
git add ${file}
```

Now you are ready to [`commit`](#/push-commit) the changes.
<small> 
* Use `git status` to see what is staged and what isn't
* Use `git commit -m "message"` to commit everything staged
* See [unstaging](#unstaging-a-file) to unstage a file.

</small>

~~~

### Commit work
<!-- .slide: id="push-commit" -->

You commit everything that is staged together. You will log a message, and be able to rewind to a previous commit.

Running `git status` will tell you what is staged.

Running
```
git commit -m "Message"
```
will commit all staged files.


~~~

### Push current commit

If you have already [staged](#/push-stage) and [committed](#/push-commit) your work, you need to push it to github:
```
# Do this while on feature_branch
git push
```

#### Possible complication
If this is your first push of this branch, GitHub will need you to it which branch you are pushing to. It tells you the command to run:
```
git t push --set-upstream origin feature_branch
```  

~~~

### Push all changes
<!-- .slide: id="push-all" -->

```bash
git add -A
git commit -m "Message about why you made the change"
git push
```

OR

```bash
# do in two lines (misses untracked files)
git commit -am "commit message" 
git push
```

---

## Branches
<!-- .slide: id="branch-overview" -->

### What branch am I on?

This command lists all branches, and places an asterisk by the branch you are on

```bash
git branch
```

Sample output:
```bash
* feature1
  feature2
  gh-pages
  master
```
~~~

### How do I make a new branch?
<!-- .slide: id="branch-new-branch" -->

To make a new branch (but stay on the same branch)
```
git branch new_branch_name
```

To make a new branch, and switch to it at the same time:
```
git checkout -b new_branch_name
```

~~~

### How do I switch branches?
<!-- .slide: id="branch-switch-branch" -->

If there are no changes to your current branch:
```
git checkout ${existing_branch_name}
```

If there are existing changes, and you want to save first, use
```
git add -A
git commit -m "commit message"
git push
git checkout ${existing_branch_name}
```

If there are changes to your current branch, you should [commit]() them first, or 

---

## Merging
<!-- .slide: id="merge-overview" -->

To merge your work from `feature_branch` back into `master`, we first have to make sure `feature_branch` is committed:
```bash
git branch feature_branch # make sure we are on feature branch
git add .
git commit -m "Ready to merge with master"
```

With this out of the way, we are ready to merge (press down)

~~~

### Merging into master
<!-- .slide: id="merge-basic" -->

To merge your changes in `feature_branch` into `master`: 
```bash
git checkout master
git pull # gets most recent master 
git merge feature_branch # does actual merge
```

If there are no merge conflicts, this completes the merge!

If git cannot figure out how to merge the files, you will need to resolve the [merge conflict](#/merge-conflict-overview) (press down)

~~~

### Merge conflict overview
<!-- .slide: id="merge-conflict-overview" -->

If you do have merge conflicts, the most common options for resolving them are:
* [Keep theirs](#/merge-conflict-keep-theirs): When there are competing merges, keep the version currently on `master`.
* [Keep ours](#/merge-conflict-keep-ours): When there are competing merges, keep the version current on `feature_branch`.
* [Pick'n'choose](#/merge-conflict-general): Resolve the merge conflicts manually.

~~~

### Merge conflict: keep theirs
<!-- .slide: id="merge-conflict-keep-theirs" -->

You tried to merge  
```bash
git checkout master
git pull
git merge feature_branch
```
and got a merge conflict. We want to merge our branch, but if there is a conflict use the *master* branch:
```bash
# still on master from above
git merge --abort # throw away broken merge
git merge -X theirs feature_branch
``` 

~~~

### Merge conflict: keep ours
<!-- .slide: id="merge-conflict-keep-ours" -->

You tried to merge
```bash
git checkout master
git pull
git merge feature_branch
```
and got a merge conflict. We want to merge our branch, but if there is a conflict use the *feature_branch*:
```bash
# still on master from above
git merge --abort # throw away broken merge
git merge -X ours feature_branch
``` 

~~~

### Merge conflict: general
<!-- .slide: id="merge-conflict-general" -->

---

## Undoing
<!-- .slide: id="undo" -->
~~~
### Unstaging a file
<!-- .slide: id="undo-staging" -->

Suppose that `contributing.md` has been modified and added, so that `git status` returns
```
On branch my_branch
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

  modified:   contributing.md
              something_else.txt
              analysis.py
```
then a commit command would stage 3 files.

If we want to commit everything except `contributing.md`, we first need to *unstage* `contributing.md`. We would run
```
git reset HEAD contributing.md
``` 

After this, `git status` yields
```
On branch my_branch
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

  modified    something_else.txt
              analysis.py

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in the working directory)

  modified:   contributing.md
```

The file `contributing.md` is still modified, but it is now _unstaged_.

~~~

### Throw away all local changes, and restore my local copy back to most recent commit
<!-- .slide: id="undo-to-most-recent-commit" -->

Suppose you have modified `contributing.md`, and it is unstaged:
```
On branch my_branch
  .....
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in the working directory)

  modified:   contributing.md
```
To revert the file, run
```
git checkout -- contributing.md
```

If your file has been staged, you will want to follow the instructions for [unstaging a file]() first, then follow these steps. 

~~~

### Throw away all local changes, and restore my local copy back to a particular commit
<!-- .slide: id="undo-to-given-commit" --> 

Go to [merging](#/merging)


