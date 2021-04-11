# Set Up Git Repository

## Gitignore

Some files / directories need to be excluded from repository, as they are not part of the source of the Project.
These files are typically the built binaries, cache or temporary files or configuration that is only valid on
a given workstation.

We are utilizing IntelliJ's Git managing capabilities here, but all steps can be completed through command
line as well. Just make sure that IntelliJ creates its own ```.idea/gitignore``` file and if it does not,
add it manually. 


Add a file to your project root named ```.gitignore``` with the following content:
```
.gradle
build
```

![Create new file](../../resources/01/create-file-with-intellij.png "Create file with IntelliJ")

![.gitignore contents](../../resources/01/gitignore.png ".gitignore contents")





## Git init

### Init with IntelliJ


![Create Repository Menuitem](../../resources/01/vcs-operations.png "VCS Menu")

![Create Repository Menuitem](../../resources/01/create-repository.png "Create Git Repository")

![Create Repository Menuitem](../../resources/01/create-repository-select-root.png "Select Repository Folder")


### Check .idea/.gitignore

![.idea/.gitignore contents](../../resources/01/idea-gitignore.png ".idea/gitignore contents")



### Init via command line (git shell)
```
cd <path to project root>
git init
```

## Add Files to Repository

### With IntelliJ

![Enter Commit Menu](../../resources/01/commit.png "Enter Commit Menu")

![Select Files and set message](../../resources/01/commit-select-files-and-set-message.png "Select Files and set message")


When prompted, choose *Fix and Commit*

![Line Separator Warning](../../resources/01/commit-line-spearators-warning.png "Line Separator Warning")


Review code analysis warnings. You may ignore them for now and just click *Commit*. We will fix them later.

![Code Analysis Warning](../../resources/01/commit-code-analysis-warning.png "Code Analysis Warning")


### Via command line
```
git add --all
git commit -m "initial commit"
```

This initializes our repository with ```master``` (or ```main``` with newer Git) branch.

Check the status:
```
$ git status
On branch master
nothing to commit, working tree clean
```

## Set Up Develop Branch
### IntelliJ

Open *Git -> New branch...* menu, then:
![Create New Branch](../../resources/01/git-new-branch.png "Create New Branch")

Check current branch in the bottom-right corner of IntelliJ
![Check Current Branch](../../resources/01/git-branch-name-display.png "Check Current Branch")

### Command line
```
git checkout -b develop
```



## Set Up Feature / Bugfix Branch
While it seems too much overhead, it is worth setting up short-lived feature / bugfix / release branches
to better organize changes to source code.

The basic idea is that development is done on ```topic branches```. Topic branches in most cases branch off of
```develop```, and in most cases they are merged back into ```develop``` as well. 
Check out [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
for details.


Our first feature branch, for instance, could be ```task/code-cleanup```


