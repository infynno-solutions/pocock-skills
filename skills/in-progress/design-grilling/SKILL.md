---
name: "design-grilling"
description: Grill the user on the design of a project or feature, after its intent and before any UI code. Use when designing or redesigning a product, brand, or design system, or when revisiting why one looks the way it does.
---

Call the Skill tool with "grilling", and run it with the design tree rooted at one **scope**'s design: how it looks, reads, and behaves for the people using it, never how it is built. A scope is the project, a feature, or a feature within a feature, keyed as in `intent/`: `project`, `billing`, `billing.invoices`.

Ask **one decision at a time**, overriding grilling's whole-frontier rounds. Pick the frontier decision the most others hang on, give your recommendation, and wait for the user's answer before the next. A system (the type scale, the color tokens, the spacing scale) is one decision: propose it whole. The **defining** decisions (brand personality, primary palette, type pairing, layout concept) each get a question of their own.

Before the first question, read the **sources**:

- the current intent of this scope and of every scope above it: the newest file in `intent/` ending in `-<key>.md`;
- the last approved BRD (the version named in the newest `-approved.md` in `intent/brd/`), and any BRD or changes-requested response newer than it;
- the current design of this scope and of every scope above it, and every other current design for the shared parts it defines: the newest file in `design/` ending in `-<key>.md`;
- `GLOSSARY.md` (or the one `GLOSSARY-MAP.md` points to for this scope), and the ADRs in `docs/adr/`.

Their answers are settled prerequisites, so the frontier starts below them. When this scope already has a design, grill what has changed since, in the design and in its sources. When it has no intent, point the user to `/intent-grilling` first; if they carry on, record what you learn about problem and users as assumptions.

**Inventory** what the sources put on screen for this scope: each capability an outcome names, each user's views and actions, each success criterion someone checks on screen, each in-scope item, and each of the BRD's "How we will know it works" checks for this feature. Every entry ends designed here, handed to a stubbed child, or marked no UI with a reason. An unassigned entry is still on the frontier.

**Audit** the **baseline** too: whatever already exists for this scope, such as a Figma file, brand guidelines, a live product, or design tokens in the codebase. Finding it is your job, under grilling's facts rule; check for a Figma connector every session, and without one, ask the user for exports (screenshots, Dev Mode CSS, a variables export). Unless the intent calls for a redesign, what the baseline settles is a prerequisite. In a redesign, every decision keeps or changes the baseline: say which. Where the baseline contradicts itself (three near-identical blues), put that to the user as a decision.

The tree grows down through these layers, each hanging off the ones above it. In a feature, each layer narrows its parent's:

1. **Character**: who the brand is and how it sounds.
2. **Identity**: the marks, colors, type, and imagery that carry it.
3. **Structure**: how screens are laid out and moved between.
4. **System**: the type, color, spacing, and components the interface is built from.
5. **Behavior**: how the interface responds, moves, and fills its empty, loading, and error moments.
6. **Access**: how everyone can use it, whatever their input or ability.

These are roots, not a running order: every answer grows its own branches, and the frontier decides what gets asked when. [`references/layers.md`](references/layers.md) holds what each layer covers and what a good recommendation weighs; read a layer's section before its first question. A layer is visited when every item in its section is settled, deferred, stubbed, or **pruned** (out of scope per the intent, or fully settled by the baseline). Say why when you prune.

**Cite** every rule. What a person may see or do (roles, visibility, money, offline behavior, regional rules such as tax) is intent, not design: the design cites the source by file and section and decides only how the rule shows. A rule the design needs that no source states is a **gap** in the intent: defer it to `/intent-grilling` and design around it.

**Escalate** disagreements between sources. When two sources disagree (the intent and the BRD, an intent and an ADR, two intents), no design decision settles it. Name both, say which is newer and what explains the gap (an intent change not yet in an approved BRD, a changes-requested response not yet grilled), mark the branch **ruling needed** with who decides, and keep going on everything that doesn't hang on it.

**Hoist** shared parts. A part more than one scope shows (the navigation shell, a status chip, how money is displayed, a role badge, an empty-state pattern) is defined once, in the design of the nearest scope above all the scopes that show it. When another design already defines it, it is a prerequisite: cite it, and raise any change as a decision for that design's scope. When none does, hoist it: decide it for that scope, and `/to-design` records it there.

**Name** parts, states, and terms as the glossary and the designs that define them do, in labels and microcopy too. A term the glossary lacks is an open question for `domain-modeling`, not a name to invent.

**Ground** every recommendation: give specific values (hex codes, typeface names, pixel values, durations) and one clause naming the problem, user, outcome, or constraint in the intent that makes them right for this scope. A recommendation that would fit any project is still ungrounded; find the intent line it answers to.

**Show** visual decisions when you can: render the palette, the type pairing, or the component beside the recommendation, so the user answers what they see.

**Five-whys** every reference. When an answer names a brand, a site, a trend, or a component library, ask what quality it carries for these users. It enters the tree as a constraint only when it is one (a mandated brand, an existing design system, a contract, an ADR); otherwise record the quality and keep the reference as an example.

**Stub** every feature large enough to warrant its own design: give it its key (the feature's intent key, when it has one) and one line on what its design must do, and leave it unopened: it gets its own session later. A stub counts as visited.

**Defer** what the client owns. The person running the session may be a designer, product manager, or FDE standing in for a client, and brand decisions are often the client's. When they say a decision is the client's, take their answer (or your recommendation, if they endorse it) as the **suggestion**, mark the branch deferred, and keep going on every frontier decision that doesn't hang on it.

When an answer contradicts a settled decision (a loud palette under a quiet personality), name the **conflict** and ask which one holds before going on.

When the whole frontier hangs on deferred decisions, stop. Point the user to `/to-design-questionnaire` for the client's questions, then `/to-design` to snapshot what's settled, with the deferred decisions as its Open Questions.

When the client's answers come back, resume from the questionnaire. An answer that matches the suggestion settles its branch. One that differs reopens every branch below it, and when it changes a defining decision, name it a **pivot** before grilling what it reopened.

Periodically summarize the current model so the user can verify that the tree still reflects their design.

**Reconcile** before asking for shared understanding: walk the inventory, the Constraints and Out list of every intent you read, the BRD's sections for this scope, and the parts other designs define, and put every mismatch to the user as a decision, a gap, or a ruling needed. When the user then confirms shared understanding, point them to `/to-design`.
