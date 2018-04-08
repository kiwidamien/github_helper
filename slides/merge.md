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

