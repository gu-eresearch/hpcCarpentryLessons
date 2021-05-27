---
layout: default
---

You know when you are working on a document/script/analysis and you have a bunch of different files saved. You've saved multiple files because you have changed the wording or analysis, and want to keep a version before the change in case you decide to go back. At a later date you decide that you like a previous version, or your code does not work anymore, you need to go back to when it did. So you try to go back through your files to find that change, 2 days later and your still searching..............

Git is a version control software specifically designed to save a version each time you make changes, you can rewind to an older version, or go through the change files to ideantify what you changed.

![versionControl](/assets/images//phdComicFinal.gif)

Or, maybe your part of a team where multiple people are working on the same file. You want to do your part, but you need to wait until a collaborator finishes and emails you their finished version. 
You could just do your part and then at the end copy and paste everyones changes in a single file......

There is a better way. The version control software git helps keep track of each individuals contribution (on a branch), and then automatically merges the individual's branches into the 'master'.

![WhatIsGit](/assets/images/WhatIsGit.png)


Git is comprised of 2 distinct repositories. There is the git software installed locally on your computer, this repository tracks the changes you make to files. Then there are external repository hosting services such as github, gitlab, bitbucket ect. These are useful when working in groups as they act as a central repository for everyone to push their individual changes to.

## External hosting services for version control

Git will control the changes made the your local repository, i.e. on your computer. However, when working in a group its usefull to have a central repository where everyones changes can be stored and merged into a master document.

Github is the best known open hosting service: https://github.com/

Did I mention that its open!!! It is an amazing resource for finding code and for tutorials.
If we search "python statistics", We get a list of packages, tutorial and code that relate to python and statistics. You can fork (get your own copy) of anyones code that you find. This can be a good starting point when developing you own code.

![github_search](/assets/images/github_search.png)

**IMPORTANT** Just remember that everything you put on github can be seen by everyone. Don't add any sensitive or private information. And **NEVER** add passwords!!!

If you would like to use a private and secure hosting service, Griffith has Gitlab, which is similar to github, except that your projects are private: https://gitlab.rcs.griffith.edu.au/users/sign_in . Again, Don't add passwords. To get an account email eresearch-support@griffith.ed.au and request a gitlab account.


## What are the steps to use git

1. Configure your git environment, this only needs to be done once.

2. Each time you start a new project, you need to initiate git. This creates a local folder that stores all the track changed information relating to the project.

3. 'add' and 'commit' code to git. This will create a "snapshot" in your local repository of the files and track changes showing everthing that has been added or removed.

If using an external repository

4. Create a new external respoitory

4. 'push' and 'pull' to an external repository. Fancy git words for uploading and downloading to an external git repository. **Note:** an external repository is not required for git.

5. If working in a group, you may need to 'merge' and 'branch'.

![git](/assets/images/git.png)
source: https://medium.com/@chonglee30/git-overview-30618e81eb77

If you haven't already done so, create a Github account and add a new repository.

![newRepo](/assets/images/newRepo.png)

## Lets git
### Initiate git locally for a new project
Git is a standalone programme, however, you can also use it from within many programming interfaces, such as R studio, spyder and jupter notbooks.

Today we will be using it through a bash terminal. Use terminal for Mac or GitBash for windows.
First we will need to configure git, instructions are <a href="https://swcarpentry.github.io/git-novice/02-setup/index.html" target="_blank">here</a>

Next we can initiate git for a new project. Once initiated, git will track all changes within the folder/directory that you initiate in.
Use the command 'cd' to change directories to your folder that you want to initiate git in. To get the directory/path in your terminal type cd, then on Windows open file explorer (finder on a Mac) go to the folder you would like to git initiate, and drag the folder into terminal, the directory or path to that folder will appear. Press enter. 
Use the 'pwd' command to print your working directory, this is used to check that you are in the correct folder.

```bash
cd /Users/s1234567/Documents/SWC/python     
pwd     
~/Documents/SWC/python    
```


Now you can initiate a git repository using the 'git init' command. This creates the version control folder that is stored locally on your computer that will track all changes you make.

```git
git init      
hint: Using 'master' as the name for the initial branch. This default branch name       
hint: ................       
hint: ................       
hint: ................       
Initialized empty Git repository in /Users/s1234567/Documents/SWC/python/.git/     
```


A .git file has been created in your folder. The . in front of the name means its a secret folder, you will not see this folder in your finder or window explorer. 

In the bash window, you can use the bash command 'ls -a' to view this secret .git folder.

```bash
ls -a        
./ ../ .git/       
```

You are ready to go now, the following will set up an external repository, this is not a requirement. If you don't want to set up an external repository you can skip this section.

### Link the local git to an external repository
Copy the repository URL as shown below, you will need this to link to a remote repository. 

![repoURL](/assets/images/repoURL.png)

The 'git remote add origin' command will link the external repository to the git folder on your computer that has all the track change information, it is where you will push and pull.

```
git remote add origin https://github.com/yourRepository/gitTutorial.git
```


Use the 'git remote -v' command to check the location of the remote repository.

```
git remote -v
origin  https://github.com/yourRepository/gitTutorial.git (fetch)
origin  https://github.com/yourRepository/gitTutorial.git (push)
```


Your ready to push and pull to a remote repository. 


### Git add, commit and push

Open the python spyder console. In a new script add a hashed out comment. Save it as a python file (i.e. .py) in your folder that you initiated the git project in. 

```python
# How to read tabular data into python dataframes using the pandas library
```

Now to create a staged snapshot that tracks the changes in git I need to run the command 'git add .', the . signifies that all new changes should be added, you can provide the names of individual files if you only want to include certain ones. This is only staged, i.e. it hasn't been saved yet.

```
git add .
```


Now save the snapshot and track changes using the command 'git commit -m "a short message about what has been added"'. The short message is important, this will be used to identify this snapshot, you will need it to make sense in a month or even a years time.

```
git commit -m 'initial script for reading dfs using pandas'
[master 9282558] initial script for reading dfs using pandas
 1 file changed, 1 insertion(+)
 ```


Now we have saved the change to our local git folder. Next we can push those changes to the external git repository using the 'git push origin master' command.

```
git push origin master
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 8 threads
Compressing objects: 100% (13/13), done.
Writing objects: 100% (16/16), 508.06 KiB | 18.14 MiB/s, done.
Total 16 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/yourRepository/gitTutorial
 * [new branch]      master -> master
 ```

Go to you external git repository, the changes will be there. 

![githubPush](/assets/images/githubPush.png)


## Challenge 
What do the git commands add, commit, push and pull do?
Talk about it with your neighbour for 5 minutes

<details><summary><h2>Solution</h2></summary>
<p>
<ul>
  <li>'add' will stage a snapshot of the files, including a track of all the changes made to the files.</li>
  <li>'commit' will save the snapshot and track changes into the .git folder you initiated on your local computer.</li>
  <li>'push' will push the snapshot and tracked changes to your external repository.</li>
</ul>
</p>
</details>



## Challenge
What is the code to add, commit and push a change

<details><summary><h2>Solution</h2></summary>
<p>
<pre>
<code class="language-git">
git add .
git commit -m "print out equation and answer"
1 file changed, 1 insertion(+)
</code>
</pre>
If you want to push to an external repository:<br>
<pre>
<code class="language-git">
git push origin master
[master 110edb3] print out equation and answer
1 file changed, 2 insertions(+), 1 deletion(-)
git push origin master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 305 bytes | 305.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/yourRepository/gitTutorial.git
   b7f021d..110edb3  master -> master
</code>
</pre>
</p>
</details>


Add a line to import the pandas library to your python script.

```python
# How to read tabular data into python dataframes using the pandas library     
          
import pandas      
```

Now add and commit the change to your local git repository.

```git
git add .     
git commit -m "added pandas library"        
[master 9282558] added pandas library         
1 file changed, 1 insertion(+)         
```

Now you can see a log of all the snapshots that have been committed locally by running the 'git log' command

```git
git log    
commit 110edb3adab86ca715e83368a9052e3fb187ca8d (HEAD -> master, origin/master)    
Author: Brett Parker <b.parker1@griffith.edu.au>    
Date:   Tue May 11 12:46:44 2021 +1000     
      
    initial script for reading dfs using pandas     
    
commit b7f021d2631565e47d0fe472975e73d921b22fae    
Author: Brett Parker <b.parker1@griffith.edu.au>    
Date:   Tue May 11 12:44:40 2021 +1000     
     
    added pandas library       
    "    
```

To see the change of a specific commit use the command 'git diff' and the tag to the specific commit.

```git
git diff b7f021d2631565e47d0fe472975e73d921b22fae
```

![gitDiff](/assets/images/gitDiff.png)

If you have an external repository you can go to it to see the changes.

## Git pull
'git pull' will pull changes that another person has pushed to the external repository.

Type the command 'git pull' and git will download everything in the remote repository.

```git
git pull origin master     
hint: ......................     
hint: ......................    
From https://github.com/yourRepository/gitTutorial    
 * branch            master     -> FETCH_HEAD    
Updating 2c5a4d0..6b6981c      
Fast-forward    
 simpleCode.py    
 1 file added, 0 insertion(+), 0 deletion(-)    
(base) s1234567@pc152233-osx:$   
```

So what happened. You will now have a file named simpleCode.py that was pulled from the repository.
