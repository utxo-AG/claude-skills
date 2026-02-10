# Obsidian Memory

Obsidian is the **single source of truth** for all project knowledge, research, and decisions.

---

## CRITICAL: Always Search First

Before ANY task, search Obsidian:
1. Search project name
2. Search relevant technologies/tools
3. Search problem domain

**Do not skip this.** Previous context saves hours.

---

## What to Document

### Projects (REQUIRED)
Every project needs a main note at `Projects/{ProjectName}/README.md`:
- Purpose/goal
- Tech stack
- Architecture overview
- Key files/entry points
- How to run locally
- Deployment info

Update this note whenever architecture changes.

### Additional Project Notes
Create separate notes for:
| Topic | Path | When |
|-------|------|------|
| Architecture | `Projects/{Name}/Architecture.md` | Complex systems, diagrams |
| Decisions | `Projects/{Name}/Decisions.md` | Why we chose X over Y |
| API/Integration | `Projects/{Name}/{ServiceName}.md` | External service docs, auth, endpoints |
| Research | `Projects/{Name}/Research-{Topic}.md` | Investigation results |

### Tools & Technologies
External tools/frameworks go in `Tech/{ToolName}.md`:
- Quick reference
- Links to official docs
- Code snippets we use
- Gotchas/lessons learned

---

## Note Structure

```
Projects/
├── MyApp/
│   ├── README.md          # Overview, tech stack, how to run
│   ├── Architecture.md    # System design, data flow
│   ├── Decisions.md       # ADRs (why we chose X)
│   └── Stripe.md          # Integration specifics
Tech/
├── Kodosumi.md            # Framework reference
├── Railway.md             # Deployment reference
└── NextJS-Patterns.md     # Patterns we use
```

---

## Workflow

### Starting a Task
```
1. mcp__obsidian__search_notes(query: "project name")
2. mcp__obsidian__search_notes(query: "relevant tech")
3. Read found notes
4. Proceed with full context
```

### After Learning Something
Ask: "Would this save time in 3 months?"

If yes → write it down:
```
mcp__obsidian__write_note
  - path: appropriate location
  - content: concise, scannable
```

### After Making Decisions
Document the decision AND the reasoning:
- What options existed
- Why we chose this one
- Trade-offs accepted

### After Changing Architecture
Update the project README and Architecture notes immediately.

---

## Writing Rules

- Bullet points > paragraphs
- Code blocks for commands/snippets
- Tables for comparisons
- Links to source docs
- No secrets/keys
- End with: `Last updated: YYYY-MM-DD`

---

## Triggers

| Situation | Action |
|-----------|--------|
| Starting ANY task | Search Obsidian first |
| Learned about new tool | Create/update Tech/{Tool}.md |
| Made architecture decision | Update project docs |
| Researched a problem | Save findings |
| Built new feature | Update README if significant |
| Integrated external service | Document in project folder |
| Found a gotcha/bug | Add to relevant note |
