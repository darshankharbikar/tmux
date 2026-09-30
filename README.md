# tmux Cheat Sheet

## 1. Start / Manage Sessions

```bash
tmux                         # Start tmux
tmux new -s work             # Create named session
tmux ls                      # List sessions
tmux attach -t work          # Attach to session
tmux new -s work             # Create session
tmux kill-session -t work    # Kill session
tmux kill-server             # Kill all tmux sessions
```

### Detach

```text
Ctrl-b d
```

Your programs continue running after detaching.

---

## 2. Prefix Key

Most tmux commands start with:

```text
Ctrl-b
```

Press `Ctrl-b`, release both keys, then press the command key.

Example:

```text
Ctrl-b c
```

creates a new window.

---

## 3. Windows

| Action               | Shortcut   |
| -------------------- | ---------- |
| New window           | `Ctrl-b c` |
| Next window          | `Ctrl-b n` |
| Previous window      | `Ctrl-b p` |
| Window list          | `Ctrl-b w` |
| Go to window 0       | `Ctrl-b 0` |
| Go to window 1       | `Ctrl-b 1` |
| Rename window        | `Ctrl-b ,` |
| Close current window | `Ctrl-b &` |

Example:

```text
Window 0 → Linux
Window 1 → Yocto
Window 2 → Kernel
```

---

## 4. Panes

### Split

```text
Ctrl-b %
```

Vertical split:

```text
┌──────────┬──────────┐
│          │          │
│  Pane 1  │  Pane 2  │
│          │          │
└──────────┴──────────┘
```

Horizontal split:

```text
Ctrl-b "
```

```text
┌─────────────────────┐
│       Pane 1        │
├─────────────────────┤
│       Pane 2        │
└─────────────────────┘
```

### Navigate

```text
Ctrl-b ←
Ctrl-b →
Ctrl-b ↑
Ctrl-b ↓
```

### Other pane commands

| Action             | Shortcut         |
| ------------------ | ---------------- |
| Swap pane          | `Ctrl-b o`       |
| Show pane numbers  | `Ctrl-b q`       |
| Zoom/unzoom pane   | `Ctrl-b z`       |
| Close pane         | `Ctrl-b x`       |
| Resize pane        | `Ctrl-b` + arrow |
| Toggle pane layout | `Ctrl-b Space`   |

**`Ctrl-b z` is particularly useful** when working with long Yocto/kernel commands.

---

## 5. Scroll / Copy Mode

Enter scroll mode:

```text
Ctrl-b [
```

Then:

```text
↑ / ↓             Scroll
PageUp / PageDown Page scrolling
q                  Exit
```

This is useful for examining long build logs.

---

## 6. Rename Sessions

From inside tmux:

```text
Ctrl-b $
```

Or from the shell:

```bash
tmux rename-session -t work yocto
```

---

## 7. Useful Commands

```bash
tmux list-sessions
tmux list-windows
tmux list-panes
tmux display-message
```

Kill a specific window:

```bash
tmux kill-window -t 2
```

Kill a specific pane:

```bash
tmux kill-pane -t 2
```

---

# Practical Yocto Setup

For your Yocto work, you could maintain one persistent session:

```bash
tmux new -s yocto
```

Then create windows:

```text
Ctrl-b c
```

Example:

```text
yocto:0  build
yocto:1  shell
yocto:2  logs
yocto:3  kernel
```

Check it later:

```bash
tmux ls
```

Reconnect:

```bash
tmux attach -t yocto
```

This is especially useful for long-running:

```bash
bitbake core-image-minimal
```

because you can detach with:

```text
Ctrl-b d
```

and reconnect later without stopping the build.

---

## 10 Commands Worth Memorizing

```text
Ctrl-b d       Detach
Ctrl-b c       New window
Ctrl-b n       Next window
Ctrl-b p       Previous window
Ctrl-b %       Vertical split
Ctrl-b "       Horizontal split
Ctrl-b arrows  Move between panes
Ctrl-b z       Zoom pane
Ctrl-b [       Scroll
Ctrl-b q       Pane numbers
Ctrl-b x       Close pane
```

And from the normal shell:

```bash
tmux new -s NAME
tmux ls
tmux attach -t NAME
tmux kill-session -t NAME
```

**If you remember only these, you can use tmux effectively.**
