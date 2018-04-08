## Undoing
<!-- .slide: id="undo" -->
* How to [unstage a file](#/undo-staging), so the file won't be in the commit.
* How to [revert changes to last commit](#/undo-to-most-recent-commit)
* How to [revert changes to arbitrary commit](#/undo-to-arbitrary-commit)

~~~
### Unstaging a file
<!-- .slide: id="undo-staging" -->

`git status` tells us the that 3 files are ready for staging:

```
On branch my_branch
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

  modified:   contributing.md
              something_else.txt
              analysis.py
```
If we want to commit everything except `contributing.md`, we first need to *unstage* `contributing.md`.
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


