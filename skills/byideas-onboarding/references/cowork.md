# Cowork

What the platform documentation says (https://claude.com/docs/plugins/platform-support):

- Skills and commands load in Cowork. A command is run by typing
  `/plugin-name:command`, for example `/byideas-onboarding:start`.
- Plugins are added in **Customize > Plugins** (claude.ai or the desktop app).
  A plugin installed there is attached to the account, and it also reaches
  Claude Code as a synced plugin at the next session start.
- A marketplace you add yourself can be a GitHub repository. There is a limit of
  25 marketplaces per account, per organization. **Add > Upload plugin** accepts
  a zip of the plugin folder.
- There is no `/plugin` command and no `claude` CLI in Cowork. Do not give
  `/plugin ...` or `claude mcp add ...` commands to a Cowork user.

## Step variants

| Step | Cowork |
|------|--------|
| 2. Private marketplace | In **Customize > Plugins**, add the GitHub repository `burstyourideas/bystack-sdd` as a marketplace. Access requires membership of the `burstyourideas` GitHub organization. |
| 3. Choose plugins | Install the chosen plugins from that marketplace in **Customize > Plugins**. Agents and hooks of `dev` load in Cowork; the automation routines do not (see below). |
| 4. GitHub | Connect GitHub from the connectors in **Customize**. |
| 5. ClickUp | Connect ClickUp from the connectors in **Customize**. Tags work the same as in Claude Code. |
| 6. Workspace roots | Skip. |
| 7. Routines | Skip. `/dev:by-install-routines` is run from Claude Code; tell the user to do it there. |
| 8. Spree | See `spree.md`, Cowork section. |

If a Cowork screen differs from this description, say so and ask the user what
they see; do not invent labels.
