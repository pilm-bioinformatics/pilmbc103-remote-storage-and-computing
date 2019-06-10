---
title: File transfer
weight: 20
disableToc: false
---

## Mount/Connect the server

Open a **new terminal**

Only for **Linux** users:

```
eval `ssh-agent`
ssh-add ~/.ssh/pilm103_rsa
# type the passphrase you used when registering your account
```

A good way to interact with remote storage is to mount the server as a folder on your computer. For that we need the `sshfs` command (See requirements to know how to install it).

```
cd
mkdir -p ~/mnts/pilm103
```

And bind the folder to the remote folder:

```bash
sshfs pilm103:. ~/mnts/pilm103 -o delay_connect -o follow_symlinks
```

Now you should be able to see your remote data space on your computer:

`ls ~/mnts/pilm103`

To **Unmount/ disconnect**:

```
umount ~/mnts/pilm103
```

## rsync command

Open a **new terminal**

Only for **Linux** users:
```
eval `ssh-agent`
ssh-add ~/.ssh/pilm103_rsa
# type the passphrase you used when registering your account
```

This is the best tool to use to transfer files in an efficient manner. The main advantages are:

* It checks the file contents so that it only sends the differences since the last time data was sent 
* Choose to send only some files
* Exclude some specific files or create a pattern of exclusions
* Copy the file metadata (modification time, owner, permissions)
* Dry-run: you can check what is going to do before doing it

The basic command is:

`rsync [options] origin target`

Normally `origin` is a local folder and `target` is a remote computer.

### test file

Download the following file:

```
cd ~/Downloads
mkdir work && cd work
curl -L https://github.com/nf-core/test-datasets/raw/smrnaseq/testdata/sample_1.fastq.gz -o sample.fastq.gz
cd ..
```

### data in/out

In this case, we will copy from our local computer to the MIT storage cluster.

`rsync -avnP work/sample.fastq.gz pilm103:~/pilm103`

Options explained:

* a: it's a combo option for: keeping owner, timestamps, permissions in a recursive manner
* v: verbose on, to know what files are being copied
* P: progress
* n: dry-run, so there is no copy action, only shows what would happen 

Alternatives:

* full folder transfered: `rsync -avn work pilm103:~/pilm103`
* full folder without creating the folder in target, only files are sent: `rsync -avn work/ pilm103:~/pilm103`

If what we see makes sense, then we repeat it without the `-n` option. We can add `-P` to see the progress of the transfer.

`rsync -avP work pilm103:~/pilm103`

Move to the terminal where you established the first connection to the server and check if you see the file/folder now in your home directory.

