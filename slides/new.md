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

