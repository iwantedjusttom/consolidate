---
name: consolidate
description: Turn a project's scattered, hard-won decisions into a small set of living "doctrine" reference docs (like Sam Camp's DESIGN.md and PLAYBOOK.md) — grounded in real examples, discoverable, and read before the relevant work. Use this when the user says "write up our philosophy / principles / conventions / house style", "consolidate what we've learned", "I don't want to start from scratch each time", "capture how we do X", "turn this into a doc", or asks why a past approach worked and wants it made reusable — OR when the agent notices the SAME CLASS of decision recurring across the issue comments/worklogs/memories/code and a pattern has formed. It is the companion to build-loop: build-loop captures the raw layer (the *why* per unit of work — **issue comments** on the GitHub-Issues pipeline, or **worklog entries** on legacy three-file projects, plus memories); consolidate distills that raw layer into doctrine once a pattern has recurred enough. It ALWAYS asks before writing a doc (it never consolidates silently/proactively), and it refuses to consolidate prematurely — every rule must be groundable in a real decision from this project, or it's too early. Trigger it for "make our learnings reusable" intents, not for routine feature work (that's build-loop).
---

# Consolidate

A project accumulates hard-won decisions — how the UI should feel, how a feature gets shaped, what the schema conventions are. Those decisions land **scattered**: in worklogs, in memories, in the code and mockups themselves. Past a certain point, "what does this project's *X* look like?" or "how do we do *Y* here?" stops being answerable without scrolling someone's context window — and the answer gets re-derived (slightly differently) every time.

Consolidation fixes that. It distills the scattered **raw layer** into a small set of **living doctrine docs** — one per axis — that are grounded in real examples, discoverable, and **read before the relevant work**. Sam Camp's `DESIGN.md` (the aesthetic) and `PLAYBOOK.md` (the method) are the canonical exemplars; this skill is the generalization of how they came to be.

The doc is worth only what gets read before work. This whole skill is in service of that one outcome — not of having docs.

## Where this sits (vs build-loop)

These are two halves of one knowledge pipeline; keep them as **separate skills that hand off**, not one mega-skill:

- **build-loop** captures the **raw layer** — the *why* behind each unit of work: **issue comments** on the GitHub-Issues pipeline (or **worklog entries** on legacy three-file projects), plus memories — as a byproduct of every unit of work.
- **consolidate** (this skill) turns that raw layer into **doctrine** once a class of decision has recurred enough to be a pattern.

So this skill *reads* the raw layer — issue comments (or worklogs), memories — and the real artifacts as its raw material. When build-loop work keeps re-deciding the same kind of thing, that's the signal this skill exists. (The split is itself an instance of the doctrine: *one doc per axis, cross-linked — don't build a mega-doc.* Same logic one level up: one skill per job.)

## When to consolidate — and ALWAYS ASK FIRST

**User triggers:** "write up our philosophy / principles / conventions / house style," "consolidate what we've learned," "I don't want to start from scratch each time," "capture how we do X," "turn this into a doc," or asking *why* a past approach worked and wanting it made reusable.

**Agent-noticed trigger:** the **same class of decision** has been made several times across the raw layer — issue comments (github-issues projects) or worklogs (legacy), and memories — a *pattern*, not a one-off. (E.g. three features in a row each decided a leadership-only RLS predicate, or each denormalized a column for a cross-cutting read.)

**The hard rule: ask before you write.** Never consolidate silently or proactively. When you notice a pile forming, **surface the evidence and ask** — list the recurring decisions, say where they live, propose the doc (name + axis + a few of the rules it would hold), and let the user decide whether to spend a doc on it. The decision to consolidate is theirs; your job is to notice the pile and make the case.

## The anti-pattern: premature consolidation

The failure mode is writing doctrine **before there are enough real examples to ground it** — which produces generic fluff that reads like a blog post and helps no one make a real decision. Guard against it with one test:

> **Can you attach a specific, real decision from *this* project to every rule in the doc?**

If a rule can only be illustrated with a made-up or generic example, it isn't doctrine yet — it's a guess. Drop it, or keep capturing in the raw layer until the project earns it. **Show the grounding evidence before you consolidate**, not after.

## The procedure

1. **Find the pile.** Scan the raw layer — **issue comments** (github-issues projects, via `gh issue list --state all` + reading the threads) or **worklogs** (legacy), plus memories — and the relevant code/mockups/schema for the recurring class of decisions. Gather the *real instances* — the actual features/issues/commits/decisions, by name.
2. **Show the evidence + ask.** Present what recurred and where, propose the doc (name, axis, a few example rules each tagged with its real instance), and get an explicit yes. (Per the project owner's standing preference, this skill asks — it does not auto-write.)
3. **Pick the axis.** One doc = one coherent axis (*aesthetic* vs *method* vs *data/RLS conventions* …). If two axes are tangled together, that's **two docs, cross-linked** — never one mega-doc. Name the doc for its axis.
4. **Distill FROM the living sources, never from scratch.** The doc's authority is that it's a *true summary of real artifacts* — the actual tokens, mockups, code, worklog reasoning. Point at them. Do not write it from generic domain knowledge; a doc that could have been written without the project is the wrong doc.
5. **Ground every rule in its originating example.** Each principle names the real feature/decision that birthed it. Concrete beats abstract — that is the entire difference between a doc people reach for and one they read once.
6. **Make it discoverable and load-bearing.** Link it from the project's always-loaded index (`CLAUDE.md` or equivalent) with a **"read before \<the relevant work\>"** instruction, so it's opened at the decision moment, not discovered by accident.
7. **Prove it with a worked example.** End the doc by applying it to a concrete *upcoming* case — it demonstrates the leverage and gives the next person a template. (PLAYBOOK.md closed by applying itself to the next feature; that feature was then built the same day.)
8. **Record it and keep it living.** Drop a worklog note that you consolidated and from what. State the doc's own governing rule inside it: *when it's wrong, change it on purpose; re-consolidate when reality drifts.* A doctrine doc is a living distillation, not a tablet.

## Best practices (the distilled rules)

- **Capture continuously, consolidate occasionally.** No raw layer → nothing to distill. Most of the value is created by build-loop; this skill just harvests it at the right moment.
- **Recurrence is the trigger, not reflex.** Wait until it's a pattern. A light process moving work beats a heavy one being tuned.
- **Grounded > abstract, every time.** Every rule carries its real example or it doesn't belong.
- **One axis per doc; cross-link.** Split when it gets big; never merge unrelated axes.
- **Discoverable or dead.** If it isn't linked with a "read before X," it won't be read at decision time, and an unread doc is worthless.
- **Living, not carved.** The doc sharpens with use. Re-consolidate on drift.
- **Ask before writing.** The owner decides whether a pile is worth a doc.

## The canonical exemplars

- **`DESIGN.md` (the aesthetic axis).** Consolidated at SC-047 from ~6 accumulated brand/shell/nav **memories** + the calm tokens in `app.html` + the `calm-*.html` mockups. Linked from CLAUDE.md: *"read before building any UI."* Turned "what does Sam Camp look like?" from tacit into a single answerable source.
- **`PLAYBOOK.md` (the method axis).** Consolidated from two features' **worklogs** (Directory SC-002, Buddy SC-006) after the owner said *"I don't want to start from scratch each time."* Every rule pinned to the feature that birthed it; closed with a worked example applying it to SC-005 — which was then built the same day, citing the doc back. Linked from CLAUDE.md: *"read before shaping a feature."*

If the project uses build-loop's git flow, a doctrine doc is a **docs change → its own branch + PR** (like PLAYBOOK.md's `docs/playbook`), *not* a tracking-file bookkeeping commit to `main`.

## Don't over-build

Mirror build-loop's closing rule: the system is worth only what flows through it. Don't consolidate by reflex, don't spawn a doc per topic, don't polish format over substance. A grounded one-pager that's actually read before work beats a polished manual that isn't. When you're unsure whether a pile is ripe — it isn't yet. Keep capturing, and ask later.
