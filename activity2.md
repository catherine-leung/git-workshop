This activity will essentially look at how we did everything we did in activity 1 via the github interface using git commands locally.  When we write code we aren't going to do this inside the github editor... it doesn't suit our needs. Thus, it is essential that we understand how the same ideas we looked at (repo creation, commits, branch, merge etc.) can be applied to a repo we create locally.

## What you will need:
* A text editor.  You can use any plain text editor you want
* A terminal where you can run git commands.
    * On macs, terminal is just fine  
    * On windows, you want git bash.  You can get this here: [https://git-scm.com/downloads](https://git-scm.com/downloads)

## Create a new git repo 

* Make a folder (put it in a place you can easily cd into from the terminal)
* Open the terminal and cd your way into that folder
* Put the folder under revision control by using the command:
```git init```
* Execute the command:
```ls -a```
* Notice you now have a  **.git** hidden folder.  This folder is our repository... our data base. DO NOT modify the contents of your .git folder, ignore the fact that it is there
* Type the command:
```git status```
and you should see:
```
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```
* So you see a few things...
  * the branch you are looking at is master
  * The repo has nothing (at Initial Commit)

## Commiting a new file
* Using your text editor create a file containing
```
ABCDEFG
HIJK
QRS
```
* save it into the folder you made
* type the command:
```git status```
  * and you should see:
```
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	alphabet.txt

nothing added to commit but untracked files present (use "git add" to track)

```
* The above means that git is aware that you have an alphabet.txt file in your folder but that the file is not being tracked at all by the git database.
* To put into the database (ie into version control) you need to execute two commands:
```
git add alphabet.txt
git commit -m "added 3 lines of the alphabet song"
```
* Why two commands and not one?
  * git tracks changes in the state of the file system by having a history of commit
  * a commit is a change in one or ***more*** files
  * since a commit can involve multiple files, we need to indicate all the files that were changed for one commit
  * think of add as a "packing" command.  You are packing up all the things you want for a commit into one.
  * Once you finish adding it all together, you then commit it.
* Type the command:
```git status```
  * you should now see:
```
On branch master
nothing to commit, working tree clean
```
* The above means that git now knows about ever file in the folder.  There aren't any changes in any file that git doesn't have a record of
 

## Modify the file
* edit your file by
* insert the following line after "HIJK"
```
LMNOP
```
* save the file
* type the command:
```git status```
you will see
```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   alphabet.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
* This indicates that the version of alphabet.txt that git knows about is not the same as the one in your folder
* Use the add and commit commands to commit this change
```
git add alphabet.txt
git commit -m "added LMNOP"
```
* Again if you use ```git status``` you will see:
```
On branch master
nothing to commit, working tree clean
```
## Lets look at the history
* Use the command:
```git log```
* this will show all the commits for the branch along with its hash and commit messages

## Branches
* Lets make a branch called alpha1
```git branch alpha1```
* Look at where you are atm:
```git status```
  * you should see:
```
On branch master
nothing to commit, working tree clean
```
* To switch branches:
```
git checkout alpha1
```
* Now take a look at your status again:
```git status```
  * you should see:
```
On branch alpha1
nothing to commit, working tree clean
```
* To switch back to master you would use ```git checkout master```
* Switch into your alpha1 branch
* Modify your file by adding:
```Now I know my ABC's``` to the bottom of the file
* Commit this file to your alpha1 branch

## Look at the history
* Checkout each of your branches and look at the logs
* Note to see what branches you have:
```git branch -v```

## Look at Network graph
* Use the command:
```git log --graph```


## Merge
* In git you do not really have pull requests... you can pull code in, you can merge it... but the process is different
* To merge what is in alpha1 into master
* Make sure you are sitting in master
```git checkout master```
* Merge alpha1 into master:
```git merge alpha1```

## Branching, merging, and conflicts
* Be in the master branch: ```git checkout master```
* Create a third branch (suggest: alpha2): ```git branch alpha2```
* We should now have 3 branches (master, alpha1 and alpha2).  You can see if this is the case by using:
```git branch -v```
* Go into master branch ``` git checkout master```
  * In the alphabet.txt add the following(after the line ```QRS```:
```
TUV
```
  * save file
  * add and commit
```
git add alphabet.txt
git commit -m "added TUV"
```

* Go into alpha1 version
* Add to the end of alphabet.txt the following line:
```
Next time won't you sing with me
```
to the last line
  * save file
  * commit and add

* Go into alpha2 version
* In the alphabet.txt add the following(after the line ```QRS```:
```
WXY and Z
```
to the last line
  * save file
  * commit and add

* Look at the network graph at this point:
```git log --graph --all --decorate --topo-order --oneline```


Now, if you will recall, on github we were able to easily merge alpha1 to master but not alpha2.  The same thing will happen here.
* Lets start by merging alpha1 into master:
```
git checkout master
git merge alpha1
```
* This should be no problem
* Now lets try to merge alpha2 into master:
```
git merge alpha2
```
* this should create a merge conflict
* Using your text editor resolve your conflict in the same manner as you did on github
* save file
* add and commit



## Summary

git commands:

* git init (creates repo)
* git add <filename> (add files)
* git status (tells you what branch you are on and what files are known to git and which aren't)
* git log (shows the history of the branch we are in)
* git log --graph --all --decorate --topo-order --oneline (an ascii graph)
* git commit -m "<some text describing what you are committing>" (puts all things you added into a commit)
* git branch <branch name> (branch commands)
* git branch -v (list branches you have)
* git checkout <branch name> (go into a branch)
* git checkout <filename> (reverts your file to the version on the tip of branch you are sitting in)

