# GIT Config for short and simple commands

Below is the file path (Mac/Unix) where you need to add the configuration.

```console
~/.gitcofig
```
----------

### **configuration**

```console
[user]
	name = your_name_here
	email = your_email_id_here
[color]
	ui = auto
[core]
	pager = less -FMRiX
[push]
	default = simple
[alias]
	dag = log --graph --format='format:%C(yellow)%h%C(reset) %C(blue)%an <%ae>%C(reset) %C(magenta)%cr%C(reset)%C(auto)%d%C(reset)%n%s' --date-order
	co = checkout
	br = branch --format='%(HEAD) %(color:yellow)%(refname:short)%(color:reset) - %(contents:subject) %(color:green)(%(committerdate:relative)) [%(authorname)]' --sort=-committerdate
	cm = commit -m 
	st = status
	unc = reset HEAD~1 --mixed
	lg1 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
	lg2 = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all
	lg3 = log --pretty=format:\"%C(magenta)%h%Creset -%C(auto)%d%Creset %s %C(magenta) (%cr) %C(bold green) [%an] %C(bold blue)[%ae]\" --abbrev-commit -10
	lg = !"git lg3" 
	sub = restore --staged 
	save = push origin HEAD 
	edit-repo = remote set-url origin 
	add-repo = remote add origin 

```