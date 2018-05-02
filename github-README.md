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
$ git remote -v
origin  https://github.com/himansu979/pythonPractice.git (fetch)
origin  https://github.com/himansu979/pythonPractice.git (push)
```

### 2. git commands for pushing local repository to github
Following commands are very useful. `git status`, `git add`, `git commit`, `git log`, `git pull`, `git push`.

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



