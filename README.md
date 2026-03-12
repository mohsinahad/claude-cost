# ClaudeMeter

Live terminal dashboard for tracking Claude Code token usage and costs.

## Install as a Claude Code skill

```
/plugin marketplace add mohsinahad/claudemeter
/plugin install claudemeter@claudemeter
```

Then launch anytime with:

```
/claudemeter
```

## Install as a standalone CLI

**Recommended — using pipx (isolated, always on PATH):**
```bash
pipx install git+https://github.com/mohsinahad/claudemeter.git
```

**Or with pip:**
```bash
pip install git+https://github.com/mohsinahad/claudemeter.git
```

> **Note:** If pip warns that the script is installed in `~/.local/bin` which is not on PATH, add this to your `~/.zshrc` or `~/.bashrc`:
> ```bash
> export PATH="$HOME/.local/bin:$PATH"
> ```
> Then restart your shell or run `source ~/.zshrc`.

Then run:

```bash
claudemeter
```

## Usage

```
claudemeter --help    # show help
claudemeter --version # show version
claudemeter           # launch the dashboard
```

**Keys inside the dashboard:**

| Key | Action |
|-----|--------|
| `q` | Quit |
| `r` | Refresh |
| `1` | Last 24 hours |
| `7` | Last 7 days |
| `3` | Last 30 days |

## What it shows

- Token usage (input / output / cached) per model
- Cost breakdown by session and cumulative
- Human cost estimate (time saved vs. manual coding)
- Live-updating as you work

No API key or extra config needed — reads directly from `~/.claude/`.

## Requirements

- Python 3.11+
- Claude Code installed and used at least once (data lives in `~/.claude/`)
