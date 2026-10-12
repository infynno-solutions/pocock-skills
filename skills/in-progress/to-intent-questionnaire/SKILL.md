---
name: to-intent-questionnaire
description: "Turn the decisions deferred to the client during intent-grilling into an ordered questionnaire, with a suggestion for each: no interview, just synthesis."
disable-model-invocation: true
---

This skill takes the decisions deferred to the client in the current conversation and writes them up as a questionnaire the product manager or FDE can send. Do NOT interview the user; each deferred decision already carries its suggestion, the user's answer or a recommendation they endorsed.

A fully blocked frontier is the usual moment to run it, not a prerequisite. If nothing has been deferred, say so and stop.

Write it to `intent/questions/YYYY-MM-DD-HHMM-<key>.md` with the current local time. Once sent, it is a record: write a new questionnaire rather than editing it.

## Order

Order the questions as a logical sequence: every question comes after the ones it depends on, and among those that are free, the one most others hang on comes first. A question downstream of another assumes the suggested answer above it, and says so.

## Writing

Write in **plain English**, at about a 6th-grade reading level. The client wasn't in the session and may not read English easily.

- Short sentences, one idea each, in everyday words. No technical terms, acronyms, or session keys. Call the client's things by the client's own names for them.
- Give context **just in time**: one or two sentences right above each question, saying what it is about in the client's world. No long background section up front.
- Ground every question in a concrete example from the client's day: "When a customer calls to change an order, ..."
- Offer choices wherever the question has natural options, with the suggestion first and "Something else" last. Picking is easier than writing. When there are no clear options, write the suggestion as "We suggest".
- Where an answer would pivot the scope (change its Problem, Users, Outcomes, or fundamental Scope), say in plain words what we would have to rethink.

Before writing the file, reread each question as the client: swap any word they might have to look up, and split any sentence that needs a second read.

<questionnaire-template>

# Questions about <the scope, in the client's words>

<Two or three short sentences: what we are building for them, why we need their answers, and roughly how long this takes.>

**How to answer:** Please answer in order. Each question shows what we suggest. If you agree, just write "Yes". If not, tell us what you want in your own words. "I'm not sure" is a fine answer too.

### 1. <the question, in one short sentence>

<One or two short sentences on what this is about, with an example from their day.>

**Your choices:**

- **A. <the suggestion> (we suggest this),** because <short reason>
- B. <another option>
- C. Something else: tell us

**Only answer this if:** <you chose A in question 1> (only when it depends on an earlier question)

**This is a big one:** <if you choose B, we will need to rethink ...> (only when an answer would pivot)

**Your answer:**

>

### Anything else?

Is there anything we didn't ask that we should know?

>

</questionnaire-template>
