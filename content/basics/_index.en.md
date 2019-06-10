---
title: Basics
weight: 5
pre: "<b>1. </b>"
chapter: true
---

### Chapter 1

# Basics

Here, you will learn how to set up your computer to connect to remote resources and some tips that will make this task easier.

```mermaid
graph LR;
  A[Local computer] -->|connection| B{credentials?}
    B -->|password| C[semi-secure]
    B -->|keys| D[secure]
    C --> E[Remote]
    D --> E[Remote]
```

## Summary

- `.ssh/config` is the file where you configure how to connect to remote computers
- `rsa keys` are files to connect to remote computers securely (they are secure password replacements)
- `tmux` is a tool to help to keep alive sessions on remote computers without the need for a permanent connection
- `/net/eofe-data004/mnt/pool/picower001` is the PILM storage space
