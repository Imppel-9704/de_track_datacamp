# Introduction to Git
## Introduction to version control with Git

What is a version?
1. Contents of a file at a given point in time.
2. Metadata (information associated with the file):
  - The author of the file
  - Where it is located
  - The file type
  - When it was last saved

What is version control?
- Version control is a group of systems and processes
  - to manage changes made to documents, programs, and directories
- Version control is useful for anything that:
  - Changes over time, or
  - needs to be shared
- Track files in different states
- Simultaneous file development (Continuous Development)
- Combine different versions of files
- Identify a particular version
- Revert changes

Git
- Popular version control system for computer programming and data projects
- Open source
- Scalable
- Git is not GitHub, but
- it's common to use git with github

Benefits of Git
- Git stores everthing, so nothing is lost
- Git notifies us when there is conflicting content in files
- Git synchronizes across different people and computers

Using Git
- Git commands are run on the shell, also known as the terminal
- The shell:
  - is a program for executing commands
  - can be used to easily preview, modify, or inspect files and directories
- Directory = folder

Useful shell commands
\
print directory
```
pwd
```
\
returns a list of all files and directory
```
ls
```
\
changing directory
```
cd directory
```
\
Editing a file
```
nano finance.csv
```

- Use nano to:
  - delete,
  - add,
  - or change contents of a file
- save changes: Ctrl + O
- Exit the text editor: Ctrl + X

- create or edit a file
```
echo
```
- cteate a new file todo.txt
```
echo "Review for duplicate records" > todo.txt
```
- Add content to existing file todo.txt
```
echo "Add more text to the file" >> todo.txt
```

### Saving files
Git stores all of its extra information in a directory called .git, located in the main directory of the repo. Should not edit or delete .git
\
Git workflow
- Modify a file
- Save the draft
- Commit the updated file
- Repeat
\
Saving a file
- Adding a single file
```
git add file_name.md
```

- Adding all modified files
```
git add .
```
- ```.``` = all files and directories in current location
\
Making a commit
```
git commit -m "Updating something in file_name.md"
```
- Log message is useful for reference
- Best practice = short and concise
\
Check the status of files
```
git status
```

### Comparing files
Comparing a single file
\
Compare the last committed version of a file with the unstaged version
```
git diff file_name.md
```
![Image](https://drive.google.com/uc?id=1qvgJ2-Ds3Ni2GUoPDX3BqyFg3RrAac3n)

Comparing a staged file with the last commit
```
git add report.md
```
```
git diff -r HEAD report.md
```
-r: to indicate we want to look at a particular revision of the file
HEAD: which is a shortcut for the most recent commit, allows us to see the difference between file in the staging area and in the last commit
\
Comparing multiple staged files with the last commit
```
git diff -r HEAD
```

## Making changes
### Storing data with Git
The commit structure Git commits have 3 parts: 
- Commit 
  - contains the metadata 
- Tree 
  - tracks the names and locations in the repo 
- Blob 
  - binary large object 
  - may contain data of any kind 
  - compressed snapshot of a file's contents

![Image](https://drive.google.com/uc?id=1EliQYsWPcx21AqJXxJglriw-cLHXS3mA)

Git log
\
To view commit information
```
git log
```

### Viewing changes
The HEAD shortcut ```git diff -r HEAD``` 
- Compares staged files to the version in the last commit 
- User a tilde ~ to pick a specific commit to compare versions 
  - HEAD~1 = the second most recent commit 
  - HEAD~2 = the commit before that 
- Must not use spaces before or after the tilde ~

What changed between 2 commits? 
- To compare the fourth and third most recent commits 
```
git diff 35f4b4d 186398f
```
or 
```
git diff HEAD~3 HEAD~2
```
\
Changes per document by line 
```
git annotate report.md
```

### Undoing changes before committing
Unstaging a single file in git 
- To unstage a single file:
```
git reset HEAD summary_statistics.csv
```
```
nano summary_statistics.csv
```
```
git add summary statistics.csv
```
```
git commit -m "Adding age summary statistics"
```
\
Unstaging all files 
- To unstage all files 
```
git reset HEAD
```
\
Undo changes to an unstaged file 
- Suppose we need to undo changes to a file in the repository 
```
git checkout -- summary_statistics.csv
``` 
- checkout: means switching to a different version 
  - Defaults to the last commit 
- This means losing all changes made to the unstaged file forever
\
Undo changes to all unstaged files
```
git checkout .
```
\
Unstaging and undoing
1. unstage all files
```
git reset HEAD
```
2. checkout the last commit, replacing all versions of files in the repo
```
git checkout .
```
3. Save the repo, using add all files to the staging area
```
git add .
```
4. commit 
```
git commit -m "Restore repo to previous commit"
```

### Restoring and reverting
Customizing the log output 
- We can restrict the number of commits displayed using -: 
```
git log -3
``` 
- To only look at the commit history of one file: 
```
git log -3 report.md
```
- Restrict git log by date: 
```
git log --since='Month Day Year'
``` 
- Commits since 2nd Apr 2022: 
```
git log --since='Apr 2 2022'
``` 
- Commits betweens 2nd and 11th Apr:
```
git log --since=='Apr 2 2022' --until='Apr 11 2022'
```
\
Restoring an old version of file 
```
git log --since='Jul 8 2022'
``` 
```
git checkout -- filename
``` 
- To revert to a version from a specific commit: 
```
git checkout dc9d8fac mental_health_survey.csv
``` 
- This was the second to last commit, so another approach is:
```
git checkout HEAD~1 mental_health_survey.csv
```
\
Restoring a repo to a previous state 
```git checkout dc9d8fac
``` 
- Alternatively: 
```
git checkout HEAD~1
``` 
\
Cleaning a repository 
- See what files are not being tracked: 
```
git clean -n
``` 
- Delete those files: 
```
git  clean -f
```

## Git workflows
### Configuring Git
Level of setting 
- ```git config --list``` 
- Git has 3 levels of settings: 
1. --local: settings for one specific project  
2. --global: settings for all of out projects 
3. --system: settings for every users on this computer

What can we configure? 
```git config --list``` 
- user.email and user.name are needed by some commands, so setting these saves time! 
- user.email and user.name are global settings

Changing our settings 
```
git config --global setting value
``` 
- Change email to johnsmith@datacamp.com: 
```
git config --global user.email johnsmith@datacamp.com
``` 
- Change username to John Smith: 
```
git config --global user.name 'John Smith'
``` 
- If we don't use '' and our user.name has a space: 
  - git would save user.name as John

### Branches
- Git uses branches to systematically track multiple versions of files 
- In each branch: 
  - some files might be the same 
  - others might be different 
  - some may not exist at all

Benefits of branches 
- Avoiding endless subdirectories 
- Multiple users can work simultaneously 
- Everything is tracked 
- Minimizes the risk of conflicting versions

Identifying branch
```
git branch
```
- ```*``` = current branch

Creating new branch 
```
git checkout -b report
```

### Working with branches
Switch between branches
```
git checkout -b new_branch
```
switch to debugging branch
```
git checkout debugging
```
\
Merge branch
```
git merge source_branch destination_brach
```
- To merge summary into main
```
git merge summary main
```

## Collaborating with Git
### Creating repos
Why make a report? Benefits of repos 
- Systematically track versions 
- Collaborate with colleagues 
- Git stores everything!

Creating new repo 
```
git init mental-health-workspace
``` 
```
cd mental-health-workspace
``` 
```
git status
```
\
Nested repo 
- Don't create a git repo inside another git repo 
  - Known as nested repos 
- There will be 2 .git directories 
- Which .git directory should be updated? 
- Not necessary in most circumstances

Why use remote repos? 
\
Benefits of remote repos 
- Everything is backed up
- Collaboration, regardless of location

Cloning locally 
```
git clone path-to-project-directory
``` 
```
git clone /home/john/repo
``` 
```
git clone /home/john/repo new_repo
```

Cloning a remote 
- Remote repos are stored in an online hosting service e.g., GitHub, Bitbucket, or Gitlab 
- If we have an account: 
  - We can clone a remote repo on to our local computer
```
git clone [url]
```
\
```
git clone https://github.com/datacamp/project
```

Identifying a remote 
- When cloning a repo 
  - Git remembers where the original was 
- Git stores a remote tag in the new repo's configuration 
```
git remote
```

Creating remote 
- When cloning, Git will automatically name the remote origin 
```
git remote add name URL
``` 
```
git remote add george https://github.com/geirge_datacamp/repo
``` 
- Defining remote names is useful for merging branches

### Gathering from a remote
Remote vs. Local
![Image](https://drive.google.com/uc?id=1gUecLmWfdZHxxJFdQTgu09hN7wz7nsw3)

![Image](https://drive.google.com/uc?id=17EAXoMmELB92IUMperHwNsXhte4chMn9)

Fetching from a remote 
```
git fetch origin main
```

Synchonizie content 
```
git merge origin main
```

Pulling from a remote 
- remote is often ahead of local repos 
- fetch and merge is a common workflow 
- Git simplifies this process for us! 
```
git pull origin main
```

Pulling with unsaved local changes 
```
git pull origin
```
- Important to save locally before pulling from a remote

### Pushing to a remote
git push 
- Save changes locally first! 
```
git push remote local_branch
``` 
- Push into remote from local_branch
```
git push origin main
```

## Git Cheat Sheet
https://education.github.com/git-cheat-sheet-education.pdf