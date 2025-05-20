---
title: Linux
tags: tool
---

## Overview

A family of operating systems based on the Linux kernel.
Usually the kernel is packaged with a variety of packages and
tools in a distribution like [[Ubuntu]].

## Network manager CLI

The `nmcli` command can be used to connect
to check wifi networks and connect to a network.

Show available wifi networks:

```
nmcli device wifi list
```

Connect to a wifi network:

```
sudo nmcli device wifi connect "<SSID>" password "<pass>"
```

## Default apps

Default Ubuntu folders like Documents can be edited in `~/.config/user-dirs.dirs`

## Symlinks

Let's say we're in `./docs/` and we want `./docs/script.py` to be sym-linked
to the root:

```
ln -s ../script.py
```

Note that we only need to specify the filename once in this case.

## Temporary shortcut

In a session you could be frequently accessing files from another directory two levels up.
We can call this `s` with:

```
export s=../../s-project/
```

Now when we type `$s` it is the same as using the full path.
If you tab after `$s` then you will get path completion in your terminal too.

## Diff

This generates a diff between the current working directory and another directory
defined using a path variable:

```
diff --brief -r . $s > files.diff
```

## Ctags

Take an `index.md` and divide into sections focused on a specific topic using markdown headers.

The sections can be navigated using native Vim keybinds and ctags.

Hovering on the path in a section and pressing `g f` takes you to that file.

In each file include a path home and pressing `g f` will take you back.

At the top of the home `index.md` file add a set of tags:

```
| linux | windows | mac | 
```

Pressing `c-]` on any tag will take you to that section.
Then `c-t` will take you back.

This ctags functionality requires `universal-ctags` to be installed:

```bash
snap install universal-ctags
```

Running a `makefile` like the following will generate a
`tags` file that will be picked up in the (Neo)Vim editor:

```makefile
CTAGS=universal-ctags
CTAGS_FLAGS=--languages=markdown
ROOT=.

.PHONY: all clean

all: tags

tags: $(ROOT)
	$(CTAGS) $(CTAGS_FLAGS) $<

clean:
	rm -f tags
```

Each time you create a section you can add a new `| tag |` then run
`:make` from within Vim to update the tags file.
