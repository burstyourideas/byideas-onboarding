# Burst Your Ideas Onboarding

Claude Code plugin that guides a team member step by step through setting up the Burst Your Ideas agent stack.

## What it covers

1. Adding the private marketplace `burstyourideas/bystack-sdd` (requires membership of the `burstyourideas` GitHub organization).
2. Choosing which plugins to install (`product`, `dev`; further plugins as they are released).
3. Connecting GitHub (`gh` CLI) and ClickUp (connector).
4. Setting `BYSTACK_WORKSPACE_ROOTS` for local use.
5. Launching `/dev:by-install-routines`.
6. Optionally installing the Spree agent skills and the Spree documentation MCP.

The plugin contains no credentials and never asks for them. Sign-in always happens in the product's own screens.

## Install

Add the plugin from Anthropic's directory on claude.ai; Claude Code loads it through account sync. Then run:

```
/byideas-onboarding:start
```

or ask Claude to help you get set up with the Burst Your Ideas stack.

## Contents

```
.claude-plugin/plugin.json
commands/start.md
skills/byideas-onboarding/SKILL.md
skills/byideas-onboarding/references/plugins.md   Plugin catalog
skills/byideas-onboarding/references/spree.md     Spree skills and docs MCP
```

## Maintenance

- Add new plugins as rows in `references/plugins.md` once they have a real install command.
- Spree commands come from the Spree documentation; re-check them when Spree changes its distribution.
- Bump `version` in `plugin.json` on every user-visible change.
