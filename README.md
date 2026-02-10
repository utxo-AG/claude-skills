# Claude Code Coworkers

Your AI team for Claude Code. Each coworker has a specialty - call on them when you need their expertise.

---

## The Team

### Engineering

| Coworker | Role | Call When |
|:---------|:-----|:----------|
| **Cartographer** | Codebase Analyst | "Map this codebase", "Document the architecture" |
| **React Expert** | Performance Engineer | Writing React/Next.js, optimizing bundles, fixing rerenders |
| **Ralph** | Project Manager | Large autonomous tasks, multi-step implementations |

### Design

| Coworker | Role | Call When |
|:---------|:-----|:----------|
| **Design Principles** | UI Architect | Building any interface - dashboards, forms, admin panels |
| **UI Skills** | Interaction Designer | Animations, micro-interactions, responsive layouts |
| **Web Guidelines** | Accessibility Lead | Forms, accessibility, content structure |
| **SVG Logo Designer** | Brand Designer | Creating logos, icons, visual marks |

### Communication

| Coworker | Role | Call When |
|:---------|:-----|:----------|
| **Email Expert** | Deliverability Specialist | SPF/DKIM setup, avoiding spam, compliance |
| **React Email** | Email Developer | Building email templates that render everywhere |
| **Obvious Communication** | Technical Writer | Documentation, explanations, clear writing |

### Infrastructure

| Coworker | Role | Call When |
|:---------|:-----|:----------|
| **Railway Deploy** | DevOps Engineer | Deploying apps, managing environments |
| **Google Docs** | Document Manager | Docs, Sheets, Drive operations |
| **Obsidian Memory** | Knowledge Manager | Persisting context across sessions |

### Creative

| Coworker | Role | Call When |
|:---------|:-----|:----------|
| **Fal AI** | Media Generator | Images, video, audio generation |

---

## Quick Start

```bash
git clone https://github.com/utxo-AG/claude-skills.git
cp -r claude-skills/* ~/.claude/skills/
```

Then reference in your `CLAUDE.md`:

```markdown
## Team

- **Design Principles** → Any UI work
- **React Expert** → React/Next.js code
- **Railway Deploy** → Deployments
```

---

## MCP Servers

Infrastructure connections in `mcp-servers/example-config.json`:

| Server | Purpose |
|:-------|:--------|
| railway | Deploy and manage Railway apps |
| obsidian | Read/write Obsidian vault |
| github | GitHub API operations |
| google-docs | Docs, Sheets, Drive |
| stripe | Payments integration |

---

MIT License
