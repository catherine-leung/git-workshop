This activity will essentially look at how we did everything we did in activity 1 via the github interface using git commands locally.  When we write code we aren't going to put all our code in the github web editor. it doesn't suit our needs. Thus, it is essential that we understand how the same ideas we looked at (repo creation, commits, branch, merge etc.) can be applied to a repo we create locally.  This activity will take look at how the concepts from activity 1 applies to local repositories and also add onto it the idea of **remotes**.

## What you will need:

* A text editor.  You can use any plain text editor you want
* A terminal where you can run git commands.
    * On macs, terminal is just fine if you have your command line tools.  You can check by typing the command:
      ```git```
      into the command line
    * On windows, you want git bash.  You can get this here: [https://git-scm.com/downloads](https://git-scm.com/downloads)
* a github account

## Create a new git repo locally

* Make a folder (put it in a place you can easily cd into from your terminal/commandline)
* Open the terminal/gitbash and cd your way into that folder
* Put the folder under revision control by using the command:
```git init```
* Execute the command:
```ls -a```
* Notice you now have a  **.git** hidden folder.  This folder is our repository... our data base. DO NOT modify the contents of your .git folder, ignore the fact that it is there

## Commiting a new file
* Using your text editor create a file containing
```
ABCDEFG
HIJK
QRS
```
* save it into the folder you made for your repo
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
 
## Push into github

This next step is not the same as activity 1. We will push this repository into github as a new repository.

*  Go to github.com
*  Use the + symbol to create a new repository

![newrepo](https://user-images.githubusercontent.com/1699186/221596506-9a2b8014-6984-4219-b1ae-3276f8f9133f.png)

*  Create a blank public or private repo but do not initialize with a readme.  Also, unless you have setup an ssh key (you will remember if you did..its rather lengthy process), make sure you are on the https settings
*  
![activity2reposetting](https://user-images.githubusercontent.com/1699186/221623049-354abf96-6498-427e-a0ee-3848bdbb5c2a.png)

* When you are done, you should see a page that looks like the following.  Copy the 3 commands in the bottom block and paste it into the terminal/commandline and hit return to execute it.

![emptyrepo](https://user-images.githubusercontent.com/1699186/221624716-64ca8bd7-51e5-4870-a72d-3807f939c0b9.png)


* Refresh the browser page.
* Look to see if you have same content as local



## Modify the file

In your local computer

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
On branch main
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
git commit -m "added LMNOP, removed HIJK"
```
* Again if you use ```git status``` you will see:
```
On branch main
nothing to commit, working tree clean
```

## Modify the file again
* edit your file by
* insert the following before "LMNOP"
```
HIJK
```
* save the file
* type the command:
```git status```
you will see
```
On branch main
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
git commit -m "added HIJK"
```
* Again if you use ```git status``` you will see:
```
On branch main
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
On branch main
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
* To switch back to main you would use ```git checkout main```
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
* To merge what is in alpha1 into main
* Make sure you are sitting in main
```git checkout main```
* Merge alpha1 into main:
```git merge alpha1```

## Branching, merging, and conflicts
* Be in the main branch: ```git checkout main```
* Create a third branch (suggest: alpha2): ```git branch alpha2```
* We should now have 3 branches (main, alpha1 and alpha2).  You can see if this is the case by using:
```git branch -v```
* Go into main branch ``` git checkout main```
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


Now, if you will recall, on github we were able to easily merge alpha1 to main but not alpha2.  The same thing will happen here.
* Lets start by merging alpha1 into main:
```
git checkout main
git merge alpha1
```
* This should be no problem
* Now lets try to merge alpha2 into main:
```
git merge alpha2
```
* this should create a merge conflict
* Using your text editor resolve your conflict in the same manner as you did on github
* save file
* add and commit

## Push it all to github.

To push all these changes into github:
```
git push origin
```

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
* git push <remote name> (pushes your local changes into a remote)

