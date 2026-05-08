# scripts

Personal shell scripts for development workflow.

---

## gitdash

Personal git activity dashboard. Scans all git repositories under a configured root directory and displays commit activity for a given date range.

### Setup

First run launches an interactive wizard to save your configuration:

```
gitdash
```

Configuration is stored at `~/.config/gitdash/config`:

```
ROOT_DIR=/path/to/your/repos
AUTHOR=you@example.com
```

View or edit config at any time:

```
gitdash config
```

### Usage

```
gitdash [--date=<range>] [--author=<email>] [--root=<dir>]
gitdash config
gitdash --help
```

### Date options

| Option | Description |
|---|---|
| `today` | Commits from today *(default)* |
| `yesterday` | Commits from yesterday |
| `this-week` | Commits since Monday |
| `this-month` | Commits since 1st of month |
| `YYYY-MM-DD` | Commits on a specific date |
| `START:END` | Commits between two dates |

### Examples

```sh
gitdash                                          # today's activity
gitdash --date=yesterday
gitdash --date=this-week
gitdash --date=2025-01-01:2025-01-31
gitdash --author=other@example.com              # one-off author override
gitdash --root=~/projects --date=this-week      # one-off root override
```

---

## vrun

Vite dev server launcher. Starts one or more Vite projects by short alias name, with per-project color-coded output and an interactive command interface.

### Setup

First run launches an interactive wizard to add your first project. Add more any time:

```
vrun add
```

Configuration is stored at `~/.config/vrun/projects.conf`:

```
alias=/absolute/path/to/project
```

### Usage

```
vrun <alias> [alias2 …]    # start one or more dev servers
vrun add                   # add a project
vrun rm <alias>            # remove a project
vrun ls                    # list configured projects
vrun --help                # full manual
```

### Interactive commands

While servers are running, type a command and press Enter:

| Command | Description |
|---|---|
| `s` | Stop all servers and exit |
| `rs` | Restart all servers |
| `r <alias>` | Restart a specific server |
| `run <alias>` | Start a configured project in this session |
| `add` | Add a project to config and optionally launch it |
| `rm <alias>` | Remove a project from config |
| `ls` | Show running server statuses |
| `h` | Show command reference |

### Examples

```sh
vrun frontend                        # single project, Vite default port 5173
vrun frontend dashboard admin        # three projects, sequential ports from 5173
```

Ctrl+C stops all servers gracefully.
