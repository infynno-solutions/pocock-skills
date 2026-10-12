---
name: to-intent
description: "Record the current conversation as an immutable intent snapshot for the scope just discussed: no interview, just synthesis."
disable-model-invocation: true
---

This skill takes the current conversation and project context and records the intent of one scope. Do NOT interview the user; just synthesize what you already know.

A finished `intent-grilling` session is the best input, not a prerequisite. Whatever hasn't been established goes under Open Questions, never filled in with a guess.

## Where it goes

Intents are immutable and live flat in `intent/`, in the order they were written: the folder listing is the audit trail. Write one new file named `YYYY-MM-DD-HHMM-<key>.md` with the current local time. The key is `project`, a feature's stub slug, or a sub-feature's dotted path (`billing.invoices`).

The current intent for a key is the newest file ending in `-<key>.md`. To change one, write a new file for the same key: a complete snapshot of the scope, carrying forward everything still true, so a reader needs no older file.

If `AGENTS.md` (or `CLAUDE.md`) doesn't point at `intent/` yet, add: "Before working on a project or feature, read its current intent and every intent above it: the newest file in `intent/` ending in `-<key>.md`. Older files are history."

## What goes in it

Write at the level of intent, from the user's perspective. How it gets built (architecture, data model, APIs, file layout, tickets) belongs in a spec; it appears here only as a constraint or a decision the user actually made, with the reason.

In a feature, record only what narrows or adds to the intents above it, and read those rather than restating them.

Set `kind` by what changed since the previous intent for this key: `initial` when there is none, `pivot` when Problem, Users, Outcomes, or fundamental Scope changed, `refinement` for anything else, `retired` when the scope is dropped. A retired intent needs only its header and Changes.

<intent-template>

---
title: <one line on what this intent establishes>
kind: initial | refinement | pivot | retired
decided-by: <the people who made the decisions, as named in the conversation>
---

# Intent: <key>

## Changes

Only when superseding: what changed since the previous intent for this key, and why.

## Problem

What hurts, for whom, and why now. What people do today instead.

## Users

Who uses it, who it acts on, who else is affected.

## Outcomes

A numbered list of what is true once it works. Each outcome names the capability that delivers it.

## Features

Only when the grilling stubbed features: each key, with one line on why it exists.

## Scope

### In

### Out

Including what stays someone else's job: external systems, manual steps.

### Deferred

Wanted, but not now. Say what would bring each one in.

## Constraints

Hard limits the solution must respect, each with its source.

## Success Criteria

Observable checks that tell us it worked.

## Decisions

Each decision, its reason, and the alternatives rejected.

## Assumptions & Risks

What we're betting on, and what would sink it.

## Open Questions

Everything unresolved. Name who decides, where known. For a decision deferred to the client, give the suggestion and link the client questionnaire.

</intent-template>

## Next

After writing, tell the user what's left, each item a next session for `intent-grilling`:

- Every stub without an intent of its own: a key listed under Features in a current intent, with no file.
- When the newest file in `intent/brd/` is a `-changes-requested.md`: every change in it that no intent written since reflects.

When nothing is left, point them to `/to-brd`; open questions travel as its Open items.
