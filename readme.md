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


## Add new modules

1. Update repos
  ```
  git submodule update --recursive --remote
  ```
2. Create new remote repo or use existing with one commit at least
3. Import the repo
  ```
  git submodule add <url>
  # EXAMPLES:
  #git submodule add https://github.com/theprotos/lab-jenkins.git 
  #git submodule add https://github.com/theprotos/lab-springboot.git
  #git submodule add https://github.com/theprotos/lab-buildtools.git
  #git submodule add https://github.com/theprotos/lab-cloud.git
  
  # Check if it appeared .gitmodules file
  # Check file .git/modules/<module-name>/config
```
4. Select branch from the repo
  ```
  cd <module-directory>
  git checkout -b <branch-name> #newone
  git fetch
  git checkout <existing_branch>
  ```

5. Changes highlight (various colours) in Intellij Idea  
  - Option A. Settings: [File] -> [Settings] -> [Version Control] > [Directory Mapping] > [+ Add] 
    - sub-repository folder
    - VCS=git
  - Option B. modify file: `.idea/vcs.xml`, change `<sub-module-name>`
    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <project version="4">
      <component name="VcsDirectoryMappings">
        <mapping directory="" vcs="Git" />
        <mapping directory="$PROJECT_DIR$/<sub-module-name>" vcs="Git" />
      </component>
    </project>
    ```

## Remove modules

```
git submodule deinit -f lab-maven
git rm -f lab-maven
git commit -m "Removed submodule"
rm -r -force .git/modules/lab-maven
```

## Mics

Setup python venv
  ```
  python -m venv lab.venv
  .\lab.venv\Scripts\Activate.ps1
  
  ```
