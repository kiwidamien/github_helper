## Branches
<!-- .slide: id="branch-overview" -->

* Find [branch you are on](#/branch-get-current) with `git branch` 
* [Make a new branch](#/branch-new-branch)
* [Switch branches](#/branch-switch-branch)

~~~
### What branch am I on?
<!-- .slide: id="branch-get-current" -->

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

If there are changes to your current branch, you should [commit](#/push-commit) them first. Git won't allow you to switch with tracked files that are not committed. 
