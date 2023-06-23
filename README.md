# Git Cheat Sheet
### Alternatives:
- Microsoft Team Foundation Server
- Subversion
- Mercurial
## Using Git
1. Command Line Interface
2. code editors & IDEs
- VS Code extensions: GitLens
3.  GUI
- GitKraken
- SourceTree
# Install Git:
1. Goto https://git-scm.com/downloads
```git
git --version
```
# Configuration Git:
1. System - All Users
2. Global - All repositories of the current user
3. Local - The current repository

```git
git config --global user.name "Toto Wolff"
git config --global user.email "Toto@mercedes.com"
git config --global core.editor "code -- wait"
```
Edit all global settings in default editor
```git
git config --global -e
```
End of line configuration
Windows
```git
git config --global core.autocrlf true
```
Linux/Mac
```git
git config --global core.autocrlf input
```
## Help
Detailed Documentation
```git
git config --help
```
Brief Documentation
```git
git config -h
```
# Creating Snapshots
## Initializing Repository
```git
mkdir shopping
cd shoppinh
git init
ls -a
```
Removing git
```git
rm -rf .git
```
## Git Workflow
1. Staging (Indexing)
```git
git add file1.txt file2.txt
```
2. Commit
```git
git commit -m "Initial Commit"
```
Add all files to staging area
```git
git add .
git add *.txt
```
Seeing files in staging area
```git
git ls-files
```
## Get details of repository
```git
git status
```
## Adding Long Description to Commit
```git
git commit
```
## Skipping the Staging Area
```git
git commit -a -m "Bug Fixed"
```
## Removing Files
```git
rm file2.txt
git add file2.txt
git commit -m "File 2 removed"
```
Or
```git
git rm file2.txt file3.txt
```
## Renaming or Moving Files
Renaming
```git
mv file1.txt main.txt
```
Staging
```git
git add file1.txt
git add main.txt
```
Or
```git
git mv main.txt file1.txt
```
Commit
```git
git commit -m "Renamed"
```
## Ignoring Files
Know More: https://github.com/github/gitignore
Create file .gitignore
```
logs/
main.log
*.log
```
Commit gitignore
```git
git add .gitignore
git commit -m "Add gitignore"
```
## Removing Files from Staging Area
```git
git rm --cached main.txt
git rm --cached -r logs/
```
## Short Status
```git
git status -s
```
## Viewing Staged and Unstaged Changes
Staged Changes
```git
git diff --staged
```
Unstaged Changes
```git
git diff
```
## Viewing History
```git
git log
```
Getting Only Commit message
```git
git log --oneline
```
Ordering in reverse, oldest to newest
```git
git log --oneline --reverse
```
## Viewing Commit
```git
git log --oneline
git show 8f092f7
```
3 steps from head
```git
git show HEAD~3
```
List all files and folders
```git
git ls-tree HEAD~1
```
## Unstaging Files
```git
git restore --staged file1.txt file3.txt
git restore --staged .
```
## Discarding Local Changes
```git
git restore file1.txt
git clean -f -d
```
## Restoring File to an Earlier Version
```git
git restore --source=HEAD~1 file1.txt
```
# Browsing History
## Viewing the History
```git
git log
git log --oneline
git log --stat
```
To see exactly what was changed
```git
git log --patch
```
## Filtering the History
Last 3 commit
```git
git log --oneline -3
```
By Author
```git
git log --oneline --author="Toto Wolff"
```
By Date
```git
git log --oneline --after="2023-06-15"
git log --oneline --after="yesterday"
```
Commit message contains
```git
git log --oneline --grep="GUI"
```
Filter by content
```git
git log --oneline -S"hello()"
git log --oneline -S"hello()" --patch
```
Filter by file
```git
git log --oneline file1.txt
```
## Formatting the Log Output
```git
git log --pretty=format:"%an author, Hash %H, abbriviated %h, date %Cgreen%cd"
```
## Viewing Commit
```git
git log --oneline
git show 8f092f7
git show HEAD~2:folder1/folder2/file1.txt
git show HEAD~2 --name-only
git show HEAD~2 --name-status
```
## Viewing Changes Across Commits
```git
git show HEAD~2 HEAD
```
## Check Out a Commit
Viewing older version by moving HEAD from MASTER
```git
git checkout 8f092f7
git log --oneline --all
git checkout master
```
## Bisect
To debug commits by diving the commit history into two parts and defining which half is good and which half is bad
## Shortlog - Finding Contributors
```git
git shortlog
```
Short by number of commits of author
```git
git shortlog -n
```
Suppress - Only author and number of commits
```git
git shortlog -n -s
```
Email of Author
```git
git shortlog -n -s -e
```
## History of a File
```git
git log --oneline --stat file1.txt
git log --oneline --patch file1.txt
```
## Restoring Deleted File
```git
git log --oneline -- file1.txt
git checkout 8f092f7 file1.txt
git commit -m "Restored file1"
```
## Blame - Find the Author
```git
git blame -e file4.txt
```
## Tagging - Bookmarking
```git
git tag v1.0
git tag v1.0 8f092f7
git checkout v1.0
```
Seeing all tags
```git
git tag -n
```
Annotated Tag
```git
git tag v1.1 -m "Version 1.1"
git show v1.1
```
Deleting Tag
```git
git tag -d v1.1
```
# Branching
## Working With Branches
Creating new branch
```git
git branch bugfix
```
Viewing all branches
```git
git branch
```
Checking the current branch
```git
git status
```
Changing to different branch
```git
git switch bugfix
```
Changing branch name
```git
git branch -m bugfix bugfix-signup-form
```
Viewing Commits across all branches
```git
git log --oneline --all
```
Deleting branch
```git
git branch -D bugfix-signup-form
```
## Comparing Branches
```git
git log master..bugfix-signup-form
git diff master..bugfix-signup-form
```
If we are on MASTER branch
```git
git diff bugfix-signup-form
git diff --name-status bugfix-signup-form
```
## Stashing - Storing Local Changes
Until changes of current branch is not committed we cannot move to another branch, we can either commit changes or stash changes
>**Stashing:** Storing local changes to move branches
```git
git stash push -m "new feature"
```
Stashing all changes
```git
git stash push -a -m "new feature"
```
View Stash
```git
git stash list
```
Apply changes after coming back to branch
```git
git stash show 1
git stash apply 1
```
Removing Stash
```git
git stash drop 1
```
Removing all Stashes
```git
git stash clear
```
## Merging
**Fast Forward Merging:** When there is no change in MASTER branch, we can directly merge into other branch
**3 Way Merge:** Changes in both,  MASTER branch and new branch.
## Fast Forward Merge
```git
git log --oneline --all --graph
git merge bugfix-signup-form
```
**Preventing Fast Forward Merge:**
Uses 'recursive' strategy
```git
git merge --no-ff bugfix-signup-form
```
>Why Preventing Fast Forward Merge is Preferred:
>1. True reflection of history
>2. Allow reverting a feature

**Disabling Fast Forwarding in Current Repository:**
```git
git config ff no
```
## 3-Way Merge
Changes in both,  MASTER branch and new branch.
```git
git log --oneline --all --graph
git merge bugfix-signup-form
```
## Viewing Merged and Unmerged Branches
All Merged branched should be deleted
```git
git branch --merged
git branch --no-merged
```
## Merge Conflicts
```git
git merger bugfix-signup-form
git status
```
## Visual Merge Tools
1. Kdiff
2. P4Merge
3. WinMerge
**Configuring Default Merge Tool**
```git
git config --global merge.tool p4merge
git config --global mergetool.p4merge "C:\p4merge"
```
## Aborting a Merge
```git
git merger bugfix-signup-form
git merger --abort
```
## Undoing Faulty Merge
```git
git merger bugfix-signup-form
```
1. Removing a Commit
```git
git reset --hard HEARD~1
```
2. Reverting a Commit
```git
git revert -m 1 HEAD
```
## Squash Merge
Just committing the changes in new branch as a new commit
```git
git merge --squash bugfix-signup-form
git commit -m "Squash merge"
git branch -D bugfix-signup-form
```
## Rebasing
![Rebasing](https://cms-assets.tutsplus.com/cdn-cgi/image/width=630/uploads/users/1885/posts/106923/image-upload/rebase.png)
Making 3-way merge to Fast Forward Merge
```git
git switch bugfix-signup-form
git rebase master
git switch master
git merge bugfix-signup-form
```
Rebasing after solving conflict
```git
git rebase --skip
git rebase --continue
git rebase --abort
```
## Cherry Picking
Copying only one particular commit from another branch
```git
git cherry-pick 8f092f7
git commit -m "copying commit1"
```
## Picking a File from Another Branch
Copying only one particular file from another branch
```git
git switch master
git restore --source=bugfix-signup-form -- file1.txt
git commit -m "copying file1"
```
