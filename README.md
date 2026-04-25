# Claude_Code_Manual
This repository contains documentation and tools for optimizing your workflow with Claude Code.

## Global Configuration (`~/.claude/CLAUDE.md`)
Set up universal rules that apply across all projects by configuring the global directory.

### Setup
1) Enter the configuration directory:
``` bash
cd ~/.claude
code ~/.claude/CLAUDE.md # May use others
```

2) You can copy and paste the `CLAUDE.md` from this repo.

**Note:** Inside any project directory, you can create a local `CLAUDE.md` to provide context specific to that codebase.

## Wakeup! Claude!
`WakeupClaude` is a minimal Linux scheduler to optimize Claude's 5-hour usage windows. By sending low-cost CLI pings, it automatically trigger the refresh mechanism, ensuring your message quotas are aligned with your peak productivity hours.

