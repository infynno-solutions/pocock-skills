---
name: "to-design"
description: "Record the current conversation as an immutable design snapshot for the scope just discussed: no interview, just synthesis."
disable-model-invocation: true
---

This skill takes the current conversation and project context and records the design of one scope. Do NOT interview the user; just synthesize what you already know.

A finished `design-grilling` session is the best input, not a prerequisite. Whatever hasn't been established goes under Open Questions, never filled in with a guess.

## Where it goes

Designs are immutable and live flat in `design/`, in the order they were written: the folder listing is the audit trail. Write one new file named `YYYY-MM-DD-HHMM-<key>.md` with the current local time. The key is the scope's intent key: `project`, a feature's stub slug, or a sub-feature's dotted path (`billing.invoices`).

The current design for a key is the newest file ending in `-<key>.md`. To change one, write a new file for the same key: a complete snapshot of the scope, carrying forward everything still true, so a reader needs no older file.

When the session hoisted a shared part, also write a `refinement` for the scope it was hoisted to, by the same rules, so the part is defined in one place only.

If `AGENTS.md` (or `CLAUDE.md`) doesn't point at `design/` yet, add: "Before building or changing UI, read the current design for its scope and every design above it: the newest file in `design/` ending in `-<key>.md`. Older files are history."

## What goes in it

Write at the level of design, from the user's perspective: what people see, read, and do. How it gets built (CSS architecture, component code, file layout, tickets) belongs in a spec; it appears here only as a constraint or a decision the user actually made, with the reason.

Record values, not adjectives: hex codes, typeface names, pixel values, durations, copy written out. Each value carries its reason in one clause that ties it to the intent.

**Cite** rules rather than restating them: each rule about what a person may see or do names its source by file and section, so a reader checks the source, not this file.

In a feature, record only what narrows or adds to the designs above it, and read those rather than restating them. Give a pruned layer its heading and one line on why: out of scope per the intent, or settled by the baseline.

Set `kind` by what changed since the previous design for this key: `initial` when there is none, `pivot` when a defining decision changed (brand personality, primary palette, type pairing, layout concept), `refinement` for anything else, `retired` when the scope is dropped. A retired design needs only its header and Changes.

## Check before writing

Read the current sources (the intents of this scope and every scope above it, the last approved BRD and anything newer, the ADRs, the glossary) and every other current design, then check the snapshot:

1. **Rules**: each rule cites a source that says it, and nothing contradicts a current intent, the approved BRD, or an ADR.
2. **Coverage**: each thing the sources put on screen for this scope is designed here, handed to a child, or marked no UI with a reason.
3. **Shared parts**: each part another scope also shows is defined here or cites the design that defines it, and agrees with it.
4. **Names**: parts, states, and terms match the glossary and the designs that define them.
5. **Citations**: each one resolves to a current file and an existing section.

An item that fails stays out of the settled sections. Record it under Open Questions as a gap, a conflict, or a ruling needed, citing both sides, and tell the user what failed. Never settle it with a guess or by picking a side.

<design-template>

---
title: <one line on what this design establishes>
kind: initial | refinement | pivot | retired
decided-by: <the people who made the decisions, as named in the conversation>
sources: <every intent, BRD version, ADR, and design this snapshot cites, by file name>
---

# Design: <key>

## Changes

Only when superseding: what changed since the previous design for this key, and why.

## Baseline

Only when something existed before: what it was and where it came from (Figma file, brand guidelines, live product, codebase tokens). In a redesign, every decision below says whether it keeps or changes it.

## Coverage

A table of everything the sources put on screen for this scope, each with its citation, and where it is designed: a section here, a child key, or "no UI" with the reason.

## Rules

Each rule that changes what a person sees or can do, cited by file and section, and how the design shows it.

## Character

Personality, positioning, voice and tone, with before/after copy.

## Identity

Name and tagline, logo direction and rules, palette (table: role, hex), typefaces, imagery, iconography, motion and sound personality, guardrails.

## Structure

Layout concept, grid, breakpoints, views by role, navigation.

## System

Type scale (table: step, size, line height, weight, use), color tokens (table: token, hex, use, contrast), dark mode, spacing, radius and elevation, components.

## Shared parts

Parts more than one scope shows: those defined here, each with the scopes that show it; and those used from elsewhere, each with the design that defines it.

## Behavior

Interaction states, motion, content states and microcopy, data visualization.

## Access

Keyboard and focus, contrast, reduced motion, touch targets, assistive tech.

## Features

Only when the grilling stubbed features: each key, with one line on what its design must do.

## Constraints

Hard limits the design must respect, each with its source.

## Decisions

Each decision where alternatives were weighed: the choice, its reason, and the alternatives rejected, including any recommendation the user overrode.

## Open Questions

Everything unresolved, each labeled: a **gap** (a rule no source states), a **conflict** (the design and a source disagree), a **ruling needed** (two sources disagree; name who decides), or a **client decision** (give the suggestion and link the client questionnaire).

</design-template>

Once it's written, when more than one current design exists, point the user to `/design-audit`.
