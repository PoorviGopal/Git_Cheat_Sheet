# Git Step by Step Guide

## What is git?

- Git is a distributed version control system that helps manage and track changes in source code during software development. 

## Git Setup

**Download Git**: 
- You can download Git from [here](https://git-scm.com/downloads).

**Installation Steps**:
  - Run the Git installer.
  - Keep all options as default except:
    - Check the box to create a desktop icon for easy access.
    - Choose the main branch over master during installation (this is a more inclusive and considerate terminology).
    - Click the option for Unix-style line endings (recommended for cross-platform compatibility).

## Git configuration

- To set your Git username globally, use:
```bash 
git config --global user.name "YourUsername"
```

- To set your Git email globally, use:
```bash 
git config --global user.email "yourEmail@example.com"
```

- The git config --list command displays the current Git configuration settings.
```bash
git config --list
```

## Clear command

- To clear the teminal any time, use:

```bash
clear
```
--------------------------------------------------------------------------
## Here We Will Learn To Create Repo In Github First Then Clone & Edit it!
--------------------------------------------------------------------------

## Git Clone

- To copy a repository from GitHub to your local machine, use the `git clone` command followed by the repository link. Here's how:

```bash
git clone <repository-link>
```

- You can find the repository link on GitHub in the HTTPS section of the repository.

## Change Directory

- After cloning a repository, it's important to change your current directory to the newly cloned repository. 
- Use the `cd` (change directory) command followed by the directory name. Here's how:

```bash
cd <directory-name>
```
- Replace <directory-name> with the name of the directory associated with the cloned repository. 

## listing the files in directory

- ls command is used to list the files in the directory.

```bash
ls 
```
- The ls -a command is used to list files and directories in a directory, including hidden files and directories. 

```bash
ls -a
```
- Note that this won't work in VS code terminal, in VScode terminal use the ls -Force command.

```bash
ls -Force
```

## git status command

- When you run git status, Git will provide information such as:

  - On branch: Shows the name of the current branch you're working on.

  - Changes not staged for commit: Lists modifications in the working directory that have not been staged (added to the Git index) for the next commit.

  - Changes to be committed: Lists modifications that have been staged and are ready to be committed in the next commit.

  - Untracked files: Lists files in the working directory that are not tracked by Git.

```bash
git status
```

**Note:**

- There are 4 types of status:
  - **Untracked:** New files that git does not have track.
  - **Modified:** Files that were modified but not saved. 
  - **Staged:** Files that are ready for commit.
  - **Unmodified:** Files that are not changed or already commited.

  ## Add & Commit

- When making modifications, it's important to follow a two-step process to save the changes:

  **Step 1: Add**
  - This involves staging the changes you've made by using the `git add` command. It prepares the changes to be included in the next commit.

  ```bash
  git add <filename>
  git add index.html
  ```
 
 - If you want to add all files together then use the following command.

 ```bash
 git add .
 ```
  **Step 2: Commit**
  - After staging the changes, you commit them to the Git repository using the `git commit` command. This creates a permanent record of the changes with a meaningful commit message, making them a part of the project's history.

  - It is the record of change. 
  ```bash
  git commit -m"index.html file was added"
  ```

## Push

- The `git push` command is used to upload the local repository's content to a remote repository.

```bash
git push origin main
```

- origin is the default name for the remote repository. You can choose a different name if needed.

- main is the default branch on GitHub, which was previously named master before moving to more inclusive terminology.

- **Note:** If you plan to push to the same repository frequently in the future, you can set the upstream branch using `-u` option for a more streamlined process.

```bash
git push -u origin main
```
- `-u` sets the upstream repository and branch, so in future pushes, you can simply use git push, and Git will know the default remote repository and branch to push to.

--------------------------------------------------------------------------
## Now Let Us Create A Directory In Local Machine First Then In Github!
--------------------------------------------------------------------------
## Step 1: In Local Machine:

- **Folder creation :** Firstly create a folder in local machine.
- **init :** used to create new git repo
  ```bash
  git init
  ```
- **Changes :** You can add files, modify them, etc.
- **Add :** `git add .`
- **Commit :** `git commit -m"added html and css files`
- **Status :** `git status` 

## Step 2: To upload this repo In Github 

- **New Repo :** Create a new repo in github and do not create the readme.md file

## Step 3 : Gitrepo in Local Machine

- add the github repo in local machine and name it as a origin/anyName.
```bash
git remote add origin <-github-repo-link->
```

- Now verify wether repo is present in local machine or not.
```bash
git remote -v
```

- Now chek for the branch that you are present in.
```bash
git branch
```

- If you are in master branch then rename it with main by this command.
```bash
git branch -M main
```

- Now push the local repo to remote repo.
```bash
git push -u origin main
```
- **It is always better to to create a github repo first than vice-versa.**
------------------------------------------------------------------------------------------------------------------------------------------

## Git Branches commands:

- `git branch` : To check branch.
- `git branch -M main` : To rename branch.
- `git checkout < --branchName -- >` : To Switch Branch.
- `git checkout -b < --NewBranchName -->` : To create and switch to that new branch.
- `git branch -d <-- BranchName -->`: To Delete the branch.
  - **Note :** You Can't delete a branch when you are currently present in the same branch. To do that switch to some other branch.
---------------------------------------------------------------------------------------------------------

## Merging Code :

**Way1 :** Using Pull Request in Github.

- After pushing the code to one branch/ after making changes in the branch in github,
- Go to repository in github
- You will get a option compare and pull request.

**Way2 :**

- `git diff < --BranchName -->` : To Compare commits,branches,files & many more.
- `git merge <-BranchName(branch which you want to merge in current branch )->` : To Merge two branches.

**Note :**  - If you want to merge from branch_001 to branch_002 branch then,
              - First go inside branch_002
              - Then use this command `git merge branch_001`

**Merge conflicts** :

- If the changes found in same line, or if it is conflicting the we ill face this warining!.
- In this case we have to manually make changes in the code editor.

```bash
git merge main
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result
```

**Note :** Do not forget to stage and commit after merging the branch.

## Git Pull Command : 

- `git pull origin main` : Used to fetch the content from the remote repo to local repo.

## Undoing Changes : 

**Case 1 :** Staged changes
 - `git reset <-file name->`(To reset particular file.)
 - `git reset` (To reset all files.)

 **Case2 :** Committed changes (for one commit)
 - `git reset HEAD~1`

 **Case3 :** Commited changes(for many commits)
- `git reset<-commit hash->`(Do check `git log` for hash number of commit. (for ex:[92ef6eb4a6a12382da2358ac437228edaeabaaf7]))
- `git reset --hard <-commit hash->` (Only at this point you can see the changes in code editor.)

## Forking a Repository in Git

- A fork is a new repository that inherits code and visibility settings from the original "upstream" repository.
- Forking essentially creates a rough copy of the original repository.
- You have the option to visit someone else's repository and fork it to your account, enabling you to make modifications.
- To merge the changes made to their main branch, you need to send a pull request to the owner through GitHub, requesting them to review and potentially integrate your changes. 
