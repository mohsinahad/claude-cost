---
name: claudemeter
description: Launch the ClaudeMeter dashboard to monitor Claude Code token usage and costs in real time. Use this when the user wants to see their Claude usage, token counts, costs, or spending.
allowed-tools: Bash
---

Launch the ClaudeMeter live terminal dashboard.

## Steps

1. Check if `claudemeter` is installed:
   ```bash
   which claudemeter 2>/dev/null || pip show claudemeter 2>/dev/null
   ```

2. If not installed, install it from the GitHub repo:
   ```bash
   pip install git+https://github.com/mohsinahad/claudemeter.git
   ```
   (If that fails, tell the user to install manually with the above command.)

3. Launch the dashboard in a new Terminal window so it doesn't interrupt the Claude session:
   ```bash
   osascript -e 'tell application "Terminal" to do script "claudemeter"'
   ```
   On Linux (no osascript), run directly:
   ```bash
   claudemeter
   ```

4. Confirm to the user that the dashboard has launched (or is running in their terminal).

Note: The dashboard reads from `~/.claude/` — no API key or config required beyond normal Claude Code usage.
