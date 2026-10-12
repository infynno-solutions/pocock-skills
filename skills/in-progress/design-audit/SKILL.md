---
name: "design-audit"
description: "Check every current design against the intents, the BRD, and each other, and report contradictions, gaps, disagreements, and rulings needed: no interview, just checking."
disable-model-invocation: true
---

This skill checks the whole set of current designs and writes a report. Do NOT interview the user, and change no design, intent, or BRD: the report says what to fix and which session fixes it.

Read the current intent and the current design of every key (the newest file ending in `-<key>.md` in `intent/` and in `design/`, skipping retired ones), the last approved BRD in `intent/brd/` and anything newer, `GLOSSARY.md`, and the ADRs in `docs/adr/`.

Write the report to `design/audits/YYYY-MM-DD-HHMM.md` with the current local time. Once written, it is a record: the next audit is a new file.

## What to check

Sort every finding into one group:

1. **Contradictions**: a rule or value in a design that contradicts a current intent, the approved BRD, or an ADR. This includes a **stale** design, one whose `sources` name an intent or BRD that is no longer current, where the newer source changed something the design shows. Fixed in `/design-grilling` for that scope.
2. **Gaps**: something the sources put on screen that no design covers, including a key with UI that has no current design, and a stub never designed. Fixed in `/design-grilling` for the scope that should own it.
3. **Disagreements**: two designs that define the same part, state, term, or value differently, or a part defined in one feature's design that another scope also shows. Fixed by hoisting it into the design of the nearest scope above both.
4. **Rulings needed**: two sources that disagree (an intent and the BRD, an intent and an ADR, two intents). No design change fixes these. Say which is newer and what explains the gap (an intent change not yet in an approved BRD, a changes-requested response not yet grilled), and who rules. Fixed in `/intent-grilling`, then `/to-brd`.
5. **Cleanup**: a stale source that changed nothing the design shows, a broken citation, a name off the glossary, a missing template section. Fixed in the next `/to-design` for that scope.

Every finding cites both sides by file and section and quotes the lines that disagree. Rate its severity: **high** when a person would see or do the wrong thing, **medium** when something is missing or inconsistent, **low** for cleanup.

<audit-template>

# Design audit: <date>

**Checked:** <every file read>

## Where things stand

A few lines on what the designs and sources agree on, so the findings read in context.

## 1. Contradictions

### C1: <one line>

**Design:** <file, section>: "<quoted>"

**Source:** <file, section>: "<quoted>"

**Severity:** high | medium | low

**Fix:** <what changes, in which session>

## 2. Gaps

## 3. Disagreements

## 4. Rulings needed

## 5. Cleanup

## Next sessions

The sessions to run, in order: rulings first, since designs hang on them; then hoisting shared parts; then each scope's `/design-grilling`, highest severity first.

</audit-template>

Once it's written, point the user to the first session under Next sessions.
