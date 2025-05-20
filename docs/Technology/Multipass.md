---
title: Multipass
tags: cloud
---

Multipass is a CLI tool for creating [[Ubuntu]] virtual machines.
It's relatively simple and also has a GUI.

# Create an Ubuntu instance with bridged networking

To create an Ubuntu 24.04 instance called "my-vm":

```bash
multipass launch 24.04 --name my-vm
```

To access `my-vm`'s shell:

```bash
mulipass shell my-vm
```

Exit with `exit` and then stop the VM:

```bash
multipass stop my-vm
```

To set up bridged networking with ethernet, first run:

```bash
multipass networks
```

Find the type `ethernet`, in my case: `enp37s0`.

If you haven't done so already, set this as the preferred network:

```bash
multipass set local.bridged-network=enp37s0
```

Finally, set the VM to use bridged networking:

```bash
multipass set local.my-vm.bridged=true
```

You should now be able serve to localhost and ssh into remote servers.
