![MasterHead](https://github.com/geekybishwas/GitHub/blob/main/staging.png)
# About GiHub Commands

A brief description of how to create an SSH key, deploy it, add it to your Github account, commit it, and push it, along with detailed code explanations and examples.




## Generate an SSH Key

To generate an SSH key, open your terminal and run the following command:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
![App Screenshot](https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/original/2X/6/632297ac3a6d94df04a256c0aeb16e8461ef4da0.png)

## Add the SSH Key to SSH Agent

To ensure secure and convenient authentication, add your SSH key to the SSH agent. Run the following commands:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```
This starts the SSH agent and adds your private key to it.

## Deploy Your SSH Key on GitHub
Log in to your GitHub account.

 Click on your profile picture in the upper right corner and select "Settings."

 In the left sidebar, click on "SSH and GPG keys."

 Click "New SSH key" or "Add SSH key."

 Give your key a title (e.g., "My Laptop") and paste your public key (usually    found in ~/.ssh/id_rsa.pub) into the key field.

 Click "Add SSH key" to save it.

## Set your Name and Email

```bash 
git config --global user.name "your_github_username"
git config --global user.email "your_github_email"
```
![App Screenshot](https://practicalseries.com/1002-vcs/01-pages/03-04-install/02-images/fig-03-25-lrg.png)

## Check your name and email
For checking your name, type below command
```bash 
git config --global user.name
```
For checking your email, type below command
```bash 
git config ---gloabal user.email
```
![App Screenshot](https://github.com/geekybishwas/GitHub/blob/main/email_name.png?raw=true)
## Initializing Git Repository
Certainly! The ```git init``` command is used to initialize a new Git repository in your current working directory.

Open your terminal and type below command to initialize a git repository

```bash 
git init 
```
![App Screenshot](https://github.com/geekybishwas/GitHub/blob/main/git_init.png?raw=true)
To check if you are inside a git repository or not, type below command
```bash 
ls -la
```
If any ```.git``` file appears after entering ```ls -la```, the initialization of the git repository was successful, and this action will show any hidden files present in the repository.
![App Screenshot](https://github.com/geekybishwas/GitHub/blob/main/check_init.png?raw=true)

## git status
The```git status``` command displays the state of the working directory and the staging area.
```bash
git status
``` 
## Add, Commit
For adding a file to staging area , type below command
```bash 
git add file_name  //For adding one file at a time

git add . //For adding all present files to staging area

git commit -m "msg" //For commiting a change.

```
## Adding a remote repository
To add a new remote, use the ```git remote add``` command on the terminal, in the directory your repository is stored at.

The ```git remote add``` command takes two arguments:

*A remote name, for example, ```origin```

*A remote URL, for example, ```https://github.com/OWNER/REPOSITORY.git```

## Push , Clone

The ```git push``` command is used to transfer or push the commit, which is made on a local branch in your computer to a remote repository like GitHub. The command used for pushing to GitHub is given below.
```bash
git push 'remote_name' 'branch_name'
```

```git``` clone is a Git command line utility which is used to target an existing repository and create a clone, or copy of the target repository.

```bash
git clone https://github.com/OWNER/REPOSITORY.git
```
## git diff
The ```git diff``` command helps you see, compare, and understand changes in your project. 
```bash 
git diff  // Compare working tree with the staging area

git diff --staged // Compare staging area with the last commit
```
## git rm
The ```git rm``` command can be used to remove individual files or a collection of files.
```bash
git rm file_name //Delete from working directory and from staging area

git rm --cached file_name //Delete from staging area
``` 
## git checkout
Updates files in the working tree to match the version in the index or the specified tree.
```bash
git checkout file_name //Update one file at a time

git checkout -f //Update all file 
```
## Creating New branch
Master is a default branch , if you want to create a new branch then type
```bash 
git branch name_of_branch
```

## Switching to branch
For switching to another branch, type below command in terminal
```bash
git checkout name_of_branch
```

## Delete Git Repository
For deleting current git repository.
```bash
rm -rf.git
```
The above command will delete the initialized git repository.
![App Screenshot](https://github.com/geekybishwas/GitHub/blob/main/rm-rf.png?raw=true)

## For Multiple GitHub Account
To use two Git accounts (one for personal and one for work) on the same computer, you can configure Git to differentiate between the two accounts based on the repository. You'll do this by setting global and local configurations

### Step 1: Set Global Git Configuration (Default Account)
Set the global Git configuration for your personal account. This will be the default for all repositories unless overridden.
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Step 2: Set Local Git Configuration for Work Repository
For your work account, you will configure a local Git configuration on the specific repository. This allows you to use your work email and name for commits in that repository.
```bash
git config user.name "Your Work Name"
git config user.email "your.work.email@example.com"
```
This will override the global settings for this repository only.

### Step 3: Set SSH Configurations (if using SSH for authentication)
If you are using SSH to authenticate with GitHub or GitLab (which is common), you'll need to set up separate SSH keys for each account.
#### Generate SSH Keys for Both Accounts
#### 1.Personal Account SSH Key
```bash
ssh-keygen -t rsa -b 4096 -C "your.email@example.com" -f ~/.ssh/id_rsa_personal
```
##### 2.Work Account SSH Key:
```bash
ssh-keygen -t rsa -b 4096 -C "your.work.email@example.com" -f ~/.ssh/id_rsa_work
```

### Configure SSH to Use the Correct Key for Each Account
Edit the SSH config file (~/.ssh/config) to specify which key to use for each account.
```bash
# Personal Account
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_personal

# Work Account
Host github.com-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_work
```
### Step 4: Update Remote URLs to Use Aliases (for SSH)
Now that you've configured the SSH aliases, you'll need to update the remote URLs in your repositories to use these aliases.

1. For your personal repository, change the remote URL:
```bash
git remote set-url origin git@github.com:your-username/repository.git
```
2. For your work repository, change the remote URL
```bash
git remote set-url origin git@github.com-work:your-work-username/repository.git
```
This way, Git will use the correct SSH key based on the repository you are working on.



