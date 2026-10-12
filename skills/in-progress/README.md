# In Progress

Beta. These skills are public on purpose: try them and tell me what breaks. They're excluded from the plugin and the top-level README until they graduate to a stable bucket, they get no docs pages, and they can change or disappear without warning.

The plugin won't give you these. Install one directly:

```bash
npx skills@latest add mattpocock/skills --skill=<name>
```

- **[loop-me](./loop-me/SKILL.md)**: Grill yourself into implementable workflow specs over multiple sessions, using the current directory as a stateful workspace. User-invoked.
- **[writing-beats](./writing-beats/SKILL.md)**: Shape an article as a journey of beats, choose-your-own-adventure style. Pick a starting beat, write only that beat, then pivot to the next, until the article reaches a natural end.
- **[writing-fragments](./writing-fragments/SKILL.md)**: Grilling session that mines you for fragments (heterogeneous nuggets of writing) and appends them to a single document as raw material for a future article.
- **[writing-shape](./writing-shape/SKILL.md)**: Take a markdown file of raw material and shape it into an article paragraph by paragraph, arguing format choices at each step.
- **[claude-handoff](./claude-handoff/SKILL.md)**: Hand the current conversation off to a fresh background agent that picks up the work immediately, seeded with a handoff summary via `claude --bg`. User-invoked.
- **[setup-ts-deep-modules](./setup-ts-deep-modules/SKILL.md)**: Wire dependency-cruiser into a TypeScript repo so each package is a deep module: implementation hidden in subfolders, reachable only through its entry-point files, tests exercising it through those. User-invoked.
- **[intent-grilling](./intent-grilling/SKILL.md)**: Grill the intent of a project or feature (problem, users, outcomes, scope) before any spec or code. Model-invoked.
- **[to-intent](./to-intent/SKILL.md)**: Snapshot the current conversation as an immutable intent file under `intent/`. User-invoked.
- **[to-intent-questionnaire](./to-intent-questionnaire/SKILL.md)**: Turn decisions deferred to the client during intent-grilling into an ordered questionnaire. User-invoked.
- **[to-brd](./to-brd/SKILL.md)**: Combine current intents into a client-facing Business Requirements Document, or record the client's response. User-invoked.
- **[design-grilling](./design-grilling/SKILL.md)**: Grill the design of a project or feature (character through access) after its intent and before UI code. Model-invoked.
- **[to-design](./to-design/SKILL.md)**: Snapshot the current conversation as an immutable design file under `design/`. User-invoked.
- **[to-design-questionnaire](./to-design-questionnaire/SKILL.md)**: Turn design decisions deferred to the client during design-grilling into an ordered questionnaire. User-invoked.
- **[design-audit](./design-audit/SKILL.md)**: Check every current design against the intents, the BRD, and each other; report contradictions, gaps, and rulings needed. User-invoked.
