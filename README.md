# Setting up Git on Ubuntu

## Set up Git username and email

* Check git version

`git -v`

* If git is not installed

`sudo apt update`

`sudo apt install git`

* Setup git configuration

`git config --global user.name "your_username"`

`git config --global user.email "name@example.com"`


## Set up ssh configuration for authentication

1 - `ls -al ~/.ssh`

Check if you have id_ed25519 and id_ed25519.pub (or id_rsa and id_rsa.pub), you likely have an existing key and can skip to Step 3. 

2 - If you don't have an SSH key, generate one:

`ssh-keygen -t ed25519 -C "your_email@example.com"`

OR

`ssh-keygen -t ed25519`

Press Enter for location and passphrase. A passphrase is a password you can add if you want, or just press Enter to skip.

## Add your SSH key to the ssh-agent

The ssh-agent manages your keys and remembers your passphrase so you don't have to enter it every time. 

1 - `eval "$(ssh-agent -s)"`

Start the ssh-agent in the background.

2 - `ssh-add ~/.ssh/id_ed25519`

Add your private SSH key to the ssh-agent.

## Add the public key to your account

1 - Copy your public SSH key

`cat .ssh/id_ed25519.pub`

2 - Go to your GitHub account Settings.

3 - In the left sidebar, click SSH and GPG keys.

4 - Click New SSH key.

5 - In the title add any name to your key (e.g., "batch-10 key").

6 - Paste your public key copied from terminal into the "Key" field.

7 - Click Add SSH key and confirm with your GitHub password if prompted. 

8 - Verify your connection.

`ssh -T git@github.com`

Congratulations!!!! Connection verified.
Now you easily do clone, push, and pull.


## Let's try an example

* Clone any repository. Use SSH link for cloning.

- `git clone git@github.com:Afroz-J-Shaikh/90DaysOfDevOps.git`

### Note: Use `git branch` check your branch name(main/master) and use that name when doing pull or push

## Let's create file and commit it to the local repo

1 - Go inside your locally cloned repo and add any file.

`cd 90DaysOfDevOps/2026/day-07`

`touch demo.txt`

`echo "Checking the push command" > demo.txt`

Added demo.txt.

2 - Now add it to your local git repo and commit.

`git add demo.txt`

`git commit -m "demo.txt added to git repo"`

We have commited demo.txt to our local git repo.

## Push our changes to remote repo

* `git push origin master`

And Done!!! Task accomplished.

### Note : Whenever you sync your forked repo on GitHub, go to your local repo and pull those changes first,
### `git pull origin master`. 

After pulling the changes to your local repo, then start creating your files and any other changes you want. This way, there won't be any conflict between your origin and master.

### Tip : Always pull changes first then create,add,commit and push any new changes.


