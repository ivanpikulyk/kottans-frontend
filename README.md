<details>
    <summary>0.Git Basics</summary>

# Credits, this descriptions of commands taken from Udacity course <a href="https://www.udacity.com/course/version-control-with-git--ud123" rel="nofollow">Version Control with Git</a> and <a href="https://learngitbranching.js.org" rel="nofollow">learngitbranching.js.org</a> 


- Create an empty Git repository or reinitialize an existing one <br>
<pre>git init </pre>
 
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


- Clone a repository into a new directory<br> 
git clone url  <additional argument how this repository which I trying to clone will be named instead of original name>

- Show the working tree status<br>
<pre>git status

git log

git log --oneline

git log --stat

git log -p

git log -p --stat

git log -p fdf5493</pre>

- git show command will show only one commit<br>
<pre>git show</pre>

- However, git show can be combined with most of the other flags we've looked at:<br>

<pre>git show -p --stat -w</pre>

- Tip from udacity git course: "I first used git log --oneline to find the SHA of the commit, then I used git log --stat with the SHA to find the right info."

- The git add command is used to move files from the Working Directory to the Staging Index.
<pre>git add <file1> <file2> … <fileN></pre>

- adds all files, directories and everything inside of those directories<br>

<pre>git add .</pre>

- Bypass The Editor With The -m Flag<br>

<pre>git commit -m "Initial commit"</pre>

- git diff command can be used to see changes that have been made but haven't been committed, yet.<br>
<pre>git diff</pre>

- this file to your project in the same directory that the hidden .git directory is located. All you have to do is list the names of files that you want Git to ignore (not track) and it will ignore them.<br>

<pre>.gitignore</pre>

- run git log —oneline command to check briefly output with SHA and commit message<br>
<pre>git log --oneline</pre>

- add an annotated tag<br>
<pre>git tag -a v1.0 a87984</pre>

- delete tag<br>
<pre>git tag -d v1.0</pre>

- list all branches in the repository<br>
<pre>git branch</pre>

- create branch with name: "sidebar"<br>
<pre>git branch sidebar</pre>

- switch to sidebar branch and then git log —oneline or git branch commands could help to check active branch if there is not any specific configuration in shell prompt to check it.<br>

<pre>git checkout sidebar</pre>

- this command will create branch: "alt-sidebar-loc" and has it pointing at the commit with the SHA 42a69f<br>
<pre>git branch alt-sidebar-loc 42a69f</pre>

- switch to another branch from sidebar and then it would be possible to delete sidebar branch with command which will force deletion, despite on commits with this branch<br>

<pre>git branch -D sidebar</pre>

- Switch and Create Branch In One Command<br>
<pre>git checkout -b richards-branch-for-awesome-changes</pre>

- show all branches<br>
<pre>git log --oneline --graph --all</pre>

- combine git branches<br>
<pre>git merge <name-of-branch-to-merge-in></pre>

- NICE TIP: git diff in order to check what is  going to be staged/committed!

- alter the most-recent commit 1) edit the file(s) 2) save the file(s) 3) stage the file(s) 4) run git commit --amend<br>
<pre>git commit --amend</pre>

- reverse a previously made commit<br>
<pre>git revert <SHA-of-commit-to-revert></pre>

- before erasing something, it is a good idea to create a backup<br>
<pre>git branch backup</pre>

- erase commit, --mixed flag is default flag and it will move changes to the working directory., --soft flag is used, the changes are moved to the Staging Index! --hard flag is used, the changes are thrown out! <br>

<pre>^ – indicates the parent commit (Moving upwards one commit at a time with ^)

~ – indicates the first parent commit (Moving upwards a number of times with ~<num>)

git reset <reference-to-commit>

git reset --mixed HEAD^

git checkout -- index.html

git merge backup

git reset --soft HEAD^

git reset --hard HEAD^</pre>

- Git does keep track of everything for about 30 days before it completely erases anything. To access this content, you'll need to use the git reflog command.

- That's right! HEAD~4 references the fourth parent commit of the current one and then the ^2 tells us that it's the second parent of the merge commit (the one that got merged in!).

- could help to reorder commits<br>
<pre>git rebase -i HEAD~4

git cherry-pick <reference-to-commit>

git clone

git fetch</pre>

- downloading from remote repository

<pre>git fetch && git merge o/master == git pull

git pull --rebase</pre>

- uploading your changes to a specified remote and updating that remote to incorporate your new commits

- Important, firstly there is a need to check and set push.default<br>
<pre>git push</pre>

- Creates a new branch named totallyNotMaster and sets it to track o/master<br>
<pre>git checkout -b totallyNotMaster o/master ;git pull</pre>

- Another way to set remote tracking on a branch is to simply use the git branch -u option. Running below command will set the foo branch to track o/master<br>

<pre>git branch -u o/master foo</pre>

- git push can optionally take arguments in the form of:<br>

<pre>git push <remote> <place></pre>

- Go to the branch named "master" in my repository, grab all the commits, and then go to the branch "master" on the remote named "origin". Place whatever commits are missing on that branch and then tell me when you're done.<br>

<pre>git push origin master</pre>

- In order to specify both the source and the destination of <place>, simply join the two together with a colon:<br>

<pre>git push origin <source>:<destination></pre>

- Git will go to the foo branch on the remote, grab all the commits that aren't present locally, and then plop them down onto the o/foo branch locally.<br>

<pre>git fetch origin foo</pre>

- Here is the only catch though -- <source> is now a place on the remote and <destination> is a local place to put those commits. It's the exact opposite of git push, and that makes sense since we are transferring data in the opposite direction

- Git abuses the <source> parameter in two weird ways. These two abuses come from the fact that you can technically specify "nothing" as a valid source for both git push and git fetch. The way you specify nothing is via an empty argument:<br>

<pre>git push origin :side

git fetch origin :bugFix</pre>
 
</details>
 <details>
    <summary>1.Linux CLI and Networking</summary>
  

## Linux CLI, and HTTP

<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/171bd2749c8824c4ab1f4750298dde72e4c979fc/task_linux_cli/photo_2020-10-31_23-04-12.jpg" alt="task_linux_cli_1" style="max-width:25%;">
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/171bd2749c8824c4ab1f4750298dde72e4c979fc/task_linux_cli/photo_2020-10-31_23-04-17.jpg" alt="task_linux_cli_2" style="max-width:25%;">
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/171bd2749c8824c4ab1f4750298dde72e4c979fc/task_linux_cli/photo_2020-10-31_23-04-20.jpg" alt="task_linux_cli_3" style="max-width:25%;">
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/171bd2749c8824c4ab1f4750298dde72e4c979fc/task_linux_cli/photo_2020-10-31_23-04-23.jpg" alt="task_linux_cli_4" style="max-width:25%;">
<hr>
1xx: Informational Messages<br>
2xx: Successful<br>
3xx: Redirection<br>
4xx: Client Error<br>
5xx: Server Error<br>
<hr>
openssl s_client -connect example.com:443<br>

TRACE / HTTP/1.1<br>
host: example.com<br>

<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/main/task_linux_cli/telnet_trace.PNG" alt="telnet_trace" style="max-width:25%;">
</details>
 <details>
    <summary>2.VCS (hello gitty), GitHub and Collaboration</summary>
    # Credits, this descriptions of commands taken from Udacity course <a href="https://www.udacity.com/course/version-control-with-git--ud123" rel="nofollow">Version Control with Git</a> and <a href="https://learngitbranching.js.org" rel="nofollow">learngitbranching.js.org</a> 
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/main/task_git_collaboration/photo_2020-11-06_19-49-09.jpg">
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/main/task_git_collaboration/photo_2020-11-06_19-47-57.jpg">
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/main/task_git_collaboration/photo_2020-11-06_19-47-48.jpg">    
</details>
<details>
    <summary>3.Intro to HTML & CSS</summary>
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/main/task_html_css_intro/photo_2020-11-29_18-45-44.jpg">
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/main/task_html_css_intro/photo_2020-11-29_18-45-59.jpg">
<img src="https://github.com/ivanpikulyk/kottans-frontend/blob/main/task_html_css_intro/photo_2020-11-29_18-46-07.jpg">    
</details>
