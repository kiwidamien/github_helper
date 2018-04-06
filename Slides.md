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

3 steps moving work from your machine onto GitHub:
1. [Stage](#stage-work) your local work
1. [Commit](#commit-work) files you staged
1. [Push](#push) a local commit to GitHub

A minimal example to add file `${file}`
```
git add ${file}
git commit -m "Message about why you made the change"
git push
```
To save all changes, see [this slide](#push-all-changes).

For more details, look at the [staging](#stage-work), [committing](#commit-work), and [pushing](#push)

~~~ 

### Stage work

Git allows you to group and upload the files that are ready, while still keeping changes for things that you are still working on.

* Staged files are ready to join the next commit.
* They are not commited until you [commit](#commit-work) them

To stage a file, run
```
git add ${file}
```

Now you are ready to [`commit`](#commit-work) the changes.
 
* Use `git status` to see what is staged and what isn't
* Use `git commit -m "message"` to commit everything staged
* See [unstaging](#unstaging-a-file) to unstage a file.


~~~

### Commit work

You commit everything that is staged together. You will log a message, and be able to rewind to a previous commit.

Running `git status` will tell you what is staged.

Running
```
git commit -m "Message"
```
will commit all staged files.


~~~

### Push all changes

```
git add -A
git commit -m "Message about why you made the change"
git push
```

OR

```
# do in one line (misses untracked files)
git commit -am "commit message" 
git push
```

---

## Branches

### What branch am I on?

```
git branch
```

~~~

### How do I make a new branch?
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

_Merging_ is how you move your work on its own branch back into other branches.

Suppose you have been working on `feature_branch`, and you are ready to merge it with `master_branch` (i.e. you want to incorportate your changes back into master). Before starting with the actual merge, we have to commit everything in our `feature_branch`:
```
git branch feature_branch # make sure we are on feature branch
git add .
git commit -m "Ready to merge with master"
```

With this out of the way, we are ready to merge (press down)

~~~

### Merging into master

You want to merge your changes in `feature_branch` into `master`. 

```
git checkout master
git pull # gets most recent master 
git merge feature_branch # does actual merge
```

If there are no merge conflicts, this completes the merge!

If you do have merge conflicts, the most common options for resolving them are:
* [Keep theirs](#merge-conflict-keep-theirs): When there are competing merges, keep the version currently on `master`.
* [Keep ours](#merge-conflict-keep-ours): When there are competing merges, keep the version current on `feature_branch`.
* [Pick'n'choose](#merge-conflict-general): Resolve the merge conflicts manually.

~~~

### Merge conflict: keep theirs

You tried to merge  
```
git checkout master
git pull
git merge feature_branch
```
~~~

### Merge conflict: keep ours

~~~

### Merge conflict: general

---

## Undoing

### Unstaging a file

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

Go to [merging](#merging)




