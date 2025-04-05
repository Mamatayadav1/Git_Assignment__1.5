# Git Assignment 1.5 - GitFlow Workflow

This repository demonstrates a complete **GitFlow Workflow** using PowerShell on Windows. Below is the full terminal output with commands and results.

---

##  Step 1: Initialize Git and Add Remote

```powershell
PS C:\Users\HP> git init
Initialized empty Git repository in C:/Users/HP/.git/

PS C:\Users\HP> git remote add origin https://github.com/Mamatayadav1/Git_Assignment__1.5.git

PS C:\Users\HP> git remote -v
origin  https://github.com/Mamatayadav1/Git_Assignment__1.5.git (fetch)
origin  https://github.com/Mamatayadav1/Git_Assignment__1.5.git (push)

```

##  Step 2: Create and Push Develop Branch

```
PS C:\Users\HP> git checkout -b develop
Switched to a new branch 'develop'

PS C:\Users\HP> git commit --allow-empty -m "Initial commit on develop"
[develop (root-commit) 69ad632] Initial commit on develop

PS C:\Users\HP> git push -u origin develop --force
To https://github.com/Mamatayadav1/Git_Assignment__1.5.git
 * [new branch]      develop -> develop
branch 'develop' set up to track 'origin/develop'.

```
## Step 3: Feature Branch Workflow
```
PS C:\Users\HP> git checkout -b feature/new-feature develop
Switched to a new branch 'feature/new-feature'

PS C:\Users\HP> New-Item feature.txt
New-Item : The file 'C:\Users\HP\feature.txt' already exists.

PS C:\Users\HP> git add feature.txt

PS C:\Users\HP> git commit -m "Add feature.txt"
[feature/new-feature 66caab9] Add feature.txt

PS C:\Users\HP> git checkout develop
Switched to branch 'develop'

PS C:\Users\HP> git merge feature/new-feature
Fast-forward
 feature.txt | Bin 0 -> 58 bytes

PS C:\Users\HP> git push origin develop
develop -> develop

```

## Step 4: Release Branch Workflow

```
PS C:\Users\HP> git checkout -b release/1.0 develop
Switched to a new branch 'release/1.0'

PS C:\Users\HP> git push -u origin release/1.0
 * [new branch]      release/1.0 -> release/1.0

PS C:\Users\HP> git checkout -b master develop
Switched to a new branch 'master'

PS C:\Users\HP> git push -u origin master
 * [new branch]      master -> master

PS C:\Users\HP> git checkout develop
Switched to branch 'develop'

PS C:\Users\HP> git merge release/1.0
Already up to date.

PS C:\Users\HP> git push origin develop
Everything up-to-date

PS C:\Users\HP> git checkout master
Switched to branch 'master'

PS C:\Users\HP> git merge release/1.0
Already up to date.

PS C:\Users\HP> git push origin master
Everything up-to-date

```
## Step 5: Hotfix Branch Workflow

```
PS C:\Users\HP> git checkout -b hotfix/urgent master
Switched to a new branch 'hotfix/urgent'

PS C:\Users\HP> New-Item urgent.txt
    Directory: C:\Users\HP
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          4/5/2025   2:46 PM              0 urgent.txt

PS C:\Users\HP> git add urgent.txt

PS C:\Users\HP> git commit -m "Add urgent fix urgent.txt"
[hotfix/urgent c10f5d7] Add urgent fix urgent.txt

PS C:\Users\HP> git checkout master
Switched to branch 'master'

PS C:\Users\HP> git merge hotfix/urgent
Fast-forward
 urgent.txt | 0

PS C:\Users\HP> git push origin master
master -> master

```
##  Final Branch Status
### develop: Ongoing development

### feature/new-feature: Feature development (merged)

### release/1.0: Version 1.0 release (merged)

### master: Stable production-ready branch

### hotfix/urgent: Urgent fix merged into master
