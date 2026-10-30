# Spree documentation resources

Source of truth:
- Skills: https://spreecommerce.org/docs/developer/agentic/agent-skills
- Docs MCP: https://spreecommerce.org/docs/developer/agentic/docs-mcp

Both are optional and independent.

## Agent skills

Install the Claude Code plugin (run inside a Claude Code session):

```
/plugin marketplace add spree/agent-skills
/plugin install spree@spree
```

Notes from the Spree documentation:

- The skills target **Spree 6**. For **Spree 5**, the documentation says to use
  the **v0.3.0** release of the skills. It does not give a pinning command here;
  point the user to the page rather than inventing one. Relevant while a project
  is still on Spree 5.2.
- The plugin also provides a `spree-expert` subagent, `/spree:doctor`,
  `/spree:audit-upgrade [version]` and safety hooks. The hooks block
  destructive database commands and warn on hardcoded secrets; they can be
  disabled with `SPREE_HOOKS_DISABLE=1`.
- Use **either** the plugin or the `npx skills add spree/agent-skills` CLI path,
  never both: installing both makes the skills collide. Prefer the plugin.

## Docs MCP

No authentication is required. In Claude Code:

```bash
claude mcp add --transport http spree-docs https://spreecommerce.org/docs/mcp
```

Add `--scope project` to share the connection through `.mcp.json`; the default
local scope applies only to the user. The server exposes two tools: full-text
search and reading a documentation page as Markdown.

Claude Desktop / claude.ai: Settings, Connectors, **Add custom connector**, and
paste `https://spreecommerce.org/docs/mcp`.

Verify afterwards with `/mcp` that `spree-docs` is listed.
