---
name: claude-cost
description: Launch the claude-cost dashboard to monitor Claude Code token usage and costs in real time. Use this when the user wants to see their Claude usage, token counts, costs, or spending. Also handles "claude-cost summary", "claude-cost reset", and "claude-cost check-budget".
allowed-tools: Bash
---

Manage the claude-cost dashboard. Arguments: $ARGUMENTS

## Subcommands

If `$ARGUMENTS` is `summary`, run:
```bash
claude-cost summary
```
Print the output inline — no need to open a new tab.

If `$ARGUMENTS` is `reset`, run:
```bash
claude-cost reset
```
Print the output inline.

If `$ARGUMENTS` is empty (default), launch the live dashboard (steps below).

---

## Steps to launch the dashboard

1. Check if `claude-cost` is installed:
   ```bash
   which claude-cost 2>/dev/null
   ```

2. If not installed, install it. Try PyPI first, fall back to GitHub:
   ```bash
   if command -v pipx &>/dev/null; then
     pipx install claude-cost 2>/dev/null || pipx install git+https://github.com/mohsinahad/claudemeter.git
   else
     pip install --user claude-cost 2>/dev/null || pip install --user git+https://github.com/mohsinahad/claudemeter.git
   fi
   ```
   If installation fails, tell the user to run one of the above manually.

3. Launch the dashboard in a new tab. Since claude-cost is a live TUI it must run in a real terminal, not inside Claude's tool executor.

   **macOS — iTerm2:**
   ```bash
   if [ "$TERM_PROGRAM" = "iTerm.app" ]; then
     osascript \
       -e 'tell application "iTerm2"' \
       -e '  tell current window' \
       -e '    set newTab to create tab with default profile' \
       -e '    tell current session of newTab to write text "claude-cost"' \
       -e '  end tell' \
       -e 'end tell'
   fi
   ```

   **macOS — Warp:**
   ```bash
   if [ "$TERM_PROGRAM" = "WarpTerminal" ]; then
     osascript -e 'tell application "Warp" to activate'
     sleep 0.3
     osascript -e 'tell application "System Events" to tell process "Warp" to keystroke "t" using command down'
     sleep 0.3
     osascript -e 'tell application "System Events" to tell process "Warp" to keystroke "claude-cost"'
     osascript -e 'tell application "System Events" to tell process "Warp" to key code 36'
   fi
   ```

   **macOS — Terminal.app (fallback):**
   ```bash
   if [ "$TERM_PROGRAM" = "Apple_Terminal" ]; then
     osascript -e 'tell application "Terminal" to do script "claude-cost"'
   fi
   ```

   **Linux:**
   Tell the user: "Run `claude-cost` in a new terminal tab to see the dashboard."

4. Confirm to the user that the dashboard is launching (or give the manual command if auto-launch didn't work).

## Notes
- No API key or config required — reads from `~/.claude/`
- Press `q` to quit, `1`/`7`/`3` to change time range
- Set budgets by editing `~/.claude/dashboard_config.json`:
  `{"daily_budget": 5.00, "monthly_budget": 50.00}`
- If `claude-cost` is not on PATH after install, add `export PATH="$HOME/.local/bin:$PATH"` to shell profile
