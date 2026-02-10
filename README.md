# Claude Code Skills & MCP Servers

A collection of skills and MCP server configurations for Claude Code.

## Skills

| Skill | Description |
|-------|-------------|
| **cartographer** | Maps codebases using parallel subagents, creates `docs/CODEBASE_MAP.md` |
| **design-principles** | Minimal design system inspired by Linear, Notion, Stripe |
| **design-plugin** | Design and refine workflow with templates |
| **email-best-practices** | Email deliverability, authentication, compliance guides |
| **fal-ai** | Image/video/audio generation via fal.ai API |
| **google-docs** | Google Docs, Sheets, Drive operations |
| **obsidian-memory** | Knowledge persistence across sessions via Obsidian |
| **obvious-communication** | Clear writing: lead with point, simple words |
| **railway-deploy** | Railway deployment workflow |
| **ralph-technique** | Large autonomous task execution |
| **react-best-practices** | React/Next.js performance optimization (from Vercel) |
| **react-email** | React Email templates for transactional emails |
| **svg-logo-designer** | Professional SVG logo creation |
| **ui-skills** | Opinionated UI constraints for agents |
| **web-interface-guidelines** | Accessibility, interactions, layout, forms |

## Installation

Copy skills to your Claude Code skills directory:

```bash
# Clone the repo
git clone https://github.com/utxo-AG/claude-skills.git

# Copy skills to Claude Code
cp -r claude-skills/* ~/.claude/skills/
```

## MCP Servers

See `mcp-servers/` for MCP server configurations. Add to your `~/.claude/settings.json`:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "package-name"]
    }
  }
}
```

### Available MCP Servers

| Server | Type | Description |
|--------|------|-------------|
| railway | stdio | Railway.app deployment management |
| obsidian | stdio | Obsidian vault operations |
| github | stdio | GitHub API operations |
| google-docs | stdio | Google Docs/Sheets/Drive |
| claude-in-chrome | stdio | Browser automation |
| sokosumi | remote | Remote MCP via mcp-remote |
| stripe | http | Stripe API operations |

## Usage

Skills are automatically loaded by Claude Code. Reference them in your `CLAUDE.md`:

```markdown
## Skills

| Skill | When to Use |
|-------|-------------|
| design-principles | ANY UI work |
| react-best-practices | React/Next.js code |
| railway-deploy | Deployments |
```

## License

MIT
