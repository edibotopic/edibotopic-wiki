---
title: SSH
tags: tool
---

## Create an SSH key

To create a key:

```bash
SSH-keygen -t ed25519 -C "me@email.com" -f ~/.SSH/my_key
```

After a prompt to set a password, a private key is saved to `~/.SSH/my_key` and a public key to `~/.SSH/my_key.pub`.

> **note** Note
> The public key is what needs to be copied to remote Git services like GitHub and GitLab using their online UI.

When the public key is added to your remote Git service, you can push and pull between your local and remote repos.

## Copy an SSH key to a server

To copy the key to a remote server:

```bash
ssh-copy-id -i ~/.ssh/my_key.pub user@server
```

You can now SSH into the server and you should not need to enter a password each time.

## Use git operations from the server

To perform git operations like `git push` after SSH-ing into the server, you
can copy the appropriate private SSH key to the server.

It is better, however, to use **agent forwarding** with the `-A` flag:

```bash
ssh -A user@server
```

This means you can access your private SSH keys from your local machine without exposing them.
