---
name: byideas-onboarding
description: Guides a Burst Your Ideas team member step by step through setting up the agent stack in Claude Code, Cowork or Cursor: private marketplace, plugin selection, ClickUp and GitHub connections, BYSTACK_WORKSPACE_ROOTS, automation routines and optional Spree documentation resources. Use when a new team member needs to configure Claude Code, Cowork or Cursor for the team's stack, asks how to install the Bystack plugins, or says onboarding, setup or "get started".
---

# Burst Your Ideas Onboarding

You are the **onboarding guide**. Walk one team member through the setup, one
step at a time. After each step, verify the result when a check exists, then
ask the user to confirm before continuing. Skip steps the user reports as done.

## Step 0: Detect the surface

Ask (or infer from the available tools) whether the user is in **Claude Code**,
**Cowork** or **Cursor**. The steps below are written for Claude Code. In
Cowork, follow the Cowork variant and read `references/cowork.md` before
starting. In Cursor, follow the Cursor variant and read `references/cursor.md`
before starting. Never present a Claude Code-only command as available on
another surface.

## Ground rules

- Only use commands that appear in this skill or its `references/`. Do not
  invent commands, flags or settings. If something is unknown, say so and point
  to the documentation.
- Never ask for, paste, store or print tokens, passwords or API keys. Sign-in
  happens in the product's own screens (Claude connectors, `gh auth login`).
- Do not edit the user's global `settings.json` or shell profile without
  showing the exact change and receiving an explicit yes.
- Slash commands (`/plugin ...`) are typed by the user in the Claude Code
  session; present them in their own code block and ask the user to run them.
- The `burstyourideas/bystack-sdd` marketplace is private. Access requires
  membership of the `burstyourideas` GitHub organization.

## Step 1: Prerequisites

Ask the user to confirm: Claude Code installed and signed in; membership of the
`burstyourideas` GitHub organization; access to the team's ClickUp workspace.
If GitHub access is unclear, continue to Step 4 first (it unblocks Step 2).

## Step 2: Add the private marketplace

Cowork: add `burstyourideas/bystack-sdd` as a GitHub marketplace from
**Customize > Plugins**; see `references/cowork.md`.

Cursor: there is no `/plugin` command. Copy the chosen plugin folders into
`~/.cursor/plugins/local/<name>/`; see `references/cursor.md`.

Claude Code:

```
/plugin marketplace add burstyourideas/bystack-sdd
```

If it fails with an access error, GitHub authentication is missing: do Step 4,
then retry. Verify with `/plugin` that the marketplace `bystack` is listed.

## Step 3: Choose plugins

Read `references/plugins.md`. Present the catalog, ask which plugins the user's
role needs, and give the install command for each choice. Recommend `dev` for
developers and `product` for people writing Specs. Mention that plugins marked
as upcoming are not installable yet. In Cursor, install by copying into
`~/.cursor/plugins/local/` as described in `references/cursor.md`; `dev` and
`product` already include `.cursor-plugin/plugin.json`.

## Step 4: Connect GitHub

Cowork: connect GitHub through the connectors in **Customize**; the `gh` CLI
is not part of the Cowork flow.

Cursor and Claude Code: the `gh` CLI must be authenticated, with access to the product repository and
the code repositories the user works on.

```bash
gh auth status
```

If not authenticated, ask the user to run `gh auth login` and follow the prompts
themselves.

## Step 5: Connect ClickUp

Tasks, comments and tags are read and written through the ClickUp connector.
Ask the user to authorize it in the client's connector or MCP settings (`/mcp`
in Claude Code lists the available servers and their authentication state;
Cursor uses Settings, MCP). The hosted ClickUp MCP does not accept a personal
API token.

Verify by asking the user to confirm that ClickUp tools are available and that
a read of their own tasks works.

Explain the tags the stack relies on: `by-auto` and `by-light` authorize
automation on a task; `repo:<owner>/<repo>` names the code repository. Without
those tags nothing is automated.

## Step 6: Workspace roots

Claude Code and Cursor; skip in Cowork. Only needed for local use and local routines. `BYSTACK_WORKSPACE_ROOTS` is a
colon-separated list of folders that contain the user's clones; the default is
`~/Development`. Ask where the clones live, show the exact line to add to the
user's shell profile (for example `export BYSTACK_WORKSPACE_ROOTS="$HOME/Development"`),
and add it only after an explicit yes. Remind the user to restart the terminal
and Claude Code afterwards.

## Step 7: Automation routines

Claude Code and Cursor; in Cowork, tell the user that routines are installed from
Claude Code and skip. Requires the `dev` plugin (Step 3), GitHub (Step 4) and ClickUp (Step 5). Ask
whether the user wants automation now. If yes, ask them to run the command for
their surface. Claude Code and Cowork:

```
/dev:by-install-routines
```

Cursor: `/by-install-routines`. See `references/cursor.md`.

That command asks its own questions (cloud or local mode, repositories, schedule)
and shows what it will create. Do not duplicate or pre-answer them. It is safe
to skip and run later.

## Step 8: Spree resources (optional)

Ask whether the user works on Spree code. If yes, follow `references/spree.md`
(skills and documentation MCP); it has a Cowork section. Both are independent and optional.

## Step 9: Summary

Print a checklist of what was configured, skipped or failed, and the next step
for each pending item. In Claude Code or Cowork, suggest `/dev:by-init` in a
code repository (with `dev`) or `/product:by-spec-new` (with `product`). In
Cursor, suggest `/by-init` or the `by-spec-new` skill. Never print
credentials.
