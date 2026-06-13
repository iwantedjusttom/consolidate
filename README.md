# consolidate

Turn a project's scattered, hard-won decisions into a small set of living **"doctrine" reference docs** (think `DESIGN.md` and `PLAYBOOK.md`) — grounded in real examples, discoverable, and read before the relevant work.

It's the companion to **build-loop**: build-loop captures the *raw* layer (the *why* per unit of work — issue comments on the GitHub-Issues pipeline, or worklog entries on legacy projects, plus memories); consolidate distills that raw layer into doctrine **once a pattern has actually recurred**.

## Principles

- **Always asks before writing a doc** — it never consolidates silently or proactively.
- **Refuses to consolidate prematurely** — every rule must be groundable in a real decision from this project, or it's too early.

## Triggers

- "write up our philosophy / principles / conventions / house style"
- "consolidate what we've learned", "I don't want to start from scratch each time"
- "capture how we do X", "turn this into a doc"
- asking why a past approach worked and wanting it made reusable
- or when the same *class* of decision keeps recurring and a pattern has formed.

Not for routine feature work — that's **build-loop**.

## Install

```powershell
git clone https://github.com/iwantedjusttom/consolidate.git
New-Item -ItemType Junction -Path "$HOME\.claude\skills\consolidate" -Target "<path>\consolidate"
```
