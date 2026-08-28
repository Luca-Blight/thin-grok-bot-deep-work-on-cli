---
name: thin-grok-bot-deep-work-on-cli
description: Use this when handing off any non-trivial build, investigation, or deep reasoning from Grok Bot. Keep the Bot mesh thin. Cursor CLI / cloud agents or grok CLI run the subtree so work spends plan-pool credits.
---
# Thin Grok Bot, deep work on CLI

## When

Any build, repo investigation, or multi-step reasoning that would burn a long Grok Bot turn.

## Rule

Grok Bot is a mesh of teammates. It decides, routes, and files the ticket. Cursor CLI, Cursor cloud agents, or grok CLI (Grok Build) run the subtree that does the deep work.

## Mesh

You run many named Bots in parallel. One can manage the others. They message each other, share context in threads, and can sit in a group chat so they pass work without you in the middle. They share one cloud computer (files and sign-ins belong to you, not to one Bot). Each Bot has its own desktop and conversation.

Use the mesh to route. Do not spend a long Bot turn investigating or rewriting a repo.

## Setup

Install grok once on the Grok Bot computer. That machine is persistent, so the binary and login stay for every Bot on the account.

```bash
curl -fsSL https://x.ai/cli/install.sh | bash
grok --version
grok login --device-auth
```

On Windows use `irm https://x.ai/cli/install.ps1 | iex`. Default login opens a browser (`grok login`). The Bot computer is headless, so `--device-auth` prints a URL and code you finish on your phone or laptop. Session lands in `~/.grok/auth.json` and is reused. Do not copy someone else's `auth.json`.

Prove from Grok Bot: `grok --version` and a headless `grok -p` that calls `spawn_subagent` and writes a file.

You do **not** install grok on every Cursor cloud agent VM. Those VMs are throwaway. A cloud agent already is the subtree (Cursor plan credits). Install grok there only if that one run needs the grok CLI, not "just to have it."

Cursor CLI on your own machine is a third path: same idea as grok CLI, billed on the Cursor plan. Set it up on the laptop or desktop you already use for Cursor, not on each ephemeral cloud VM.

## Pools

Grok Bot has its own weekly allowance, separate from Cursor and SuperGrok. A Cursor cloud agent started from a Bot draws the Cursor plan (included usage first, then on-demand at the selected model's API price). grok CLI draws the SuperGrok weekly pool (Chat, Imagine, Voice, Build, and API share it).

## Subtree

grok CLI subagents are child sessions with their own context. The parent fans out research, implementation, tests, and review, then takes summaries back. Types: `general-purpose`, `explore`, `plan`. Nesting depth is one. Isolation can be a git worktree. Cursor cloud agents are the same idea on a VM: one agent per stream, reply to that agent for follow-ups.

## Do

1. Name the outcome and the repo (or start a new repo if the work is greenfield).
2. File a ticket if the team uses a tracker. Name the owner.
3. If another Bot owns the lane, message that Bot. Do not do their job in this chat.
4. Hand the problem to a Cursor cloud agent or to grok CLI / Cursor CLI. Do not clone the repo onto Grok Bot.
5. Give symptoms, how to reproduce, constraints, and done-when. Do not prescribe line-by-line edits.
6. Fan-out from the grok or cloud parent only. Follow-ups stay on the same agent.

## Do not

- Investigate or rewrite code inside Grok Bot.
- Clone the repo onto Grok Bot to "just look."
- Dual-run the same task in Grok Bot and a cloud agent.
- Install grok on a Cursor cloud agent VM just to have it. Install once on the Bot computer. Add it to a cloud VM only when that run needs grok CLI.

## grok 1.0.5

Depth is one (children do not get `spawn_subagent`). Parallel and `resume_from` work. `explore` can write despite a read-only prompt, and has no shell. Use `general-purpose` when the child needs a shell. `--no-subagents` does not block spawn. Re-check after you upgrade grok.
