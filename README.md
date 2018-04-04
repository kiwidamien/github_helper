# Github helper

Variables:
* ${repositoryDirectory}
* ${repositoryName}
* ${username}
* ${existing_branch_name}

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

## Commiting and pushing to a repository

### Pushing a particular file to a github repo

```
git add ${file}
git status # check only ${file} is staging
git commit -m "Message about why you made the change"
git push
```

### Push everything to a github repo

```
git add -A
git commit -m "Message about why you made the change"
```

OR

```
git commit -am "commit message" # only commits recently changed files
```

## Branches

### What branch am I on?

```
git branch
```

### How do I make a new branch?
To make a new branch (but stay on the same branch)
```
git branch new_branch_name
```

To make a new branch, and switch to it at the same time:
```
git checkout -b new_branch_name
```

### How do I switch branches?

If there are no changes to your current branch:
```
git checkout ${existing_branch_name}
```

If there are existing changes, and you want to  
