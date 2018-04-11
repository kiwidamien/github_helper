## Undoing
<!-- .slide: id="undo" -->
* How to [unstage a file](#/undo-staging-single), or [multiple files](#/undo-staging-mutiple) so the file won't be in the commit.
* How to [revert changes to a single file](#/undo-revert-file)
* How to [revert changes to last commit](#/undo-to-most-recent-commit)
* How to [revert changes to arbitrary commit](#/undo-to-arbitrary-commit)

~~~
### Unstaging a file
<!-- .slide: id="undo-staging-single" -->
Problem: The file `new_file.txt` is staged, but we don't want it in the next commit

Solution:
```
git reset HEAD new_file.txt
```

Note: 
`git status` will remind you of this command:
```
On branch my_branch
Changes to be committed:
  (use "git reset HEAD <file> ...." to unstage)
...
```

~~~
### Unstage all files
<!-- .slide: id="undo-staging-multiple" -->

Problem: We want to unstage all our files, so we can start choosing what to stage again 

Solution:
```
git reset
```

~~~

### Undo changes to a file since last commit
<!-- .slide: id="undo-revert-file" -->

Problem: We made changes to `new_file.txt`, but want to change only this file on our computer back to how it looked on the most recent commit

Solution:
```
git checkout -- new_file.txt
```

If you want to go back `n` commits, you can do
```
git checkout HEAD~n -- new_file.txt
```
instead

~~~

### Revert changes to last commit
<!-- .slide: id="undo-to-most-recent-commit" -->

Problem: We made changes, and messed everything up. We want to restore everything on our computer back to how it looked on the most recent commit.

**Warning:** The following solution throws away your work and replaces it. You cannot undo this command. Be really, really sure!

Solution:
```
git reset --hard
```

You can also go back `n` commits using
```
git reset --hard HEAD~n
```

