+++
title = "Git TLDR"
+++

### Basics
```bash
git init . # Init git repo in current directory
git clone some_repo_url # Clone remote repo
git pull # Get changes from remote
git status # Show changes
git add . # Add changes to staging area
git add path_to_file1 path_to_file2 path_to_file3 # Add only the specified files to the staging area
git commit -m "message" # Commit and add commit message
git push # Push changes to remote repo
```

### SSH Setup
```bash
ssh-keygen # Create keypair

# Basic ssh config file for GitHub
Host github.com
    HostName github.com
    User git
    IdentityFile path_to_your_private_key_not_the_pub_file
    IdentitiesOnly yes
```


### Setup Name and Email
```bash
git config user.name "my name" # Adds your name to the repo you are in
git config user.email "my_email@howtogit.info" # Adds your email to the repo you are in 
git config --global user.name "my name" # Adds your name the global config
git config --global user.email "my_email@howtogit.info" # Adds your email to the global config
```


### Branches and Merging
```bash
git branch # List local branches
git branch -r # List remote branches
git branch -a # List all branches
git checkout -b new_branch # Create branch with name new_branch
git checkout some_branch # Switches to branch with name some_branch

git merge some_branch # Merge some_branch into current branch
```
