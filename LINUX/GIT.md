Linux
=====

GIT HUB
-------

#### Add new and updated files to Repo
git add -A

#### Commit changes to local
git commit -m “Update Message”

#### Push changes to remote
git push

#### Commit all new changes and push in one command
git commit -a -m "Message goes here" && git push

#### Create new BRANCH
git branch <BRANCH-NAME>

#### Checkout branch
git checkout <BRANCH-NAME>

#### Create new branch and checkout in one command
git checkout -b <BRANCH-NAME>

#### Publish new branch to server
git push --set-upstream origin <BRANCH-NAME>
or
git push -u origin <BRANCH-NAME>

#### Retrieve and checkout new branch
git pull
git checkout -t origin/<BRANCH-NAME>



## Common usages and options for Git Commit

* `git commit`: This starts the commit process, but since it doesn't include a -m flag for the message, your default text editor will be opened for you to create the commit message. If you haven't configured anything, there's a good chance this will be VI or Vim. (To get out, press esc, then :w, and then Enter.)
* `git commit -m "descriptive commit message`: This starts the commit process, and allows you to include the commit message at the same time.
* `git commit -am "descriptive commit message"`: In addition to including the commit message, this option allows you to skip the staging phase. The addition of -a will automatically stage any files that are already being tracked by Git (changes to files that you've committed before).
* `git commit --amend`: Replaces the most recent commit with a new commit


## Merging and deleting branches

#### Merge completed branch into main
git checkout main
git merge DataPoolAsArrays

#### Push the merge to server
git push

#### Delete branch locally
git branch -d DataPoolAsArrays

#### List local branches (to check deletion)
git branch  
Delete remote copy of branch  
git push origin --delete DataPoolAsArrays  

### Cloning

#### Clone Remote Repository:
Open terminal/GitBash into the directory where you want the put the repository  
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY

### GIT IGNORE

#### Remove already tracked file:
Before adding .ignore file run this in the terminal:  
`git rm --cached <FILENAME>`  
Example:  
`git rm --cached *.sqlite`  
Then add *.sqlite to .ignore file  


