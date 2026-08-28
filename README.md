# Thin Grok Bot, deep work on CLI

A skill for [Grok Bot](https://x.ai/bot) and Cursor: keep the Bot mesh thin, and hand deep builds or investigations to Cursor CLI, Cursor cloud agents, or grok CLI (Grok Build).

## Why

Grok Bot is a mesh of named teammates. They message each other, sit in group chats, and share one cloud computer. That mesh is for routing. Long Bot turns burn the Grok Bot weekly pool.

Cursor cloud agents draw the Cursor plan. grok CLI draws the SuperGrok weekly pool. Both give you a subtree: child sessions with their own context.

## Install

```bash
npx skills add Luca-Blight/thin-grok-bot-deep-work-on-cli
```

After this plugin is listed:

- Grok Bot: Settings, Plugins, install `thin-grok-bot-deep-work-on-cli`
- Cursor: Customize, find the plugin, Install

Until then, clone this repo and load it as a local plugin:

```bash
git clone https://github.com/Luca-Blight/thin-grok-bot-deep-work-on-cli.git
# Cursor: symlink into ~/.cursor/plugins/local/thin-grok-bot-deep-work-on-cli
# Grok Bot already has the skill if you created it there; this repo is the public copy
```

Invoke with `/thin-grok-bot-deep-work-on-cli` or mention it when handing off a build.

## Setup grok CLI (once)

On the persistent Grok Bot computer:

```bash
curl -fsSL https://x.ai/cli/install.sh | bash
grok --version
grok login --device-auth
```

Do not install grok on every Cursor cloud agent VM. Those VMs are throwaway. A cloud agent already is the subtree.

## License

MIT
