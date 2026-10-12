---
name: "to-design-questionnaire"
description: "Turn the design decisions deferred to the client during design-grilling into an ordered questionnaire, with a suggestion for each: no interview, just synthesis."
disable-model-invocation: true
---

This skill takes the design decisions deferred to the client in the current conversation and writes them up as a questionnaire the designer, product manager, or FDE can send. Do NOT interview the user; each deferred decision already carries its suggestion, the user's answer or a recommendation they endorsed.

A fully blocked frontier is the usual moment to run it, not a prerequisite. If nothing has been deferred, say so and stop.

Only client decisions belong here. A ruling needed between two sources, or a gap in the intent, goes to `/intent-grilling`, where the client's answer lands in the intent first.

Write it to `design/questions/YYYY-MM-DD-HHMM-<key>.md` with the current local time. Once sent, it is a record: write a new questionnaire rather than editing it.

## Order

Order the questions as a logical sequence: every question comes after the ones it depends on, and among those that are free, the one most others hang on comes first. A question downstream of another assumes the suggested answer above it, and says so.

## Writing

Write for someone who wasn't in the session: plain language, one decision per question, none of the session's keys or internal terms.

Make every suggestion concrete enough to react to: hex codes beside a color name, typeface names beside a sample line, copy written out in full, and a rendered preview wherever the session made one.

Mark every answer that would pivot the design, meaning one that changes a defining decision (brand personality, primary palette, type pairing, layout concept), and say what it would reopen, so the client sees the weight of that answer.

<questionnaire-template>

# Questions for <client>: design of <scope, in plain words>

**Why we're asking:** one paragraph on what we're deciding and what's already settled, so each answer lands in context.

**How to answer:** Go in order. Each question carries our suggestion, and agreeing with it is a full answer. Where you disagree, later questions that depend on it may no longer apply: answer what you can and tell us.

### Q1: <one decision, as a question>

_Why it matters:_ <what hangs on it>

**Our suggestion:** <the suggestion, with its reason>

**Depends on:** <earlier questions> (only when it does)

**Would change direction if:** <the answer that would pivot the design, and what it would reopen> (only when one exists)

**Your answer:**

>

</questionnaire-template>
