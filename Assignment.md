[<img src="assets/images/su-logo.png" alt="Skills Union Logo" height="80px" />](https://www.skillsunion.com/)

# Team-workflow-with-Git-and-GitHub: Assignment

## Problem

This exercise is a little bit different. Rather than following my exact instructions step by step, I'd like for you to come up with your own scenarios that meet my requirements.

Start by creating a new repo. Make a file or two in the repo for you to work on.

If you need some inspiration...I'll be working in a file called `greetings.txt` It will contain greetings in different languages.

### 1: Fast Forward Merge

**Your goal is to generate a fast forward merge. Demonstrate that you understand how FF merges work by creating one on your own!**

Make a new branch. Do some work in the repo such that when you merge the new branch into master, it results in a fast forward merge. Merge that branch into master and see if you were right!

```
$ git branch
* master

$ git branch greetingcomp

$ git branch
  greetingcomp
* master

$ git switch greetingcomp
Switched to branch 'greetingcomp'

[Changes made to repo in greetingcomp branch]

$ git status
On branch greetingcomp
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   public/index.html
        modified:   src/App.js
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        src/Greeting.jsx
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .

$ git commit -m "Linked relevant files and created initial greeting"

$ git log
commit 375170d17ee37a59f4573f50ca750a2447c56b1a (HEAD -> greetingcomp)
Author: NealLyonsWake <waken.games@gmail.com>
Date:   Fri Oct 1 21:35:21 2021 +0100
    Linked relevant files and created initial greeting
commit 108667caa2dcf668fa2865960b3290c63df4bb2d (origin/master, master)
Author: NealLyonsWake <waken.games@gmail.com>
Date:   Fri Oct 1 21:24:57 2021 +0100
    Initial creation of app project and scope added to README.md
commit ff3f68762aa7074d7fd78e5cc661d7cb4bcd28f9
Author: NealLyonsWake <waken.games@gmail.com>
Date:   Fri Oct 1 21:21:26 2021 +0100
    Initialize project using Create React App

[Further changes made to repo in greetingcomp branch]

$ git status
On branch greetingcomp
Your branch is up to date with 'origin/greetingcomp'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   src/Greeting.jsx
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .

$ git commit -m "Added the array, state and interaction functions to Greeting component. Updated README.md file"

$ git switch master

$ git merge greetingcomp
Updating 108667c..f8543ee
Fast-forward
 README.md         |  4 +++-
 public/index.html |  3 ++-
 src/App.js        | 17 ++---------------
 src/Greeting.jsx  | 27 +++++++++++++++++++++++++++
 4 files changed, 34 insertions(+), 17 deletions(-)
 create mode 100644 src/Greeting.jsx
```

### 2: Merge Commit (No Conflicts)

Your goal is to generate a merge commit with NO MERGE CONFLICTS.

Create a new branch. Make some changes to the repo such that when you merge the new branch into master, it results in a merge commit. The merge should not result in any conflicts. Merge that branch into master and see if you were right!

```
$ git branch moreGreetings

$ git switch moreGreetings

[Changes made in moreGreetings branch]

$ git status
On branch moreGreetings
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   src/Greeting.jsx
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .

$ git commit -m "Added two greetings to the greetingArray"

[More Changes made in moreGreetings branch]

$ git status
On branch moreGreetings
Your branch is up to date with 'origin/moreGreetings'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   src/Greeting.jsx
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .

$ git commit -m "Added one other greeting to the greetingArray"

$ git switch master

[Changes made to master branch]

$ git status
On branch master
Your branch is up to date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .

$ git commit -m "Added further explaination of the branch and merge scope in README.md file"

$ git merge moreGreetings
Merge made by the 'recursive' strategy.
 src/Greeting.jsx | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

```

### 3: Conflicts!

Create a new branch. Make some changes to the repo such that when you merge the new branch into master, it results in a merge commit. The merge should not result in any conflicts. Merge that branch into master and see if you were right!

```
 $ git branch conflictGreetings

 $ git switch conflictGreetings

 [Changes made to conflictGreetings branch]

 $ git status
On branch conflictGreetings
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   src/Greeting.jsx
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .

$ git commit -m "Added two new greetings to greetingArray"

$ git switch master

[Changes made to master branch with one being a conflicting change to conflictGreetings branch]

$ git status
On branch master
Your branch is up to date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   src/Greeting.jsx
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .

$ git commit -m "Added two new greetings to greetingArray"

$ git merge conflictGreetings
Auto-merging src/Greeting.jsx
CONFLICT (content): Merge conflict in src/Greeting.jsx
Automatic merge failed; fix conflicts and then commit the result.

[Manually fixed changes to include all appropriate and unique code and removed conflicting code]

$ git status
On branch master
Your branch is up to date with 'origin/master'.
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)
Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   src/Greeting.jsx
no changes added to commit (use "git add" and/or "git commit -a")

$ git add .

$ git commit -m "Resolved merging conflict in greetingArray"

```

## Submission Guidelines

- Cite any relevant sources consulted during your research
- Solve the problems using your own code
- Do not copy and paste solutions from the source material
