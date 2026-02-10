# Ralph Technique

Autonomous development loop using Claude Code. Based on Geoffrey Huntley's technique.

## When to Use

- Large tasks that need sustained, autonomous work
- When you want Claude to keep working until done
- Projects with clear objectives and a task list

## Quick Start

### New Project
```bash
ralph-setup my-project
cd my-project
# Edit PROMPT.md with your goals
ralph --monitor
```

### Existing Project
```bash
cd existing-project
ralph-setup .
# Create PROMPT.md and @fix_plan.md
ralph --monitor
```

### From PRD/Requirements Doc
```bash
ralph-import requirements.md my-project
cd my-project
ralph --monitor
```

## Key Files

| File | Purpose |
|------|---------|
| `PROMPT.md` | Instructions for Claude - what to build/fix |
| `@fix_plan.md` | Prioritized task list (Claude updates this) |
| `specs/` | Detailed specifications |

## Commands

```bash
ralph --monitor      # Start loop with tmux dashboard
ralph --help         # Show all options
ralph-monitor        # Open dashboard separately
ralph-setup <name>   # Initialize new project
ralph-import <prd>   # Convert PRD to Ralph format
```

## How It Works

1. Ralph starts Claude Code with your PROMPT.md
2. Claude works on tasks, updates @fix_plan.md
3. When Claude stops, Ralph detects completion
4. If tasks remain, Ralph restarts Claude
5. Loop continues until objectives met

## Safety Features

- **Rate limiting**: 100 API calls/hour default
- **Circuit breaker**: Detects stuck loops
- **5-hour limit**: Prompts when API limit hits

## Writing Good PROMPT.md

```markdown
# Project Goal
[Clear, specific objective]

# Context
[What exists, what's the current state]

# Tasks
[Reference @fix_plan.md for prioritized list]

# Constraints
[Any rules or limitations]

# Definition of Done
[How to know when finished]
```

## Writing @fix_plan.md

```markdown
# Fix Plan

## Priority 1 (Critical)
- [ ] Task A
- [ ] Task B

## Priority 2 (Important)
- [ ] Task C

## Priority 3 (Nice to have)
- [ ] Task D

## Completed
- [x] Done task
```

## Tips

- Be specific in PROMPT.md - vague goals = infinite loops
- Keep @fix_plan.md updated with clear checkboxes
- Use `--monitor` to watch progress in real-time
- Set realistic scope - Ralph works best on defined tasks

## Stopping Ralph

- `Ctrl+C` in the terminal
- Or close the tmux session
