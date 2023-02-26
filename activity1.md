# Learning about git terminology through github

In this first activity we will learn some basic git terminology by creating repo (short for repositoy) on github.

## What you will need:
* A web browser
* A github account

## Create a new git repo 

* log into github
* click + sign at top right and select new repo
* choose a name for this repo  (suggestion: gitwsrepo1)
* if your account is a free account, you must make this repo public as some of the features listed below are not available in private repos to free accounts
  * check the the "Initialize with a README" checkbox
  * hit create button

## What you get with each repo

Once you have a repo in github, there are a number of things that come with the repo.  Notice the row of tabs at the top of the screen.  The first tab name code is essentially every file your repo tracks.  Currently there is a single README.md file.  The other tabs are:

* issues
* pull requests
* project
* wiki
* security
* insights

(these have changed over time and may change again in future).  A repo in other words can help you organize a project, provide space for feedback, documentation, and some basic analytics.  For this first activity we will mostly just be using  the code tab

## Commiting a new file
* Make sure you are in the code tab
* Hit the "Add file" drop down and choose "Create new file"
* give the file a name (suggestion: alphabet.txt)
* Edit the file by adding the following to it:
```
ABCDEFG
HIJK
QRS
```
* hit the commit new file button (keep the default Commit directly to the main branch setting in the radio buttons)

This file is now known to git.  git is storing a version of this file

## Modify the file
* click link for the file you created in the last step 
* hit the pencil icon in top right to edit the file
* insert the following line after "HIJK"
```
LMNOP
```
* delete the line HIJK
* then click commit changes button

## Modify the file again
* click link for the alphabet.txt file
* hit the pencil icon in the top right
* insert the following before "LMNOP"
```
HIJK
```
* click commit changes button

## Lets look at the history
* click on the file in code tab
* click the history button (top right)
* notice there are two commits each has a 7 digit hex code associated.
* This 7 digit hexcode is actually the beginning of a much longer hex code that uniquely identifies each commit.  These are hash codes.
* notice you can look at the state of each file in each commit
* notice you can see what was changed from the previous commit in the history
* ```+``` and green indicate additions
* ```-``` and pink indicate deletions

## Branches
* A key idea that makes git unique is the ease with which you can make and merge branches
* A branch is made when you want to add something but you aren't totally sure if you want to keep it
* By default when you create a repo in github, you create a branch named main
  * You do not have to keep this branch name...there isn't anything special about it
* notice at the top left there is a dropdown with the word ```main``` in it.  This is the branch you are looking at.
* more accurately it is the most recent commit within that particular branch
* To create a branch inside github click the dropdown and type a name for your new branch (suggest: alpha1)
* You can click between the two branches by using the dropdown button
* Make sure you are on your new branch (ie NOT main)
* Edit the file by typing: 
```Now I know my ABC's``` to the bottom of the file
* Commit this file (the default setting should be committing file to new branch

## Look at the history
* At this point take a quick look at the history
* in the main branch there will be one commit less than the other branch

## Look at Network graph
* In the insight tab, click on network
* The network graph is a visual representation of your branches

## Merge, Compare and pull request
* Go back into your code tab
* At this point you should have a bar with a green button at top that says "compare and pull request"
* This is because github realizes you have something in a branch that is different from main and is asking if you want to create a request to review and and accept the changes
* Hit this button
* Now, this button does not actually merge the files into main...it creates a pull request.  In otherwords it creates a request to ask if you want to merge it back together.
  * You can also make your own pull request even without that button, just go to pull request tab and hit new pull request
  * Notice the two buttons at the top.  One is labelled base.  The other compare.
  * Base is where you want the changes to go...which branch do you merge to
  * Compare is the changes you want to pull into the Base ... which  branchdo the changes come from
* In the pull request tab, you will now see merge pull request button
* Click this button to pull the changes in your second branch back to main
  * Confirm the merge
  * DO NOT DELETE THE BRANCH

## Branching, merging, and conflicts
* Be in the main branch
* Create a third branch (suggest: alpha2)
* In the **main** version commit (after the line ```QRS```:
```
TUV
```
* In the **alpha1** version commit:
```
Next time won't you sing with me
```
to the last line
* In the **alpha2** version commit (after the line ```QRS```):
```
WXY and Z
```
* Now lets go to the pull request tab and start a new pull request
* Use main as the base
* for compare switch between your two branches.... you will notice that alpha1 is followed by green checkmark and the text ```able to merge```.  If you switch to alpha2 it is followed by red X and the text ```can't automatically merge```
* Essentially this is github saying that it knows how to put together main and alpha1.  It can figure this out on its own.  However not main and alpha2 that it needs help with.
* Create a pull request to main from alpha1
* Create a pull request to main from alpha2 (yes even though it can't be done automatically)
* Lets merge in the easy one first, go to the pull request that can be automatically merged and merge it.
* In the other pull request hit the ```Resolve conflict``` button
* When you do this, you will open an editor that has what you wrote plus a number of conflict markers like the following:
```<<<<<<< alpha2```
* These conflict markers mark the places where git got confused.  It basically can't figure out what do...
  * do you want to keep the version in alpha2 and erase version in main?
  * do you want to keep the version in main and erase version in alph2?  
  * do you want to keep both?
  * do you want to switch the order?
* Your job is to figure out which parts of each version you keep and the ordering of the text.
* Edit the file so that it is correct and remove all the lines containing the conflict markers.  Hit mark as resolved button
* hit the commit merge button
* finish the pull request now that it can be automatically merged

## Summary

Here are the ideas and terms we looked at:

* repository
* commit
* branch
* merge
* conflict
* pull request
* history
* uniquely identifying hash codes

