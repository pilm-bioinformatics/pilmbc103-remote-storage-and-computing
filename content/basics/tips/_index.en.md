---
title: Permanent connection
weight: 15
disableToc: true
tags: ["ssh", "terminal"] 
---

## Tricks to use sessions inside teminal: tmux 

Learn more about [tmux](https://thoughtbot.com/blog/a-tmux-crash-course), it basically is a way to leave your session and its environment alive in a remote computer even after closing your local terminal.

For instance, imagine that you use an interactive job to copy a lot of files over. If you lose the connection to the remote computer, that session ends, and the transfer will be killed. As well, it allows to have multiple sessions with a single connection.

Interaction with **tmux** is done by the use of two keys in the keyboard: `Ctrl + b`. That is called the **prefix**, and is the trigger to get **tmux** listen to what you want to do next: for instance create a new window, or change between windows. 

When you are in the remote computer, type:

```
tmux new -s s1
```

Then create another window:

```
prefix + c
```

Name windows:

```
prefix + ,
```

Now type `other` and press `Enter`

Move across windows:

```
prefix + 0
prefix + 1
```

Detach the session and connect back to your previous session:

```
prefix + d
tmux a -t s1
```

Disconnect from the computer and connect back:

```
ctrl + d
ssh mit
tmux -a -t s1
```

