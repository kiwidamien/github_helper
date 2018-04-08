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

