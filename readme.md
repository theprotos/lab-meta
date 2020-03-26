# lab-meta

Git **mono repo** concept powered by `git submodule`, includes sandboxes for:

- [cassandra](lab-cassandra/readme.md)
- [ELK stack](lab-elk/readme.md)
- [jenkins](lab-jenkins/readme.md)
- [node](lab-node/readme.md)
- [react](lab-react/readme.md)
- [packer](lab-packer/readme.md)


## Git how to

### git submodule

- add
```
git submodule add https://github.com/theprotos/lab-jenkins.git
```

- remove
```
git submodule deinit -f ci/lab-jenkins
git rm -f ci/lab-jenkins
git commit -m "Removed submodule "
rm -r -force .git/modules/ci/lab-jenkins
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
