# Cursor

What the Cursor plugin docs say (https://cursor.com/docs/plugins and
https://cursor.com/docs/reference/plugins):

- A Cursor plugin needs `.cursor-plugin/plugin.json`. Skills load from `skills/`.
  Commands load from the files named in that manifest, or from `commands/` when
  the manifest does not set `commands`. The slash-command slug is the filename
  stem: `commands/by-init.md` is `/by-init`, not `/dev:by-init`.
- There is no `/plugin` command. Do not give `/plugin ...` to a Cursor user.
- A local plugin is a real directory at `~/.cursor/plugins/local/<plugin-name>/`
  that contains `.cursor-plugin/plugin.json`. Copy the plugin folder there.
  Cursor skips a symlink whose target sits outside that folder. Then run
  **Developer: Reload Window**.
- `product` and `dev` in `burstyourideas/bystack-sdd` already ship
  `.cursor-plugin/plugin.json`. They do not need a format change to load.
  `dev` also has `commands/` and `agents/`. `product` exposes skills
  (`by-spec-new`, `by-spec-existing`, `by-spec-ship`, and the rest), not
  slash commands.

## Step variants

| Step | Cursor |
|------|--------|
| 2. Private marketplace | Do not run `/plugin marketplace add`. Copy each chosen plugin into `~/.cursor/plugins/local/<name>/` as a real directory. The source folders in a clone of `burstyourideas/bystack-sdd` are `plugins/product` and `plugins/dev`. |
| 3. Choose plugins | Same copy. Recommend `dev` for developers and `product` for people writing Specs. After the copy, **Developer: Reload Window**, then confirm the plugin appears under Settings, Plugins. |
| 4. GitHub | `gh auth status`. If it is not authenticated, the user runs `gh auth login`. |
| 5. ClickUp | Authorize ClickUp under Settings, MCP. The official plugin is OAuth. A personal API token is not accepted by `https://mcp.clickup.com/mcp`. |
| 6. Workspace roots | Same shell line as Claude Code, only after an explicit yes. |
| 7. Routines | The command is `/by-install-routines`, from the `dev` plugin. It asks its own questions. Do not pre-answer them. |
| 8. Spree | See `spree.md`, Cursor section. |

`/dev:by-init` and `/product:by-spec-new` are Claude Code and Cowork names. In
Cursor the dev command is `/by-init`. A new spec is the `by-spec-new` skill,
not a slash command.

If a Cursor screen differs from this description, say so and ask the user what
they see. Do not invent menu labels.
