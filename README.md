# ClaudeMeter

Live terminal dashboard for tracking Claude Code token usage and costs.

![ClaudeMeter dashboard](https://raw.githubusercontent.com/mohsinahad/claudemeter/main/screenshot.png)

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

```bash
pip install git+https://github.com/mohsinahad/claudemeter.git
```

Then run:

```bash
claudemeter
```

## What it shows

- Token usage (input / output / cached) per model
- Cost breakdown by session and cumulative
- Human cost estimate (time saved vs. manual coding)
- Live-updating as you work

No API key or extra config needed — reads directly from `~/.claude/`.
