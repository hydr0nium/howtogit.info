+++
+++
# How to Git

You are probably here because one of your coworkers or friends has send you this page when you told them you know nothing about git. For you and anyone else that found their way here, this is the right place.

Let's start with the basics.

### What is git? [🔗](https://howtogit.info/#what-is-git-link)

git is what is called a version control software, basically just a way to track what and who did something with files. git first and foremost is a commandline tool but it can often be used in your favorite code editor or IDE like VSCode. It is important to note that git is different from GitHub and GitLab.

### What is GitHub / GitLab? [🔗](https://howtogit.info/#what-is-github-gitlab-link)

GitHub and GitLab are cloud storages for your git managed files. They have some features that enhance the way people can collaborate like pull-request and pipelines.

### What is a repository (repo)? [🔗](https://howtogit.info/#what-is-a-repository-repo-link)
A repository or repo for short is just the directory your files are managed in. You can think of it as the box all your files / code live in. Are repo has always a .git folder in its root directory.

### How do I create a repo? [🔗](https://howtogit.info/#how-do-i-create-a-repo-link)
There are two ways to create a git repo. First on GitHub or GitLab and then locally. In both cases you need to somehow 'connect' your local repo to the remote repo.

### Creating a repo on GitHub [🔗](https://howtogit.info/#creating-a-repo-on-github-link) 
To create a repo on GitHub you click on the top right '+' and then 'New repository'. After answering some questions like, the name of the repo, or if it should be public the repository is created.

### Creating a repo locally [🔗](https://howtogit.info/#creating-a-repo-locally-link)
To create a git repo locally navigate to the folder you want to create the repo in then run
```bash
git init .
```

### How do I download a repo from GitHub / GitLab? [🔗](https://howtogit.info/#how-do-i-download-a-repo-from-github-gitlab-link)
You can either just clone the repo from GitHub / GitLab which automatically connects the local and remote repo together. On GitHub you can do this with the blue 'Code' button. Then choose SSH or HTTPS (with HTTPS you can only pull but not push any changes). Note that SSH requires a ssh-key to be setup. 
```bash
git clone https://github.com/someuser/somerepo.git # Clone the repo to your local PC
```

### How do I add my local repo to the remote repo? [🔗](https://howtogit.info/#how-do-i-add-my-local-repo-to-the-remote-repo-link)
If you created a local and a remote repo and you need to connect them you can follow the GitHub / GitLab instruction that are shown on the remote repo. For more information you can checkout [this](https://docs.github.com/en/get-started/git-basics/managing-remote-repositories-link)

### How do I add a ssh-key? [🔗](https://howtogit.info/#how-do-i-add-a-ssh-key-link)
A ssh-key is a way to tell the remote server like GitHub or GitLab who you are. It uses something which is called public key cryptography. The setup varies from site to site and as such GitHub will be used as an example here.


Setup the ssh keypair. To do this navigate (and/or create) the folder .ssh in your home folder (/home/yourusername in Linux, C:/Users/yourusername/ in Windows). Then run the following command in the terminal:
```bash
ssh-keygen # Create a ssh private / public keypair
```
This will ask you some questions. The first being the name of the key. Give it some name without extension, then press enter. You can also give it a password after that but it's not needed. After that you will find two files in your folder you ran ssh-keygen in: somename (private key) and somename.pub (public key).


Now open the somename.pub file and copy its content. You now need to go to GitHub, Settings, SSH and GPG Keys, New SSH key, then paste your key into the key field and give it a name. Click Add SSH key. This will add your public key to GitHub.

Lastly you need to setup the ssh config for git to work. For this create a config file (no extension) in your .ssh folder we entered previously. Add the following lines:
```bash
Host github.com
    HostName github.com
    User git
    IdentityFile path_to_your_private_key_not_the_pub_file
    IdentitiesOnly yes
```

Now you should be good to go. If you need more information then you can follow [this link](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

### How do I use git? [🔗](https://howtogit.info/#how-do-i-use-git-link)
To use git you first need to create a repo. All of the stuff that follows in this sections are done in the repo with the terminal but you can also use the git interface of your editor or IDE. After creating the repo each change in it is tracked by git. You can see the changes with:
```bash
git status
```
This will tell you what files have changed and how they changed. After that you need to add the changes to the staging area. There are basically two ways:
```bash
git add path_to_file1 path_to_file2 path_to_file3 # This will add all the specified files.
```
or 
```bash
git add . # This will add all changed files.
```
Now that the files are in the staging area they are ready to be commited. Commiting means that the changes will be added to the current [branch](https://howtogit.info/#what-is-a-branch-link). For every commit you also need to add a message while committing the changes:
```bash
git commit -m "Hey this is a cool commit message"
```

<mark>IMPORTANT: Anyone with access to the repo can see ALL your commit messages.</mark>

After the changes are commited you can push them to the remote you added. This can be done with:
```bash
git push # This will push (send) your changes to the remote git repo
```
There might be some configuration you need to do before you can push like name and email. For this see [here](https://howtogit.info/#configuring-git-link).

If you are collaborating with many people, others might push stuff that you don't have locally. To get the current changes that are at the remote repo you use the pull command:
```bash
git pull # Get the remote changes to your local repo
```
This pull might result in a merge conflict. For more information see [this](https://howtogit.info/#merging-branches-link).

The recommended way of working with git is:
1. Pull changes from the remote repo
2. Do what you need to
3. Add and commit your changes regularely.
4. Push them to the remote repo at the end of the working session
5. Resolve possible merge conflicts.

### What is a branch? [🔗](https://howtogit.info/#what-is-a-branch-link)
A git branch is like a different timeline for you files. When you create a new branch, your 'timeline' splits into two paths. You can choose to take any of the two paths to continue. To create a new branch you can use:
```bash
git checkout -b new_branch_name # Create new branch with name 'new_branch_name'
```
Can can also change to other branches with:
```bash
git checkout some_branch_name # Change branch to some_branch_name
```
Branches can also be merged together. Merging branches can be a bit confusing. For this see [merging branches](https://howtogit.info/#merging-branches-link).

### Merging branches [🔗](https://howtogit.info/#merging-branches-link)
When merging branches git tries its best to merge the two branches together, but sometimes it just don't know how to handle some merging. To merge a branch you will use:
```bash
git merge some_branch_name # Merge some_branch_name into current branch
```
This can result in something which is known as a merge conflict. Merge conflicts look like this in the file:
```
<<<<<<< HEAD
I hate git.
=======
I love git.
>>>>>>> my_awesome_branch
```
This will show you what the current content (HEAD - 'I hate git.') and other content (my_awesome_branch / 'I love git.') is. To solve the conflict you can either use the inbuild tools in the editor or IDE, or just edit the file, choosing one of the changes and removing the merge conflict markers.
After all merge conflicts are fixed, you need to add, commit and push them again.

Handling a lot of merge conflics can get out of hand quickly so using a good IDE or editor for handling these conflics in the beginning is recommended. Merge conflicts are a big topic and this only scratches the surface if you need more help checkout [the github help](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)

### Configuring git [🔗](https://howtogit.info/#configuring-git-link)
git can be configured to do a lot of cool stuff. You can even add your own custom git commands. The most basic configuration most people need to deal with are name and email, as git requires them when you work with a remote repo. To add add email and name you use the following two commands:
```bash
git config user.name "my name" # Adds your name to the repo you are in
git config user.email "my_email@howtogit.info" # Adds your email to the repo you are in 
```
You can also add them globally for any repo that you are working on. 


<mark>IMPORTANT: Anyone with access to the repo can see your name and email.</mark>

Git can be configured to do a lot more. Here is for example my config:
```bash
[init]
	defaultBranch = main
[status]
	short = false
[user]
	email = 37932436+hydr0nium@users.noreply.github.com 
	name = hydr0nium
[merge]
	tool = nvimdiff2
[push]
	autoSetupRemote = true
[mergetool]
	keepBackup = false
[gpg]
	mode = ssh
	format = ssh
[filter "lfs"]
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
	process = git-lfs filter-process
	required = true
```


### I broke my repo, YELP [🔗](https://howtogit.info/#i-broke-my-repo-yelp-link)
The good thing is if you use git with a remote repo then it's pretty hard to accidentally break it beyond repair. First off all make a backup of what you have locally. You don't want to break more than you already have. After the backup you can decide how to proceed. If you have no important changes or no changes at all you can try to delete your local repo and just pull it again. This will delete anything that was not pushed to the remote. Thats why we have a backup. If you have any important changes you still have the backup now and can just do some copy / paste action. If you are more advanced with git you might also be able to create a new branch, add the backup and merge the branch into the main branch. This should fix 99% of your problems. If you still have problems you should try Google and Stackexchange. In most cases someone, somewhere fucked it up too and asked a question about it. Good luck


### I pushed sensitive data ... [🔗](https://howtogit.info/#i-pushed-sensitive-data-link)
So you pushed a secret api key, your address, real name, what ever it is, it was sensitive. This is bad. In git, especially if you have pushed it to a remote repo it is notoriously hard to remove anything while keeping everything else. If it's something you can change like a password or API token, change it QUICKLY. If it is something like your address best bet you have is to delete it and create a new repo. There are other more non destructive ways but if you are non experienced this might be too difficult. [StackOverflow - How to remove a commit from GitHub](https://stackoverflow.com/questions/448919/how-can-i-remove-a-commit-on-github)


### Pull requests [🔗](https://howtogit.info/#pull-requests-link)
Pull requests sound similary to pulling but the two things a different. A pull request is NOT a git feature. It is aGitHub, GitLab, etc. feature. When visiting a public repo someone made you can 'fork' that repo. This just means you get a repo that you can edit even though you can't push to the repo directly. You can now edit your copy of that repo and then ask for it to be merged into the other ones repo to basically add your changes to them. This is a great way to collaborate because it allows anyone to add features, if the owner approves the pull request. A pull request can also be done in a collaberative project where multiple people have access to the same repo / project. Then you make a pull request for a branch you made and a project admin accepts or denies these changes. 

<mark>It is generally a good idea to work on what is called feature branches, no matter if you make a pull request or work together at the same project. These feature branches get then merged into the projects main branch.</mark>



