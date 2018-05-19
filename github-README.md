# Git and Github commands

### 1. General git commands
```
$ cd dir/
/dir (master)
$ git --version
git version 2.17.0.windows.1
$ git branch
* master
$ git checkout master
Already on 'master'
Your branch is up to date with 'origin/master'.
```
After you ``cd`` into the directory, you will notice **(master)** is added at the end of the directory name. The ``*`` symbol before the
master shows that you are currently in master branch.
#### check global variables
```
$ git config --global user.name user_name
$ git config --global user.email user_email
$ git config --global core.editor
```
Check last few edits in the repository
```
$ git log -10 --oneline
953aaa1 (HEAD -> master, origin/master) Update README.md
1cba174 modified README.md file
```
Check the remote repositories
```
$ git remote
origin
$ git remote -v
origin  https://github.com/himansu979/pythonPractice.git (fetch)
origin  https://github.com/himansu979/pythonPractice.git (push)
```

### 2. git commands for pushing local repository to github
Following commands are very useful. `git status`, `git clone`, `git add`, `git commit`, `git log`, `git pull`, `git push`.

```
$ git pull https://github.com/himansu979/pythonPractice.git
$ git status
$ git add test.txt
$ git status
$ git commit -m "adding test.txt"
$ git status
$ git log
$ git push
$ git status
```

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```
After a new file **test.txt** is created in the same directory, **git** recognized it as untracked file.

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        test.txt

nothing added to commit but untracked files present (use "git add" to track)
```
Add this file to be committed.
```
$ git add test.txt
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   test.txt
```
Now **git** recognized it as a new file and ready to be committed to github. add a message for the change.
```
$ git commit -m "adding test.txt"
[master 4755aeb] adding test.txt
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
```
```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
```
$ git log
commit 4755aebf0f50ba8507988aadd8d9cc38027397a9 (HEAD -> master)
Author: user_name <user_email@xxx.com>
Date:   Tue May 1 20:46:43 2018 -0500

    adding test.txt
```

```
$ git push
To https://github.com/himansu979/pythonPractice.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/himansu979/pythonPractice.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
```git push``` is rejected, because one file is modified in the remote repository. do ```git pull``` first and then ```git push```.
Enter a message for the ``git pull``. 
<pre>
Some `vi` editor commands: 
`x` to delete 
`u` to undo last change 
`i` to enter command mode 
`Esc` exit command mode
`:x` to save and exit.
</pre>
```
Merge https://github.com/himansu979/pythonPractice

# Please enter a commit message to explain why this merge is necessary,
# especially if it merges an updated upstream into a topic branch.
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
```
```
$ git pull https://github.com/himansu979/pythonPractice.git
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/himansu979/pythonPractice
 * branch            HEAD       -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 README.md | 2 ++
 1 file changed, 2 insertions(+)
```

```
$ git push
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 552 bytes | 552.00 KiB/s, done.
Total 5 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/himansu979/pythonPractice.git
   d024bed..bfb4797  master -> master
```

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

### 2. clone repository from github &rarr; local

```
$ git clone https://github.com/himansu979/pythonPractice.git
Cloning into 'pythonPractice'...
remote: Counting objects: 70, done.
remote: Compressing objects: 100% (59/59), done.
remote: Total 70 (delta 25), reused 21 (delta 5), pack-reused 0
Unpacking objects: 100% (70/70), done.
```

```
$ cd pythonPractice/
$ /pythonPractice (master)
$ git remote -v
origin  https://github.com/himansu979/pythonPractice.git (fetch)
origin  https://github.com/himansu979/pythonPractice.git (push)
```

Here no need to set up remote origin. Already it is linked.
```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```
modify test.txt file

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   test.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

```
$ git add test.txt
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   test.txt
```

```
$ git commit -m "added new line to test.txt"
[master 3aba7e8] added new line to test.txt
 1 file changed, 1 insertion(+)
```

```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

```
$ git log
commit 3aba7e85a91549d297787fa34ac4778b4c768b69 (HEAD -> master)
Author: himansu979 <himansusahoo@gmail.com>
Date:   Tue May 1 23:48:37 2018 -0500

    added new line to test.txt
```

```
$ git log -1 --oneline
3aba7e8 (HEAD -> master) added new line to test.txt
```

```
$ git push
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 289 bytes | 289.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/himansu979/pythonPractice.git
   8f763fc..3aba7e8  master -> master
```

### 3. Creating a new local git repository on command line

```
$ mkdir myProject
$ cd myProject
$ git init
Initialized empty Git repository in C:/Users/hisahoo.ISC/Desktop/Datascience/Weekly-DS-meeting/myProject/.git/
/myProject (master)
```
Since no git repository exist, we need to initialize it with `git init`. Once you type this a hidden folder `.git` appears in the repository. Type `ls -a` to view this.

```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

create a new file test1.txt
```
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        test1.txt

nothing added to commit but untracked files present (use "git add" to track)
```
`$ git remote -v` outputs nothing. There is no remote origin setup for this.

```
$ git log -1
fatal: your current branch 'master' does not have any commits yet
```

```
$ git add test1.txt
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   test1.txt
```

```
$ git commit -m "added test1.txt"
[master (root-commit) f62a3b0] added test1.txt
 1 file changed, 1 insertion(+)
 create mode 100644 test1.txt
```

```
$ git status
On branch master
nothing to commit, working tree clean
```

Modify test1.txt and add new test2.txt

```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   test1.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        test2.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
`git add .` adds all files for commit.

```
$ git add .
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   test1.txt
        new file:   test2.txt
```

```
$ git commit -m "added test2.txt"
[master 050e39e] added test2.txt
 2 files changed, 2 insertions(+), 1 deletion(-)
 create mode 100644 test2.txt
```

```
$ git status
On branch master
nothing to commit, working tree clean
```

since there is no remote origin for this repo, you have to setup one.
```
$ git remote -v
$ git remote add origin https://github.com/himansu979/pythonPractice.git
$ git remote -v
origin  https://github.com/himansu979/pythonPractice.git (fetch)
origin  https://github.com/himansu979/pythonPractice.git (push)
```

```
$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master
```
`git push` is giving error, because there is no upsream branch for this

```
$ git push -u origin master
To https://github.com/himansu979/pythonPractice.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/himansu979/pythonPractice.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
The remote origin repo is not empty. There is an `README.md` exists. First `git pull` this.
`-u` option is helpful for tracking the connection between local and remote branch.
You have to do this once for the first push, it will set up association between your branch and the remote branch.
Then you check with `git branch -a` and you can just do `git push`. <br>

`git push -u origin master` means push the changes from the master branch to the remote origin.
```
$ git pull
warning: no common commits
remote: Counting objects: 76, done.
remote: Compressing objects: 100% (63/63), done.
remote: Total 76 (delta 28), reused 24 (delta 6), pack-reused 0
Unpacking objects: 100% (76/76), done.
From https://github.com/himansu979/pythonPractice
 * [new branch]      master     -> origin/master
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> master
```

```
$ git pull https://github.com/himansu979/pythonPractice.git
From https://github.com/himansu979/pythonPractice
 * branch            HEAD       -> FETCH_HEAD
fatal: refusing to merge unrelated histories
```

Since it is first pull request, giving error

```
$ git pull https://github.com/himansu979/pythonPractice.git --allow-unrelated-histories
From https://github.com/himansu979/pythonPractice
 * branch            HEAD       -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 Auto.csv                | 393 +++++++++++++++++++++
 README.md               |  39 ++
 github-README.md        | 268 ++++++++++++++
 images/scatter-plot.png | Bin 0 -> 97228 bytes
 lab-one.ipynb           | 918 ++++++++++++++++++++++++++++++++++++++++++++++++
 test.txt                |   2 +
 6 files changed, 1620 insertions(+)
 create mode 100644 Auto.csv
 create mode 100644 README.md
 create mode 100644 github-README.md
 create mode 100644 images/scatter-plot.png
 create mode 100644 lab-one.ipynb
 create mode 100644 test.txt
```

```
$ git push -u origin master
Counting objects: 9, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (9/9), 804 bytes | 804.00 KiB/s, done.
Total 9 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/himansu979/pythonPractice.git
   ed96d5b..65222e6  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```
```
$ git pull
Already up to date.
```

```
$ git push
Everything up-to-date
```

```
$ git pull https://github.com/himansu979/pythonPractice.git
From https://github.com/himansu979/pythonPractice
 * branch            HEAD       -> FETCH_HEAD
Already up to date.
```

```
$ git push -u origin master
Everything up-to-date
Branch 'master' set up to track remote branch 'master' from 'origin'.
```
### 3. Creating a new empty local git repository on command line

```
$ cd test-may02
$ git init
Initialized empty Git repository in C:/Users/test-may02/.git/
will change to (master)
```

```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

```
$ git pull https://github.com/himansu979/pythonPractice.git
remote: Counting objects: 88, done.
remote: Compressing objects: 100% (70/70), done.
remote: Total 88 (delta 31), reused 33 (delta 7), pack-reused 0
Unpacking objects: 100% (88/88), done.
From https://github.com/himansu979/pythonPractice
 * branch            HEAD       -> FETCH_HEAD
```
If you will do again `git pull`, it will show already up to date.

```
$ git pull https://github.com/himansu979/pythonPractice.git
From https://github.com/himansu979/pythonPractice
 * branch            HEAD       -> FETCH_HEAD
Already up to date.
```

```
$ git status
On branch master
nothing to commit, working tree clean
```
you don't see the message here `Your branch is up to date with 'origin/master'.`, because there is no remote orgin is setup yet.

```
$ git push
fatal: No configured push destination.
Either specify the URL from the command-line or configure a remote repository using

    git remote add <name> <url>

and then push using the remote name

    git push <name>
```

```
$ git remote -v
$ git remote add origin https://github.com/himansu979/pythonPractice.git
$ git remote -v
origin  https://github.com/himansu979/pythonPractice.git (fetch)
origin  https://github.com/himansu979/pythonPractice.git (push)
$ git status
On branch master
nothing to commit, working tree clean
```
Check that it still doesn't appear the link to upstream branch in git status

```
$ git push
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master
```

```
$ git push -u origin master
Everything up-to-date
Branch 'master' set up to track remote branch 'master' from 'origin'.
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

Just mark the output difference between these two commands.
```
$ git push -u origin master
Everything up-to-date
Branch 'master' set up to track remote branch 'master' from 'origin'.
$ git push
Everything up-to-date
```

```
$ git branch -a
* master
  remotes/origin/master
```
see now remote/origin/master shows up in git branch -a









