# ClaudeMeter

Live terminal dashboard for tracking Claude Code token usage and costs.

## Install as a Claude Code skill

```
/plugin marketplace add mohsinahad/claudemeter
/plugin install claudemeter@claudemeter
```

Then use:

```
/claudemeter             # launch live dashboard in a new tab
/claudemeter summary     # print today/month costs inline
/claudemeter reset       # reset config to defaults
```

## Install as a standalone CLI

```bash
pipx install claudemeter        # recommended
# or
pip install claudemeter
```

> **Note:** If pip warns that the script is installed in `~/.local/bin` which is not on PATH, add this to your `~/.zshrc` or `~/.bashrc`:
> ```bash
> export PATH="$HOME/.local/bin:$PATH"
> ```

Then run:

```bash
claudemeter           # live dashboard
claudemeter summary   # quick inline summary
claudemeter reset     # reset config
```

## Budget alerts

Set spending limits in `~/.claude/dashboard_config.json`:

```json
{
  "daily_budget": 5.00,
  "monthly_budget": 50.00
}
```

To get automatic warnings after each Claude session, add a hook to `~/.claude/settings.json`:

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "claudemeter check-budget"
          }
        ]
      }
    ]
  }
}
```

Claude will print a warning in your session whenever you hit 80% or 100% of your budget.

## Usage

```
claudemeter --help     # show help
claudemeter --version  # show version
claudemeter            # launch the dashboard
claudemeter summary    # print costs inline (no TUI)
claudemeter check-budget  # check limits (exits 2 if over 80%)
claudemeter reset      # reset config to defaults
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
