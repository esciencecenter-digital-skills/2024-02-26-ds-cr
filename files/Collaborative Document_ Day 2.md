![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document: Day 2

2024-02-26--29 Good Practices in Research Software Development Day 2.

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
| 9:15 | Workshop Introduction |
| 09:30 | Collaboration with Git and GitHub |
| 10:15 | Coffee break |
| 10:30 | Collaboration with Git and GitHub |
| 11:30 | Coffee break |
| 11:45 | Collaboration with Git and GitHub |
| 12:45 | Wrap-up |
| 13:00 | END |

## Welcome
- Questions about yesterday?
- Feedback from yesterday

## 🔧 Exercises

### 'The remote' exercises
#### GitHub GUI

Browse to your `planets` repository on GitHub. Under the Code tab, find and click on the text that says “XX commits” (where “XX” is some number). Hover over, and click on, the three buttons to the right of each commit. What information can you gather/explore from these buttons? How would you get that same information in the shell?

#### (optional) Push vs. Commit

In this lesson, we introduced the `“git push”` command. How is `“git push”` different from `“git commit”`?

Answer:
`git commit` adds the changes from your staging area to your _local_ repository. 
`git push` sends all changes in your local repository to the remote (online, on GitHub) repository 

#### (optional) GITHUB TIMESTAMP
Create a remote repository on GitHub. Push the contents of your local repository to the remote. Make changes to your local repository and push these changes. Go to the repo you just created on GitHub and check the [timestamps](https://swcarpentry.github.io/git-novice/reference.html#timestamp) of the files. How does GitHub record times, and why?

Answer: The primary visual time shown is a very rough timing (e.g., "yesterday" or "5h ago"). When hovering over the timestamp, you can see the exact date and time, including the time zone.


### Exercise: Working as a project collaborator (in pairs)

- Log into Github and create a new repository (ideally don't use identical names between the pair)
- Make the repository public
- clone it to your desktop
- add some code
- push the changes to the repository
- Add one person as a collaborator (settings -> Manage Access). Make sure everyone in the group has a collaborator.
- Clone that repo
- make changes on a new branch
- push the changes
- submit a Pull Request
- wait for approval
- At the same time review a collaborators Pull Request
- (Optionally) Learn about [protecting branches](https://docs.github.com/en/github/administering-a-repository/about-protected-branches) and try it out. 

### Exercise: Working as an external contributor (in breakout rooms):
- Remove your group member(s) as collaborators from your repository
- Fork another group members repo (Repository page, top right corner)
- Create an issue on the original repository
- Clone your forked repo to your computer
- Make some changes, use a somewhat real-world example so it makes sense to review it (but don't overdo it).
- Push it to your fork
- make a pull request from your fork to the main repository mentioning the issue
- Consider turning your Pull Request into a draft Pull Request.
- let your code be reviewed by tagging the repo owner using (@Username)
- At the same time review Pull Request using comments on individual lines. Try to act as if it was a real peer review as much as possible.
- Accept or reject the Pull Request
- (Optionally) learn about [merge conflicts](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts) and try it out in your collaboration. 

## 🧠 Collaborative Notes

### Questions from yesterday:

1. Are changes in the staging area (but not committed) also stored?
- Yes, they are in a sort of intermediate place where changes are tracked. Additional changes need be added to the staging area using `git add <filename>` to ensure they are fully tracked.

2. Why are we using git BASH?
- It is more similar to the Unix OS than e.g. Windows command prompt. 


### Adding your local repository to the remote (GitHub) repository
GitHub will also helkp guide you through this (select ssh instead of https first).

add a remote (online) source for your repository and then push your local onto the remote. In your repositroy folder run:

```bash
git remote add origin git@github.com:<username>/planets1.git
git push origin main
```

If you then refresh the browser on the GitHub page, then you will see the files have been added to your remote repository.


### Collaborative coding workflow

#### Adding a collaborator to a project/repository

Person A (main project developer)
- Navigate to Settings/Collaborators in GitHub (this will require authentication).
- Click "Add People" and search for you collaborator's username and add them to the repo.
- This will send an invite email to your collaborator, who can choose to accept it.
- You may want to create an issue (on the Issues tab), which you want or need help for from your collaborator. 
    - The issue usually has both a title and a brief description of what your issue is and potentially what the next steps could be.
    - An issue can be anything you would like to communicate with (other) developers of the repo, a question about the code, bug reports, feature requests, etc.
    - Issues can also have task lists, links, images, etc. Often they also will include comments or follow up questions by developers. 
    - This is very useful for keeping track of project history and decisions, etc.

Person B (collaborator)
- Get the repository onto their local machine
    - Click on the green "Code" button, select SSH and copy.
    - on your local terminal, run: `git clone <paste url from github>`, this downloads the repo
        - you can now navigate to the new repo
        - if you an identically named repo locally already, you may need to remove or rename it first.
- Create a new branch for your changes: `git switch -c <branchname>`
    - this both creates and immediately switches to the new branch.
    - you can then add a file with to your local clone of the repo.
    - `git status`, you will see a new file.
    - add, commit, push your changes:
```
git add <filename>
git commit -m "commit message"
git push origin <branchname>
```
- If you go to GitHub, you can see the new branch. Often you will see a big green button "Create Pull Request", but this depends how soon after pushing you visit GitHub.
- On the Pull Requests tab, click on "New Pull Request". You can now see the changes that are part of this PR.
- In the description of the pull request, you can type `fixes #<issue number>`, which links to a specific issue and in case the PR is merged (we will cover this later), it will automatically close (mark as resolved) the issue.
- Click request review and choose person A.

Person A:
- Will get a notification that they got a review request.
- Visits the PR to see the changes suggested.
- Click "Review changes" green button, write a short message and say "Approve" (or could be "Request changes" or "Comment")

Depending on agreements within the collaboration, either the reviewer or the issuer of the PR can merge the PR and delete the branch.

The changes have now happened on the remote (online) repo, but not yet locally.

Your local repo is not automatically synchronized with remote.
`ls` will not show the old files, but not the new one
`git branch` will not show the new branches
`git log` will not show the commit from the collaborator
To synchronize your local remote (for person A) from the remote: `git pull`
`git log` will now show the commit from your collaborator as well.

You can track the changes on GitHub on the Insights tab.
You can also see the branch structure graph on the local terminal using `git log --oneline --graph`



### Questions from collaborative excercise:

#### How to prevent merge conflicts?
- merge conflicts will occur if two different branches change the same lines. Ideally try to always pull just before making your own changes and push asap so others will work off your changes rather than changing the same thing as you.
- communicate well with your collaborators about who is doing what
- merge conflicts will occur sometimes in real world situations. This is not necessarily bad. They are often easy enough to resolve.

### Real world code reviews
- you can communicate on specific lines or pieces of code
- you can have a back and forth about these
- be sure to "be nice". E.g., by
    - complimenting and/or thank your collaborator for their effort. 
    - use "we" rather than "you" when suggesting improvements

### How to go about collaborating when you're not listed as a collaborator on GitHub (external collaborator)
- remember that the repo is still public and visible and clonable to anyone
- e.g., you see that a feature is missing or there is a bug
- generally the first thing you want to do is open an issue, e.g., to check if the maintainers are already working on this or are aware.


Person A (external collaborator):
- opens an issue

Person B (maintainer):
- responds to issue and suggests to A to work on it

Person A:
- cannot create a branch because not officially collaborating (and generally does not have as many permissions on GitHub)
- instead you can create a fork of the repo. A fork is an exact copy of the original repo and GitHub still knows they are linked. However, any changes on the fork are listed on the original (and vice versa).
- locally, you can clone the forked repo (as you would with any other repo)
- enter your fork repo folder
- `git status` will show your general status
- in theory you can here work on main, because it is a fork, but it is still good practice to always create a new branch for new work (`git switch -c <branchname>`)
-  add code or text to new branch. Then `git add`, and `git commit` and `git push`. The work will now be pushed to _your fork_.
- If you create a PR from this, GitHub already assumes that you want to merge into the original repo rather than your forked repo. You can change this to your own fork if you want (but we don't in this case).
- You cannot assign reviewers to this, because you will not have access on the original repo

Person B:
- can self-assign themselves to the PR
- can do all the same reviewing procedures as mentioned above

Person A:
- Can see the reviewer's suggestions
- Can make the changes locally on their fork.
- Can then add, commit, and push their changes (to the remote fork).
- This automically will be added to the PR (PRs track branches on the remote).
- Note that external contributers cannot merge to the repo, and instead need to request a maintainer to do this.

Person B:
- Can re-review the PR.
- Can merge the PR if they agree.
- Note there is no button to delete the branch. This is because it is not Person B's branch to delete, as it only exists on the forked repo.


## 📚 Resources
- [Learn more about object-oriented programming](https://carpentries-incubator.github.io/python-intermediate-development/35-object-oriented-programming/index.html)
- 