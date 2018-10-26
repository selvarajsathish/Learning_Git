## **Initialize git repo in local:**

	$ mkdir learning_git

	$ cd learning_git

	$ git init

	$ git status

## **Creat new file and add to staging:**

	$ vi hello.py
		## hello.py
		print('hello Git!')

	$ git status

   To move new to staging area.

	$ git add hello.py

	$ git status

   Now Git knows about hello.py and lists it under changes to be committed.

## **Committing file:**
	for commit the changes we use git commit command with "-m" option for metion short info about that file changes.

	$ git commit -m "creating hello.py"

	$ git status
   
   it shows working directory clean.

## **.gitignore**
	We will see that there are a bunch of files that show up in the untracked section and that we want Git to just not see. Then we use .gitignore file for ignoring other than sourcecode file or unwanted file.

	$ vi .gitignore
		## .gitignore
		*__pycache__
		*.pyc
		*.txt

## **git log**
	Git log shows the history of the commits that we have made up to this point.

		$ git log


# **Branching Basics:**
	To create new branch, if below command executed from master or any other branch new branch will have all the commits of parent branch commit where HEAD pointing.

		$ git checkout -b my_new_feature

	we existing commits by using below commands,

		$ git status

		$ git log
## **Merging :**
	If other branch ahead of the current branch then it will just do a fast-foward merge and place those new commits on this branch.

		$ git merge my_new_feature

## **Rebasing :**
	we can take all the changes that were committed on one branch and replay them on another one.

		$ git rebase master

It works by going to the common ancestor of the two branches, getting the diff introduced by each commit of the branch we’re on, saving those diffs to temporary files, resetting the current branch to the same commit as the branch we are rebasing onto, and finally applying each change in turn.

## **Cherry-Picking:**
	with cherry-picking we specify exactly which commits we want to rebase. The easiest way to do this is just specifying a single SHA of commit.

		$ git cherry-pick 4a4f4492ded256aa7b29bf5176a17f9eda66efbb



# **Working with Remote Repos:**
----------------------------
	we have only four major Git commands which actually talk to remote repos:

		clone
		fetch
		pull
		push

## **Clone:**
	Git clone is the command we use when we have the address of a known repository and  want to make a local copy.

		$ git clone https://github.com/selvarajsathish/Learning_Git.git


## **Fetch:**
	When we clone a new repo, Git doesn’t just copy down a single version of the files in that project. It copies the entire repository and uses that to create a new repository on our local machine.
	Remember that every branch that existed on the remote when we cloned the repo will have a branch in remotes/origin.
	Now that we know about the remotes/origin branches, All fetch does is update all of the remotes/origin branches. It will modify only the branches stored in remotes/origin and not any of we local branches.

## **Pull:**
	Git pull is simply the combination of two other commands. First, it does a git fetch to update the remotes/origin branches. Then, if the branch we are on is tracking a remote branch, then it does a git merge of the corresponding remote/origin branch to wer branch.

		$ git pull 

	sometimes we with rebase to get only the changes from server respective of local branch.

		$ git pull --rebase

## **Push:**
	Push sends the info about the branch we are pushing and asks the remote if it would like to update its version of that branch to match wers.
	Generally, this allows to we pushing wer new changes up to the server.

		$ git push <path>

		$ git push origin/<branch name>

## **Rename a local and remote branch name in git:**
	1. Rename wer local branch.
		If we are on the branch we want to rename: 

		$ git branch -m new-nam

		If we are on a different branch:

		$ git branch -m old-name new-name

	2. Delete the old-name remote branch and push the new-name local branch.

		$ git push origin :old-name new-name


## **Credits:**

https://realpython.com/python-git-github-intro/                                                                                         
https://git-scm.com/book/en/v2                                                                                                           
https://github.com/jima80525/github-playground/blob/master/git-commands.md