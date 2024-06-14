# Understanding Git and git commands


Install git bash @ https://git-scm.com/downloads


# Git commands


## When you install Git-bash, the first thing you should be doing is setting up your user details

git init # To create a local Git empty repository on the current working directory
git config --global user.name "enter user name" #configure username for the git user
git config --global user.email "enter email"  # configure user email for the git user
git config --global color.ui auto   #set automatic command line coloring for Git for easy reviewing
git config -h # GEt help on possible git config commanda and description
git config --global -l  ## To list details about the git user


## Git Workflow ##


##### Before running the commands below, ensure your have created a new file and put in some content.

git init # To create a local Git empty repository on the current working directory.
git status # provides the status of your local repository. This will display all untracked and tracked files.
git add <file name>  # Add files into your staging area. This enables git to start tracking chnages to the files
git add --all or git add . # To add all files in current directory
git commit -m "pass your own commit message"  # this takes a snapshot of the your local repository that way you can revert to previous snapshots/commits. This in another sense is adding the changes to the history of your repo
git commit -a -m "pass your own commit message"  # This command with stage all changes and commits at the smae time
git push -u origin < branch-name >  # push committed changes to remote repository

### Other Git commands ###

git rm --cached <file name > # to untrack files

### To untrack files, create a file called .gitignore and list files and folders you want to ignore by listing the file or folder name

git rm < file name > # to delete file form directory
git status
git add .
git clone -b <branch name> <repos url> # To copy codebase from remote to local working area
git restore --staged <file name>
git restore < file name > to restore file back to the directory 
git mv <old file name> <new file name> # to rename file name
git log  # It will give all commit ids.
git log -2  # It will display only 2 commit ids.
git log --oneline # to display brief summary of your commits
git revert <commit ID>
git revert --abort To abort and get back to the state before "git revert"
git commit --amend -m "New commit message"  # To edit the commit message of the most recent commit
git log -p # This command will print out the details of all commit chanages including changes to file or folder content
git diff # This will show what differences have been made from the previous commit
git diff < branch A > < branch B > # Show difference of what is in branch A that is not in branch B


#######################
# git branch commands #
#######################


git branch < branch name > # To create new branch
git checkout -b <branch name> # create a new branch and switch user to new branch
git switch <branch name> # switch from one branch to another
git checkout <existing branch name>
git branch # to list branches current branch will be marked by asterix (*)
git merge -m "merge message" <branch to merge>
git branch -d <branch name> to delete a merged branch
git branch -D <branch name> to delete a branch


#########################################
# Integrating local repo to remote repo #
#########################################


git remote add <remote-name> <remote repo url> # The git remote command lets you create, view, and delete connections to other repositories
git remote # List the remote connections you have to other repositories.
git remote -v # Same as the above command, but include the URL of each connection
git remote rename <old-name> <new-name>  # Rename a remote connection from ＜old-name＞ to ＜new-name＞
git remote show < name of remote e.g origin > # It will give the information on a particular remote (here origin is the remote name)
git remote rm <name> # Remove the connection to the remote repository called ＜name＞
git branch -r # To list remote branches in gitlab/gitlab/bitbucket
git fetch # fetch changes from remote repository to your local repository,
# This also downloads all of the required commits and files from the other repository
# Fetching is what you do when you want to see what everybody else has been working on
# It will download the remote content but not update your local repo's working state, leaving your current work intact.
git switch main # To switch to main branch existing in remote repo
git merge -m "merging master to main" master --allow-unrelated-histories # Mergemaster to main branch. Make sure to be in the main branch before running the command
git commit -a -m "message" # To add any changes in your local and then commit it to your local repo
git push origin --all # This will push changes from all branches in your local repo to the remote repo
git fetch <remote> # Fetch all of the branches from the repository. This also downloads all of the required commits and files from the other repository
git fetch <remote> <branch>  # Same as the above command, but only fetch the specified branch.
git fetch --all # A power move which fetches all registered remotes and their branches
git fetch --dry-run # The --dry-run option will perform a demo run of the command. It will output examples of actions it will take during the fetch but not apply them.
git merge # to apply fetched details to your local repository  
git pull <remote> <branch name> # The git pull command is used to fetch and download content from a remote 
# repository and immediately update the local repository to match that content
# The git pull command is actually a combination of two other commands, git fetch followed by git merge


############
# Git Tags #
############

## tags are ref's that point to specific points in Git history. 
## Tagging is generally used to capture a point in history that is used for a marked 
## version release (i.e. v1.0.1). 
## A tag is like a branch that doesn’t change. 
## Unlike branches, tags, after being created, have no further history of commits.
# Git supports two different types of tags, annotated and lightweight tags. 
## Lightweight tags and Annotated tags differ in the amount of accompanying meta data 
## they store. 
# for more details, follow this link https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag

git tag # Check existing tags
git tag <tag-version e.g v1.0.0> # Creates a Lightweight tag.

# Lightweight tags are essentially 'bookmarks' to a commit, 
## they are just a name and a pointer to a commit, 
## useful for creating quick links to relevant commits.
  
git tag -a <tag-version e.g v1.0.0> -m "tag-message" # Annotated tags are stored as full objects in the Git database. 

## They store extra meta data such as: the tagger name, email, and date. 
## Similar to commits and commit messages Annotated tags have a tagging message.

git tag -a <tag-version e.g v1.0.0> <commit ID> -m "tag-message" # tagging a specific commit
git tag -d <name of tag> # Deletes specific tags
git tag -d $(git tag -l) # Deletes all tags    git tag -d v1.0.0 v2.0.0
git push <remote> master <tag-name> # Push code changes with specific tags
git pull origin master2 v1.0.0 # Pulling code base with a specific tag
git push origin master --tags Push code changes with all tags
git clone --branch <tag_name> <repo_url>
