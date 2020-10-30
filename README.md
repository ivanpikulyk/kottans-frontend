# Credits, this descriptions of commands taken from Udacity course <a href="https://www.udacity.com/course/version-control-with-git--ud123" rel="nofollow">Version Control with Git</a> and <a href="https://learngitbranching.js.org" rel="nofollow">learngitbranching.js.org</a> 


- Create an empty Git repository or reinitialize an existing one <br>
git init 
 
new-git-project <br>
.git <br>
├── branches <br> 
├── COMMIT_EDITMSG <br>
├── config <br>
├── description <br>
├── HEAD <br>
├── hooks <br>
│   ├── applypatch-msg.sample <br>
│   ├── commit-msg.sample <br>
│   ├── fsmonitor-watchman.sample <br>
│   ├── post-update.sample <br>
│   ├── pre-applypatch.sample <br>
│   ├── pre-commit.sample <br>
│   ├── pre-merge-commit.sample <br>
│   ├── prepare-commit-msg.sample <br>
│   ├── pre-push.sample <br>
│   ├── pre-rebase.sample <br>
│   ├── pre-receive.sample <br>
│   └── update.sample <br>
├── index <br>
├── info <br>
│   └── exclude <br>
├── logs <br>
│   ├── HEAD <br>
│   └── refs <br>
│       └── heads <br>
│           └── master <br>
├── objects - this directory will be stored all commits which I make <br>
│   ├── 03 <br>
│   │   └── 71c624d9e48a458e47af4b58265e53558059e5 <br>
│   ├── 21 <br>
│   │   └── cf2ad8af085eeba4074f1bfdde0859e4b5a27a <br>
│   ├── 23 <br>
│   │   └── d0346d5da86206ce06f42438ee3657bbfe0ef7 <br>
│   ├── 50 <br>
│   │   └── baa5e568df5577d90c22d6b7dd2250c09a4861 <br>
│   ├── 51 <br>
│   │   └── afa957071f56ff61b0542737b862f416ee7c75 <br>
│   ├── 53 <br>
│   │   └── a2754e67e533925d6baded5e3876617d8d0bc3 <br>
│   ├── a3 <br>
│   │   └── 3232ad235b9b00959c54e8c14fa8bf81ffee22 <br>
│   ├── b7 <br>
│   │   └── 3fde3a497eced12b98f5514129038ef54c95f0 <br>
│   ├── e6 <br>
│   │   └── 9de29bb2d1d6434b8b29ae775ad8c2e48c5391 <br>
│   ├── info <br>
│   └── pack <br>
└── refs - this directory holds pointers to commits (basically the "branches" and "tags") <br>
    ├── heads <br>
    │   └── master <br>
    └── tags <br>


- Clone a repository into a new directory
git clone url  <additional argument how this repository which I trying to clone will be named instead of original name>

- Show the working tree status
git status

git log

git log --oneline

git log --stat

git log -p

git log -p --stat

git log -p fdf5493

- git show command will show only one commit
git show

- However, git show can be combined with most of the other flags we've looked at:

git show -p --stat -w

- Tip from udacity git course: "I first used git log --oneline to find the SHA of the commit, then I used git log --stat with the SHA to find the right info."

- The git add command is used to move files from the Working Directory to the Staging Index.
git add <file1> <file2> … <fileN>

- adds all files, directories and everything inside of those directories

git add .

- Bypass The Editor With The -m Flag

git commit -m "Initial commit"

- git diff command can be used to see changes that have been made but haven't been committed, yet.
git diff

- this file to your project in the same directory that the hidden .git directory is located. All you have to do is list the names of files that you want Git to ignore (not track) and it will ignore them.

.gitignore

- run git log —oneline command to check briefly output with SHA and commit message
git log --oneline

- add an annotated tag
git tag -a v1.0 a87984

- delete tag
git tag -d v1.0

- list all branches in the repository
git branch

- create branch with name: "sidebar"
git branch sidebar

- switch to sidebar branch and then git log —oneline or git branch commands could help to check active branch if there is not any specific configuration in shell prompt to check it.

git checkout sidebar

- this command will create branch: "alt-sidebar-loc" and has it pointing at the commit with the SHA 42a69f
git branch alt-sidebar-loc 42a69f

- switch to another branch from sidebar and then it would be possible to delete sidebar branch with command which will force deletion, despite on commits with this branch

git branch -D sidebar

-Switch and Create Branch In One Command
git checkout -b richards-branch-for-awesome-changes

- show all branches
git log --oneline --graph --all

- combine git branches
git merge <name-of-branch-to-merge-in>

- NICE TIP: git diff in order to check what`s  going to be staged/committed!

- alter the most-recent commit 1) edit the file(s) 2) save the file(s) 3) stage the file(s) 4) run git commit --amend
git commit --amend

- reverse a previously made commit
git revert <SHA-of-commit-to-revert>

- before erasing something, it is a good idea to create a backup
git branch backup

- erase commit, --mixed flag is default flag and it will move changes to the working directory., --soft flag is used, the changes are moved to the Staging Index! --hard flag is used, the changes are thrown out! 

^ – indicates the parent commit (Moving upwards one commit at a time with ^)

~ – indicates the first parent commit (Moving upwards a number of times with ~<num>)

git reset <reference-to-commit>

git reset --mixed HEAD^

git checkout -- index.html

git merge backup

git reset --soft HEAD^

git reset --hard HEAD^

- Git does keep track of everything for about 30 days before it completely erases anything. To access this content, you'll need to use the git reflog command.

- That's right! HEAD~4 references the fourth parent commit of the current one and then the ^2 tells us that it's the second parent of the merge commit (the one that got merged in!).

- could help to reorder commits
git rebase -i HEAD~4

git cherry-pick <reference-to-commit>

git clone

git fetch

- downloading from remote repository

git fetch && git merge o/master == git pull

git pull --rebase

- uploading your changes to a specified remote and updating that remote to incorporate your new commits

- Important, firstly there is a need to check and set push.default
git push

- Creates a new branch named totallyNotMaster and sets it to track o/master
git checkout -b totallyNotMaster o/master ;git pull

- Another way to set remote tracking on a branch is to simply use the git branch -u option. Running below command will set the foo branch to track o/master

git branch -u o/master foo

- git push can optionally take arguments in the form of:

git push <remote> <place>

- Go to the branch named "master" in my repository, grab all the commits, and then go to the branch "master" on the remote named "origin". Place whatever commits are missing on that branch and then tell me when you're done.

git push origin master

- In order to specify both the source and the destination of <place>, simply join the two together with a colon:

git push origin <source>:<destination>

- Git will go to the foo branch on the remote, grab all the commits that aren't present locally, and then plop them down onto the o/foo branch locally.

git fetch origin foo

- Here is the only catch though -- <source> is now a place on the remote and <destination> is a local place to put those commits. It's the exact opposite of git push, and that makes sense since we are transferring data in the opposite direction

- Git abuses the <source> parameter in two weird ways. These two abuses come from the fact that you can technically specify "nothing" as a valid source for both git push and git fetch. The way you specify nothing is via an empty argument:

git push origin :side

git fetch origin :bugFix
