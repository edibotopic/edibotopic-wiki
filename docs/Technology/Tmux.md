---
title: Tmux
tags: tool
---

Terminal multiplexer.

Open a named Tmux session with `tmux new -s <name>`.

To set the working dir use `tmux new -s <name> -c <path/to/dir/>`.

End a session with `c-d`.

Detach a session with `c-b d`.

Check active sessions with `tmux ls`.

Attach to session called `<name>` with `tmux attach -t <name>`.

If using `tmux-resurrect`:

* save a session with `c-b s`
* restore a session with `c-b r`

[[Zellij]] is an alternative multiplexer.
