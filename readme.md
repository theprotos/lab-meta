# lab-meta

Git **mono repo** concept powered by `git submodule`, includes sandboxes for:

- [cassandra](lab-cassandra/readme.md)
- [ELK stack](lab-elk/readme.md)
- [ethical](lab-ethical/readme.md)
- [jenkins](lab-jenkins/readme.md)
- [k8s](lab-k8s/readme.md)
- [node](lab-node/readme.md)
- [packer](lab-packer/readme.md)
- [react](lab-react/readme.md)
- [springboot](lab-springboot/readme.md)


## Git how to add modules


### git submodule (prefer)

Create remote repo before with one commit at least

- add
```
git submodule add https://github.com/theprotos/lab-jenkins.git 
git submodule add https://github.com/theprotos/lab-springboot.git
git submodule add https://github.com/theprotos/lab-buildtools.git
git submodule add https://github.com/theprotos/lab-cloud.git

# Check file .gitmodules file
# Check file .git/modules/<module-name>/config
```

- Select branch
```
cd <module-directory>
git checkout -b <branch-name> #newone
git fetch
git checkout <existing_branch>
```

- remove
```
git submodule deinit -f lab-maven
git rm -f lab-maven
git commit -m "Removed submodule"
rm -r -force .git/modules/lab-maven
```

### git subtree

- add
```
git remote add -f lab-cassandra https://github.com/theprotos/lab-cassandra.git
git merge -s ours --no-commit --allow-unrelated-histories lab-cassandra/master
git read-tree --prefix=database/lab-cassandra/ -u lab-cassandra/master
```

- push & pull

```
git subtree pull --prefix database/lab-cassandra https://github.com/theprotos/lab-cassandra.git master --squash
git subtree push --prefix database/lab-cassandra https://github.com/theprotos/lab-cassandra.git master

# Push troubleshhoting
git subtree split --prefix=database/lab-cassandra --onto=lab-cassandra/master
git push lab-cassandra 01234567:master
```
