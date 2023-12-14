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