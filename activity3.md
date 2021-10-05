
git remotes link a local repository to a repository elsewhere (like github) through a uri.

We will now put the local git repository that you created in activity two and put it into a remote server

## What you will need:

* A text editor.  You can use any plain text editor you want
* A terminal where you can run git commands.
    * On macs, terminal is just fine  
    * On windows, you want git bash.  You can get this here: [https://git-scm.com/downloads](https://git-scm.com/downloads)
* A github account
* A local repository that you wish to put into github (like the one created by activity 2).  Note that the description applies to that particular repository.

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

