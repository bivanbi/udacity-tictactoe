# Git Flow and Semantic Versioning


## Git: a Code Versioning Tool

Code Versioning is crucial to track changes in code, add reasoning and to easily roll back if something
goes wrong. Git is such a tool. Not the only one, but certainly the most popular and well known,
and for a reason. Git has many features such as branching, multiple merging strategies, tagging and so on.
Besides that, Git is great for teamwork.

## Git as a Network Service
Git is also capable of doing all the aforementioned stuff over *networks*, so there can be a central
repository from developers can *pull* code and *push* their changes back.
This Git server can be self-hosted (on-premise) or one could choose from several cloud
providers, such as [GitHub](https://github.com), [Atlassian Bitbucket](https://bitbucket.net),
[Microsoft Azure](https://azure.microsoft.com/en-us/services/devops/) just to mention a few.

Even if you are an hobbyist working on your own projects for your own enjoyment, you might consider
using a Git server (on-prem or cloud), for the following benefits:

* have a backup copy of your work you can update quickly with your latest changes
* if you work on multiple devices, you can do so with the help of a Git server

Cloud providers have some more benefits:
* you can easily share your code or collaborate with others
* Cloud providers usually offer other features such as issue management, or even automated
  build services to create your software packages to be released to the public.  

## Branching
Team members can branch off of a common code base, work on their features in their *topic branches* and
when ready, merge their changes back in to the common code base. Merging can be initiated with
a *pull request*, where the developer proposes a branch to be merged into another, explains the proposed
changes. Then those changes can be reviewed and approved, and then the actual merge carried out.

One can quickly change between branches and tags, which is great if you need to have a look
at de code base in different stages. This is invaluable when, for instance you are working on
a feature but find a bug in the released version of your code you need to quickly fix. You can
save your changes on your topic branch, go to your stable branch, branch off of it into a bugfix
branch, fix your code, and merge those changes into your stable branch *and* your topic branch.
Then you can continue to work on your new feautere, which already has that bugfix applied.

### Branching Model
[A successful branching model](https://nvie.com/posts/a-successful-git-branching-model/) is a good
read into developing your habits.

## Merging
Merging is the procedure where you apply changes in one branch to another. A branch can be merged in
to multiple braches. For instance, a bugfix branch will usually be marged into ```master``` and 
```develop``` branch too.

Atlassian has a good [documentation on merging](https://www.atlassian.com/git/tutorials/using-branches/git-merge)
and [merge strategies](https://www.atlassian.com/git/tutorials/using-branches/merge-strategy).


## Tagging and Semantic Versioning

### What is a tag
Tag represents a point in the history of your code. You can reproduce the given state of the code by
checking out a tag. You can think of a tag as a label applied to a specific commit.


### When to use tags

Tags are certainly to be used for marking releases, pre-releases and such.

When you feel you reached a milestone in your project, you might want to *release* it.
Those *releases* are usually marked in your stable (main, master) branch with a tag.
Also when you fix a bug in your code and want to indicate that there is a fixed version
of your program, you should tag it.


### How to name tags
The name of a tag is arbitrary, free text. Common naming convention examples:

* release candidate: ```v1.0.2rc1```.
* release: ```v1.0.2```.


### Semantic Versioning
Given a version number MAJOR.MINOR.PATCH, increment the:

MAJOR version when you make incompatible API changes,
MINOR version when you add functionality in a backwards compatible manner, and
PATCH version when you make backwards compatible bug fixes.
Additional labels for pre-release and build metadata are available as
extensions to the MAJOR.MINOR.PATCH format."

See [Semantic Versioning](https://semver.org/) for more details.


