# tmux Cheatsheet

Personal tmux config — Nord theme + vi-mode.

## Setup

```bash
cp tmux.conf ~/.tmux.conf
tmux
```

> **Note:** Do not paste the file contents into the terminal.
> Copy the file directly to avoid bracketed paste issues (`[200~`).

---

## Prefix key

All shortcuts require pressing the **prefix key first**.

| Default | This config |
|---------|-------------|
| `Ctrl+b` | `Ctrl+a` |

---

## Pane management

| Shortcut | Action |
|----------|--------|
| `Prefix` + `\|` | Vertical split |
| `Prefix` + `-` | Horizontal split |
| `Prefix` + `h/j/k/l` | Move between panes (left/down/up/right) |
| `Prefix` + `H/J/K/L` | Resize pane |
| `Prefix` + `m` | Zoom / unzoom pane |

---

## Windows

| Shortcut | Action |
|----------|--------|
| `Prefix` + `c` | New window (inherits current path) |
| `Prefix` + `n` | Next window |
| `Prefix` + `p` | Previous window |
| `Prefix` + `0-9` | Jump to window by number |

---

## Copy mode (vi)

| Shortcut | Action |
|----------|--------|
| `Prefix` + `Enter` | Enter copy mode |
| `v` | Begin selection |
| `V` | Select entire line |
| `Ctrl+v` | Rectangle selection |
| `y` | Copy selection and exit |
| `H` / `L` | Jump to start / end of line |
| `q` | Cancel |

---

## Sessions

| Shortcut | Action |
|----------|--------|
| `Prefix` + `d` | Detach from session |
| `Prefix` + `$` | Rename session |
| `tmux ls` | List sessions (from shell) |
| `tmux attach -t <name>` | Reattach to session |

---

## Misc

| Shortcut | Action |
|----------|--------|
| `Prefix` + `r` | Reload `~/.tmux.conf` |
| `Prefix` + `?` | Show all keybindings |

---

## Troubleshooting

**`no server running on /tmp/tmux-0/default`**
Run `tmux` first to start a session. `source-file` only works inside a running session.

**`unknown command: [200~`**
Bracketed paste issue. Copy the file directly instead of pasting its contents:
```bash
cp tmux.conf ~/.tmux.conf
```

**CRLF line endings (`^M`)**
```bash
sed -i 's/\r//' ~/.tmux.conf
```
