---
name: to-brd
description: "Combine every current intent into a client-facing Business Requirements Document for approval, or record the client's response to one: no interview, just synthesis."
disable-model-invocation: true
---

This skill combines the current intent of the project and of every feature into one **Business Requirements Document** (BRD) the client can review and sign. Do NOT interview the user; the intents are the only source. Whatever they don't establish goes under Open items, never filled in with a guess.

The current intent for a key is the newest file in `intent/` ending in `-<key>.md`. Skip keys whose current intent is `retired`.

## Where it goes

BRDs are immutable and live in `intent/brd/`. Write one new file named `YYYY-MM-DD-HHMM-v<major>.<minor>.md` with the current local time.

The first BRD is version 1.0. After that, look at the intents written since the previous BRD: any `pivot` bumps the major version, anything else the minor. If no intent was written since, say so and stop.

## Writing

Write for the client, who knows their business but not our process:

- **Plain English**, at about a 6th-grade reading level: short sentences, everyday words, the client's own names for their things. Any term you can't avoid goes in the Glossary.
- Leave out internal working: scope keys, rejected alternatives, who decided, solution candidates.
- Each feature intent becomes a subsection of Features, in the order its parent lists it; a sub-feature becomes a subsection of its feature.
- Use only headings, paragraphs, lists, and tables, so the file converts cleanly to PDF.

"What changed" compares against the last approved version, or the previous version if none is approved yet. Build it from the Changes sections of the intents written since, and call out any pivot as a change of direction.

<brd-template>

# <Project name>: Business Requirements

| | |
|---|---|
| Version | <x.y> |
| Date | <date> |
| Status | For approval |
| Prepared by | <team> |

## Revision history

| Version | Date | Status | Summary |
|---|---|---|---|

One row per BRD, oldest first. Status comes from its response record: Approved, Changes requested, or Awaiting response.

## What changed since version <x.y>

Only when there is an earlier version: each change in one or two sentences, grouped by feature, with the reason.

## 1. Summary

Half a page: what we are building, for whom, and why. Write it last.

## 2. Background and business need

## 3. Goals and how we will measure them

## 4. Who it is for

## 5. Scope

### 5.1 Included

### 5.2 Not included

### 5.3 Later phases

## 6. Features

### 6.1 <feature name>

**What it does:**

**Who uses it:**

**How we will know it works:** a numbered list, each item something the client can check.

**Not included:**

## 7. Your responsibilities

What the client provides or does: data, access, decisions, people.

## 8. Constraints, assumptions and dependencies

## 9. Risks

Each risk, and what we will do about it where that's agreed.

## 10. Open items

Each item with our suggestion and who decides.

## Glossary

## Sign-off

By signing, you approve version <x.y> of this document as the agreed requirements.

| Name | Role | Signature | Date |
|---|---|---|---|
| | | | |

</brd-template>

Once it's written, remind the user to bring the client's response back to `/to-brd`.

## Recording the client's response

When the user reports the client's response to a BRD, write a response record instead of a BRD: `intent/brd/YYYY-MM-DD-HHMM-v<x.y>-approved.md` or `...-v<x.y>-changes-requested.md`. The last approved version is the one in the newest `-approved.md` file.

<response-template>

---
version: <x.y>
outcome: approved | changes-requested
by: <name, role>
date: <date of the client's response>
signed-copy: <where the signed PDF is kept, when there is one>
---

## Changes requested

Only for changes-requested: each change in the client's own words. These are the input to the next `intent-grilling`.

</response-template>

After a changes-requested record, point the user to `intent-grilling` for each scope the changes touch.
