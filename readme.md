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


## Git how to add new modules

### git submodule (preferred, current repo)

Create remote repo before with one commit at least

- add
```
git submodule add <url>
# EXAMPLES:
#git submodule add https://github.com/theprotos/lab-jenkins.git 
#git submodule add https://github.com/theprotos/lab-springboot.git
#git submodule add https://github.com/theprotos/lab-buildtools.git
#git submodule add https://github.com/theprotos/lab-cloud.git

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

- Changes highlight in Intellij (idea)  
  - [Option A] Settings: [File] -> [Settings] -> [Version Control] > [Directory Mapping] > [+ Add] sub-repository, VCS=git
  - [Option B] modify file: .idea/vcs.xml

- remove
```
git submodule deinit -f lab-maven
git rm -f lab-maven
git commit -m "Removed submodule"
rm -r -force .git/modules/lab-maven
```

## Mics
### Setup python venv

```
python -m venv lab.venv
.\lab.venv\Scripts\Activate.ps1

```
