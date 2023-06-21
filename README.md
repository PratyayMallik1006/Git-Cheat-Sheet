# Git-Cheat-Sheet

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
# Initializing Repository
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
# Git Workflow
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
git diff --stages
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
