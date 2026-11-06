# Burst Your Ideas Onboarding

Plugin for Claude Code, Cowork and Cursor that guides a team member step by step through setting up the Burst Your Ideas agent stack.

## What it covers

1. Adding the private marketplace `burstyourideas/bystack-sdd` (requires membership of the `burstyourideas` GitHub organization).
2. Choosing which plugins to install (`product`, `dev`; further plugins as they are released).
3. Connecting GitHub (`gh` CLI) and ClickUp (connector).
4. Setting `BYSTACK_WORKSPACE_ROOTS` for local use.
5. Launching `/dev:by-install-routines`.
6. Optionally installing the Spree agent skills and the Spree documentation MCP.

The plugin contains no credentials and never asks for them. Sign-in always happens in the product's own screens.

## Install

### Own marketplace (available now)

This repository is also a marketplace named `byideas`, so the plugin can be installed before it is listed in Anthropic's directory.

Claude Code:

```
/plugin marketplace add burstyourideas/byideas-onboarding
/plugin install byideas-onboarding@byideas
```

Cowork: in **Customize > Plugins**, add the GitHub repository `burstyourideas/byideas-onboarding` as a marketplace and install `byideas-onboarding` from it. Alternatively, use **Add > Upload plugin** with a zip of this repository.

Cursor: copy this repository to `~/.cursor/plugins/local/byideas-onboarding` (a real copy, not a symlink to another folder) and run **Developer: Reload Window**. The command is `/byideas-onboarding-start`. `product` and `dev` already include `.cursor-plugin/plugin.json` in `burstyourideas/bystack-sdd`; copy `plugins/product` and `plugins/dev` the same way. Details are in `skills/byideas-onboarding/references/cursor.md`.

### Anthropic directory

Once listed, add it from **Discover** in **Customize > Plugins**. Claude Code loads it through account sync.

## Use

```
/byideas-onboarding:start
```

In Cursor the command is `/byideas-onboarding-start`.

Or ask the agent to help you get set up with the Burst Your Ideas stack. In Cowork the guide skips the steps that only exist in Claude Code (workspace roots and automation routines). In Cursor, `dev` commands use the filename (`/by-init`, `/by-install-routines`) and `product` is a set of skills.

## Contents

```
.claude-plugin/plugin.json
.claude-plugin/marketplace.json                 Own marketplace `byideas`
.cursor-plugin/plugin.json                      Cursor manifest
.cursor-plugin/commands/byideas-onboarding-start.md
commands/start.md
skills/byideas-onboarding/SKILL.md
skills/byideas-onboarding/references/plugins.md   Plugin catalog
skills/byideas-onboarding/references/cowork.md     Cowork variants of each step
skills/byideas-onboarding/references/cursor.md     Cursor variants of each step
skills/byideas-onboarding/references/spree.md     Spree skills and docs MCP
```

## Maintenance

- Add new plugins as rows in `references/plugins.md` once they have a real install command.
- Spree commands come from the Spree documentation; re-check them when Spree changes its distribution.
- Bump `version` in `plugin.json` on every user-visible change.
