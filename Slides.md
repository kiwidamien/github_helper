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

## Commiting and pushing to a repository

### Pushing a particular file to a github repo

```
git add ${file}
git status # check only ${file} is staging
git commit -m "Message about why you made the change"
git push
```

~~~

### Push everything to a github repo

```
git add -A
git commit -m "Message about why you made the change"
```

OR

```
git commit -am "commit message" # only commits recently changed files
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

### Moving changes to a new branch

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




