
This activity introduces participants to working with remotes.  When we use git, we are rarely ever working entirely on our local machines or entirely on github.  Usually it is a mix of both.  This next activity will introduce you to working with remotes.


## What you will need:

* A modern web browser
* access to github codespace (this is now standard)


## Cloning an Existing Repo



## Preparing a place to put repo in github

* On github, start by creating an empty repository:
   * DO NOT initialize that repository with any files.. we want to put our current repository into github.

once you do that, github sets up a nice page showing you the commands to put up your current repository... lets go over what it means:
```
git remote add origin someuri
```
The word ```origin``` is a name you are using.. it doesn't have to be origin, you can call it whatever you want.. its just a name
The ```someuri``` is the uri that refers to the repository on github.  

Thus, what you are doing is referring to the remote repository on github as origin

After you run this line, you will be able to see the remote shorthand with the command:

```
git remote -v
```
***

```
git branch -M main
```

renames the local branch main

***

```
git push -u origin main
```
pushes the entire branch into github

***

Now, lets get our repository and put it into our matrix accounts...

* Log into matrix
* Clone your repository from github.

Notice that there is a remote in this directory already setup to github so there is no need to do it ourselves.

Make a small change to your file and put it into github:

* edit the file on matrix and save
* add and commit the file
* push the file into github (```git push origin```)

Now, if you look on github you have this change... but this change doesn't exist on your local computer. 
To get this update, do a pull on your local computer

```
git pull origin
```

