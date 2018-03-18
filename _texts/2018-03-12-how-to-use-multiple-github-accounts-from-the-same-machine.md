---
layout: post
title:  "How to Manage Multiple Github Accounts from the Same Machine"
date:   2018-3-12 16:16:01 -0600
categories: Github
---

_March 12, 2018_
<br>

Suppose you have two github accounts, `githubPersonal` and `githubWork`.
Now to manage both those accounts from the same machine you can follow the following steps:

<strong>Step 1: Set up SSH keys</strong>

Go to your `.ssh` directory and create two SSH keys. 
When prompted, save each of them to a separate file. 

{% highlight shell %}
$ cd ~/.ssh
$ ssh-keygen -t rsa -C "your_personal_email"
# save it as id_rsa_personal when prompted
$ ssh-keygen -t rsa -C "your_work_email"
# save it as id_rsa_work when prompted
{% endhighlight %}

The above commands will create the following four files:

* id_rsa_personal
* id_rsa_personal.pub
* id_rsa_work
* id_rsa_work.pub


<strong>Step 2: Add the keys to your Github accounts</strong>

Follow these steps with both the keys and the Github accounts:
* Copy the key to your clipboard (`$ pbcopy < ~/.ssh/id_rsa_personal.pub` will do this for you)
* Go to your [Github Account Settings > SSH and GPG Keys](https://github.com/settings/keys)
* Click "New SSH key"; then paste the key into the field and add a suitable title
* Click "Add key" then enter your Github password to confirm


<strong>Step 3: Create a Configuration File</strong>

Create a config file in `~/.ssh/`:

`$ touch ~/.ssh/config`

Edit the file using the text editor of your choice. e.g. With nano: `$ nano config`
{% highlight shell %}
# githubPersonal
Host personal
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_rsa_personal

# githubWork
Host work
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_rsa_work
{%endhighlight %}

<strong>Step 4: Update stored identities<strong>

Clear currently stored identities:

`$ ssh-add -D`

Add new keys:

`$ ssh-add id_rsa_personal`  
`$ ssh-add id_rsa_work`

Test to make sure new keys are stored:

`$ ssh-add -l`

Test to make sure Github recognizes the keys:

`$ ssh -T personal`  
`Hi githubPersonal! You've successfully authenticated, but GitHub does not provide shell access.`  
`$ ssh -T work`  
`Hi githubWork! You've successfully authenticated, but GitHub does not provide shell access.`

<strong>Step 5: Test it out!<strong>

On Github, create a new repo in your personal account, `githubPersonal`, called `test-personal`.
Back on your local machine, create a test directory:

`$ mkdir ~/githubPersonal/test-personal`  
`$ cd ~/githubPersonal/test-personal`

Add a test “readme.md” file and push to Github:

`$ touch readme.md`  
`$ git init`  
`$ git add .`  
`$ git commit -m "first commit"`  
`$ git remote add origin git@personal:githubPersonal/test-personal.git`  
`$ git push origin master`

Repeat the process for your githubWork account. Except replace the following command:

`$ git remote add origin git@personal:githubPersonal/test-personal.git`

with this one:

`$ git remote add origin git@work:githubWork/test-work.git`

assuming you named the repos and the directories accordingly.

_Note: In the command, we changed 
the `git@github` part based on how we named the host in our config file._

Return to your GitHub. You should see the changes have taken place in the repository.

<br> 