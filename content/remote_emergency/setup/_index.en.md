---
title: Set up
weight: 10
disableToc: true
tags: ["ssh", "rsa", "connection"] 
---

## setup your credentials

### Get the credential files

```
cd
curl -L  https://github.com/pilm-bioinformatics/core/raw/master/workshops/pilm103/pilm103_rsa -o pilm103_rsa
```

Look for the `pilm03_rsa` file. Normally is good to save it inside the `~.ssh/` folder so it is private. Copy the file to that location:

`mkdir -p ~/.ssh`

`mv pilm103_rsa ~/.ssh/.`

Check the file permission: `ll ~/.ssh/pilm103_rsa`

It should show something like this:

`-rw-------@ 1 lpantano  staff   1.7K May 23 10:32 /Users/lpantano/.ssh/pilm103_rsa`

If not, type this:

`chmod 600 ~/.ssh/pilm103_rsa`

Then add the following lines to this file `~/.ssh/config` (Open it with Atom editor if you don't have experience editing from the terminal). This file contains information on how to connect to different computers: like `username`, `hostname` ...

```
Host pilm103
Hostname bioinfopilm46.mit.edu
User lpantano
IdentityFile ~/.ssh/pilm103_rsa
UseKeychain yes
```

{{% notice warning %}}
UseKeychain, only in OSX systems
{{% /notice %}}

{{% notice info %}}
change the username to the one given to you
{{% /notice %}}

This will do that you can connect to that space just by doing `ssh pilm03` and if you are on:

* mac OSX: you will be asked for the password once and it'll save it until you restart your computer
* linux: things are not that nice here, but it is not that bad :). You can do the following to get ask by the password only once.
 
```
eval `ssh-agent`
ssh-add ~/.ssh/pilm103_rsa
# type the passphrase you used when registering your account
```

### Test your connection

Now is the time to try and connect:

`ssh pilm103`

{{% notice warning %}}
You need to get this working to move forward.
{{% /notice %}}

### Create working folder

`mkdir pilm103` 
