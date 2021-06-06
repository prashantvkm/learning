# Using multiple github account on same machine

### Mac (unix)

1- create ssh key using below command for your work account

```language
ssh-keygen -t rsa -C "your-email-address"
```

give a unique key name starting with id_rsa_

e.g. id_rsa_github_work

2- set the key ending with .pub into github 

**github > click on your profile pic > setting > SSH nd GPG key**

click button "New SSH Key" and then give title and paste the key content
to view the key content use below command
```language
less ~/.ssh/id_rsa_(you key name).pub
``` 

3- Now do the same steps again for your personal account setup.

4- after this copy below item in ~/.ssh/config

```language
#work github account (default)
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_github_work

#personal github account
Host github-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_github_personal
```

5- after this add below content in ~/.gitconfig

```language
[user]
        name = your_name_here
        email = your-personal-email-address
[includeIf "gitdir:~/work/"]
	path = ~/work/.gitconfig
```

create a file ~/work/.gitconfig and add below content

```language
[user]
        name = your_work_name_here
        email = your-work-email-address
```

6- after this you have to set the remote repo url in your secondary account (personal) according to the user you are using.

```language
# if you are updating
git remote set-url origin git@github-personal:username/reponame.git

# if adding to new repo
git remote add origin git@github-personal:username/reponame.git

```

this is a one time process after this you can commit and push without worry in your personal or work account.

**Note:** The last step you have to every time whenever you start a new repo for your secondary account (personal). For default last step is not required.