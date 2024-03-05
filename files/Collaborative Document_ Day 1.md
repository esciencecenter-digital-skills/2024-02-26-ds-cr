![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document: Day 1

2024-02-26--29 Good Practices in Research Software Development Day 1.

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

----------------------------------------------------------------------------

##  🫱🏽‍🫲🏻 Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.
 
## 🎓 Certificate of attendance

If you attend the full workshop you can request a certificate of attendance by emailing to training@esciencecenter.nl .

## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, raise your hand in zoom. Click on the icon labeled "Reactions" in the toolbar on the bottom center of your screen,
then click the button 'Raise Hand ✋'. For urgent questions, just unmute and speak up!

You can also ask questions or type 'I need help' in the chat window and helpers will try to help you.
Please note it is not necessary to monitor the chat - the helpers will make sure that relevant questions are addressed in a plenary way.
(By the way, off-topic questions will still be answered in the chat)


## 🖥 Workshop website

[link](https://esciencecenter-digital-skills.github.io/2024-02-26-ds-cr/)

🛠 Setup

[link](https://esciencecenter-digital-skills.github.io/2024-02-26-ds-cr/#setup)

## 👩‍🏫👩‍💻🎓 Instructors

Sander van Rijn, Sven van der Burg, Olga Lyashevska

## 🧑‍🙋 Helpers

Dani Bodor

## 🗓️ Agenda
| Time | Topic |
|--:|:---|
| 9:00 | Welcome and icebreaker |
| 9:15 | Introduction to version control with Git |
| 10:15 | Coffee break |
| 10:30 | Introduction to version control with Git |
| 11:30 | Coffee break |
| 11:45 | Introduction to version control with Git |
| 12:45 | Wrap-up |
| 13:00 | END |


## 🔧 Exercises

### Tracking changes exercise

#### 1. Which command(s) below would save the changes of myfile.txt to my local Git repository?
git add myfile.txt

1. `git commit -m "my recent changes"`
2. `git init myfile.txt`
   `git commit -m "my recent changes"`
3. `git add myfile.txt`
   `git commit -m "my recent changes"`
4. `git commit -m myfile.txt "my recent changes"`

#### 2. Committing Multiple Files
Remember that the staging area can hold changes from any number of files that you want to commit as a single snapshot.

1. Add some text to ``mars.txt`` noting your decision to consider Venus as a base
2. Create a new file ``venus.txt`` with your initial thoughts about Venus as a base for you and your friends
3. Add changes from both files to the staging area, and commit those changes.

**Answer:**

```bash
$ nano mars.txt
# write about venus decision and save the file
$ nano venus.txt
# write about venus
$ git add mars.txt venus.txt  # could also be done in two separate commands
$ git commit -m "Add notes about Venus base"
```


#### 3. (optional) A new repository
1. Create a new Git repository on your computer called bio.
2. Write a three-line biography for yourself in a file called me.txt.
3. Add the file to the staging area, and commit your changes.
4. Make a modification.
5. Display the differences between its updated state and its original state.

**Answer:**

```bash
$ cd your/prefered/directory  # go to where you want to make your new repository
$ mkdir bio  # create new folder
$ cd bio     # go to new folder
$ git init   # initialize empty git repository
$ nano me.txt
# write biography
$ git add me.txt
$ git commit -m "Write three-line bio"
$ nano me.txt
# make changes
$ git diff  # show the changes you made
$ git diff --color-words  # show differences on a per-word level instead of per line
```


### Exploring history exercise

#### 1. Recovering Older Versions of a File
Jennifer has made changes to the Python script that she has been working on for weeks, and the modifications she made (& committed!) this morning “broke” the script and it no longer runs. She has spent ~ 1hr trying to fix it, with no luck…

Luckily, she has been keeping track of her project’s versions using Git! Which commands below will let her recover the last committed version of her Python script called `data_cruncher.py?` Multiple options might be correct:

1. `$ git checkout HEAD`
2. `$ git checkout HEAD data_cruncher.py`
3. `$ git checkout HEAD~1 data_cruncher.py`
4. `$ git checkout <unique ID of last commit> data_cruncher.py`

**Answer:** 3 & 4

#### 2. (optional) Understanding Workflow and History

What is the output of the last command in
```
$ cd planets
$ echo "Venus is beautiful and full of love" > venus.txt
$ git add venus.txt
$ echo "Venus is too hot to be suitable as a base" >> venus.txt
$ git commit -m "Comment on Venus as an unsuitable base"
$ git checkout HEAD venus.txt
$ cat venus.txt #this will print the contents of venus.txt to the screen
```
1. Venus is too hot to be suitable as a base
2. Venus is beautiful and full of love
3. Venus is beautiful and full of love
4. Venus is too hot to be suitable as a base
5. Error because you have changed venus.txt without committing the changes

**Answer:**
2&3, the change of "Venus is too hot to be suitable as a base", was not added, so the `git commit` committed the state of `venus.txt` at the time of `git add venus.txt`. `git checkout HEAD venus.txt` restored it to the last committed version.

#### 3. (optional) Reverting a Commit

Jennifer is collaborating on her Python script with her colleagues and realizes her last commit to the project’s repository contained an error and she wants to undo it. `git revert [erroneous commit ID]` will create a new commit that reverses Jennifer’s erroneous commit. Therefore `git revert` is different to `git checkout [commit ID]` because `git checkout` returns the files within the local repository to a previous state, whereas `git revert` reverses changes committed to the local and project repositories.
Below are the right steps and explanations for Jennifer to use `git revert`, what is the missing command?

1. `________ # Look at the git history of the project to find the commit ID`
2. `Copy the ID (the first few characters of the ID, e.g. 0b1d055).`
3. `git revert [commit ID]`
4. Type in the new commit message.
5. Save and close

**Answer:**
`git log`


### Optional exercises during SSH setup check
#### 1. CHECKING UNDERSTANDING OF `git diff`
Consider this command: `git diff HEAD~9 mars.txt`. What do you predict this command will do if you execute it? What happens when you do execute it? Why?

Try another command, `git diff [ID] mars.txt`, where [ID] is replaced with the unique identifier for your most recent commit. What do you think will happen, and what does happen?

#### 2. GETTING RID OF STAGED CHANGES
`git checkout` can be used to restore a previous commit when unstaged changes have been made, but will it also work for changes that have been staged but not committed? Make a change to mars.txt, add that change using `git add`, then use `git checkout` to see if you can remove your change.

#### 3. IGNORING NESTED FILES
Given a directory structure that looks like:

```bash
results/data
results/plots
```

How would you ignore only `results/plots` and not `results/data`?

#### 4. INCLUDING SPECIFIC FILES
How would you ignore all `.csv` files in your root directory except for final.csv? Hint: Find out what `!` (the exclamation point operator) does



## 🧠 Collaborative Notes

Quick test to see if `git` is correctly installed: print its installed version
```bash
$ git --version
```

Git has configuration options
```bash
$ git config --help  # show options
...
# You have to set up your name and email first:
$ git config --global user.email "your.email@example.com"  # Set your email
$ git config --global user.name "Your Name"                # Set your name
$ git config --global user.name                            # show what is configured as user.name
Your Name
$ git config --global core.editor nano  # If you don't already have a preference, we recommend nano
# ^ means the 'Ctrl' button, so '^O Write out'  means press 'Ctrl+O' to save
$ git config --global init.defaultBranch main  # in some old versions, this is still set to "master", which comes from "master/slave" terminology
$ git config --global --edit   # open the configuration file in the currently configured editor 
$ git config --list  # lists all configured options
$ man git-config  # 'man' means 'manual', shows the help information for git's configuration
```


Let's create a new git repository:
```bash
$ cd your/prefered/directory  # 'cd' means 'change directory'
$ mkdir planets  # 'mkdir' means 'make directory'
$ ls  # 'ls' means 'list', shows what is in the current directory
$ cd planets
$ ls -a  # also shows hidden files and folders
.  ..  # only '.' (the current folder) and '..' (the parent folder) are visible, so this folder is empty
$ git init  # initialize a new git repository
$ ls -a
.  ..  .git
```
The `.git`'folder contains all the 'magic' that Git does in the background. If you ever need to remove the repository information, you can simply remove the `.git` folder.

Let's create some files to work in so we have some changes to track:

```bash
$ nano mars.txt  # open mars.txt in the nano editor
# <make your edits>
$ ls  # our folder now contains a file!
mars.txt$ git status  # gives an overview of the current state of your repository
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        mars.txt

nothing added to commit but untracked files present (use "git add" to track)
$ git add mars.txt  # add mars.txt to the 'staging area', i.e., prepare them to be commited
$ git commit -m "Start notes on Mars as a base"  # make the commit, and immediately add the message with -m. Wihtou -m, it will open the configured editor to write one
$ git status
# no changes
$ git log  # shows a history of your commits
```

:::info
You can ignore warnings about `LF will be replaced by CRLF` for now, we will address that in day 2
:::

```bash
$ nano mars.txt
# <make more changes>
$ git status
# there are changes to mars.txt!
$ git diff  # shows the difference between current state of files and the staging area
$ git commit -m "Add concerns about effects of moons on Wolfman"
# Nothing committed! Nothing was added
$ git add mars.txt
$ git diff
# no differences shown because they're already in the staging area
$ git diff --staged
# now we do see the differences
$ git commit -m "Add concerns about effects of moons on Wolfman"
$ git log
# new commit has appeared in the log
$ git log --oneline
# more compact commit log
```

Branches:
```bash
$ git branch  # show what branches you have, but only after the first commit 🙃
$ git switch -c feature  # switch to a newly 'c'reated branch (old alternative: git checkout -b feature)
```

### Exploring History

```bash
$ git diff HEAD~2 mars.txt
# shows difference for mars.txt between now and 2 commits ago
$ git log
# copy hash ID of desired commit
$ git diff 4b52963a... mars.txt
# same result
$ git show 4b52963a... mars.txt
# shows differences committed in that commit
$ git restore 4b52963a... mars.txt  # old style: git checkout 4b52963a... mars.txt
# mars.txt has been set back to the state it was in at commit 4b52963a...
# to save these changes we would have to 'git add mars.txt' and `git commit' them again
$ git restore HEAD mars.txt  # old style: git checkout HEAD mars.txt
# mars.txt has been set back to its version in the latest commit
```

### Ignoring Things

You can often have files you don't want to commit, such as output files
```bash
# simlate data & output files
$ touch a.csv
$ touch b.csv
$ mkdir results
$ touch results/c.csv
$ git status  # shows all kinds of files we don't want to see
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        a.csv
        b.csv
        results/
        
$ nano .gitignore
*.csv      # ignore all csv files
results/   # ignore everything in the 'results' folder
# save file

$ git status  # unwanted files are gone, .gitignore now shows up which you can add to your repository
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
```

Supppose you forgot to add files to `.gitignore` and already commited them. To stop tracking files that were previously committed and add them to `.gitignore`.

```bash
# Add the files to .gitignore
echo 'file_to_ignore' >> .gitignore
# Remove the files from the repository
git rm --cached file_to_ignore
git commit -m "Stop tracking some files"
```
Replace `files_to_ignore` with path of the file or directory you want to ignore. If it is a directory, make sure to append a `/` at the end.

### SSH

To check whether your SSH keys have been set up correctly:
```bash
$ ssh -T git@github.com
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```



## 📚 Resources