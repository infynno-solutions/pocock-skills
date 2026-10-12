# Layers

What each layer covers, and what a good recommendation weighs. Visit only the items the scope needs; in a feature, most of Character, Identity, and System come settled from the designs above it.

## Character

- **Personality**: 3–5 adjectives a competitor couldn't claim.
- **Positioning**: whether the brand meets its category's expectations or breaks them, and why. One line: for [users], [name] is the [category] that [difference].
- **Voice and tone**: the voice is fixed ("direct, no fluff"); the tone flexes by moment (confirmation, error, onboarding, marketing). Give 2–3 before/after lines of copy, and the words the brand stays away from.

## Identity

- **Name and tagline**, only when not already fixed: the rationale, and a flag that domain and trademark checks are the user's. The tagline grows from the positioning line.
- **Logo**: wordmark, symbol, combination mark, or monogram, weighed against name length and the smallest size it must survive (a favicon). Decided as a direction in words for a designer or image tool to execute, with clear space, minimum size, and misuse rules.
- **Palette**: primary and supporting colors as hex values, and a neutral scale (how many steps, warm or cool). Check it on light, on dark, in grayscale, and at small sizes.
- **Typefaces**: display and text faces, and the character each carries (geometric, humanist, serif), tied to Personality.
- **Imagery**: photography, illustration, 3D, or none, weighed against budget and how consistently it can be kept up. Then its treatment: subjects, grading, and whether people appear; or illustration style and complexity.
- **Iconography**: line, filled, or duotone; stroke weight; corner treatment, in agreement with the typefaces.
- **Motion and sound personality**, only where the brand moves or sounds: snappy or soft easing; notification sounds, video idents.
- **Guardrails**: what the brand never does with its logo, colors, or tone.

## Structure

- **Layout concept**: one sentence ("a focused single-column reading experience", "a dense multi-panel dashboard"). A defining decision.
- **Grid**: columns, gutter, margins, max content width, fixed or fluid. Alignment, weighed against content type: long-form text reads best left-aligned with lines under ~80 characters.
- **Breakpoints**: concrete pixel values, mobile-first or desktop-first, and what changes at each beyond reflow (nav pattern, density, what collapses).
- **Views by role**: what each user sees and can do on each screen, from the rules the intent states, cited rather than restated.
- **Navigation**: the primary pattern (top nav, sidebar, tab bar, command palette, hybrid), weighed against the number of destinations, the platforms, and how often each is used; secondary navigation (breadcrumbs, in-page tabs, filters); how users always know where they are.

## System

- **Type scale**: every step (display, h1–h6, body, small, caption) with size, line height, letter spacing, and weight, from a stated ratio; the weights in use and what each signals. It uses Identity's typefaces, or names the deliberate difference (a serif for marketing, a sans for the product).
- **Color tokens**: the palette as semantic tokens, each with a hex value: surfaces, text (primary, secondary, disabled), border, actions, status (success, warning, error, info). Every text/background pair meets WCAG AA (4.5:1 for body text, 3:1 for large text and UI parts); adjust any pair that falls short.
- **Dark mode**: in or out. If in, a reversed palette or a distinct one (brand colors usually need desaturating on dark).
- **Spacing**: base unit and step sequence; component sizes (small, medium, large) where elements recur.
- **Radius and elevation**: radius steps that follow hierarchy; how many elevation levels, and whether shadows, borders, or both carry them.
- **Components**: only those the scope needs, each with a style direction (a component another scope also shows is a shared part, defined in their nearest common scope): buttons by hierarchy (primary, secondary, tertiary, destructive), inputs with validation states, cards and list items, dialogs vs panels vs toasts and when each is used, tables, tags and status badges.

## Behavior

- **Interaction states**: hover, focus, active, and disabled for every interactive element.
- **Motion**: default durations and easing (150–200ms ease-out for micro-interactions is a fair starting point); motion answers what the user does (opening, confirming, expanding).
- **Content states**: empty (and the action it prompts), loading (skeleton, spinner, or progressive, by load time and content shape), error (specific, actionable, in the brand's voice), success (inline, toast, or redirect).
- **Imagery and icons in the product**: where imagery appears in the interface versus marketing only; one named icon set.
- **Data visualization**, when the scope has charts: chart conventions, categorical and sequential color, and a chart palette drawn from the brand yet distinct from action colors.

## Access

- **Keyboard and focus**: a full keyboard path, and a visible focus style on every interactive element.
- **Contrast**: cross-checked against System's tokens.
- **Reduced motion**: what `prefers-reduced-motion` turns off or swaps.
- **Touch targets**: at least 44×44px.
- **Assistive tech**: labels for icon-only controls, roles and states for custom components.

## Unearned defaults

These turn up in designs because they are safe, not because a brief asked for them. Recommend one only with a grounding from the intent, and name that grounding when you do:

- a warm cream background with a high-contrast serif and a terracotta accent;
- a near-black background with a single acid accent;
- one radius and one soft grey shadow on every card, whatever its place in the hierarchy;
- tracked-out all-caps eyebrows above every heading;
- meta strings joined by middle dots, or labels styled "WORD: fragment";
- a monospace face as decoration for small labels;
- an arrow appended to every link and button;
- 01/02/03 markers on content that isn't sequential;
- fade-and-slide-up on every section, hover-lift on every card.
