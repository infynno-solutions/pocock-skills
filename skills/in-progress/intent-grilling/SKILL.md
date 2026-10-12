---
name: intent-grilling
description: Grill the user on the intent behind a project or feature, before any spec or code. Use when starting a project or feature, or when revisiting why one exists.
---

Call the Skill tool with "grilling", and run it with the design tree rooted at one **scope**'s intent: what it is for, never how it is built. A scope is the project, a feature, or a feature within a feature, named by a key: `project`, `billing`, `billing.invoices`.

Ask **one question at a time**, overriding grilling's whole-frontier rounds. Pick the frontier question the most others hang on, give your recommended answer, and wait for the user's answer before asking the next.

Before the first question, read the current intent of this scope and of every scope above it. The current intent for a key is the newest file in `intent/` ending in `-<key>.md`. Their answers are settled prerequisites, so the frontier starts below them. When this scope already has an intent, grill what has changed since.

When the newest file in `intent/brd/` is a `-changes-requested.md`, read it too: the requested changes that touch this scope, and that no intent written since reflects, go on the frontier first.

The tree grows down through these layers, each hanging off the ones above it. In a feature, each layer narrows its parent's:

1. **Problem**: what hurts, for whom, why now, and what people do today instead.
2. **Users**: who uses it, who it acts on, who else is affected.
3. **Outcomes**: what is true once it works, and the capabilities that make it true.
4. **Scope**: in, out, deferred, and what stays someone else's job (external systems, manual steps).
5. **Constraints & success**: hard limits (budget, deadline, compliance, platforms), and how we'll know it worked.
6. **Assumptions & risks**: what we're betting on, and what would sink it.

These are roots, not a checklist: every answer grows its own branches, and the frontier decides what gets asked when.

**Stub** every feature that is large enough to warrant its own intent: give it a slug and one line on why it exists, and leave it unopened: it gets its own session later. A stub counts as visited. Its key is its slug, or the parent's key plus `.<slug>` when the parent is itself a feature.

**Five-whys** every solution until the underlying intent or hard constraint is exposed. When an answer names a stack, a feature, or an architecture, ask what problem it solves. It enters the tree as a constraint only when it is one (an existing system, a team's skills, a contract); otherwise record the problem behind it and keep the solution as a candidate.

**Defer** what the client owns. The person running the session may be a product manager or FDE standing in for a client. When they say a decision is the client's, take their answer (or your recommendation, if they endorse it) as the **suggestion**, mark the branch deferred, and keep going on every frontier question that doesn't hang on it.

When the whole frontier hangs on deferred decisions, stop. Point the user to `/to-intent-questionnaire` for the client's questions, then `/to-intent` to snapshot what's settled, with the deferred decisions as its Open Questions.

When the client's answers come back, resume from the questionnaire. An answer that matches the suggestion settles its branch. One that differs reopens every branch below it, and when it changes Problem, Users, Outcomes, or fundamental Scope, name it a **pivot** before grilling what it reopened.

Periodically summarize the current model so the user can verify that the tree still reflects their intent.

When the user confirms shared understanding, point them to `/to-intent`.
