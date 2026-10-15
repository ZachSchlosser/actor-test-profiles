# Test 3 (Expert Read): how the lens layer is generated

## What a lens is

A lens is a short reading of one actor's pre-cutoff record, written the way one of four experts would notice it. The plain record (persona + rows) states what happened, on what date, with what source. The lens layer exists to pull out what the record implies but does not state: what a pattern of choices adds up to, what the actor does just before and just after pressure lands, what it never does. Each lens reads the same rows through one professional habit of attention. Four experts, four habits, four short notes per actor.

## The four lenses and what each looks for

**Psychologist.** Reads the actor's choices as evidence of how it decides under pressure. Looks for: what it says before it acts (promises, warnings, framing), how it reacts to being named, sanctioned, summoned or beaten to a market (speed, tone, walk-backs, silence), and what it avoids (topics never touched, incidents never acknowledged). A psychologist's note sounds like: "it credits the rival by name, then calls the rival slow and expensive from the same stage ten weeks later."

**Economist.** Reads what the actor protects financially. For companies: revenue exposure to each gate, the cost of compliance versus the cost of resistance, where its money actually moves (filings, price cuts, R&D, investments, IPOs), and what it tells investors on scheduled days. For regulators and ministries the same lens is adapted naturally: it reads budget-relevant behaviour — fine amounts, licence regimes, compute targets, procurement orders, what a rule costs the regulated and what an easing gives back. It does not read motives, only money.

**Political scientist.** Reads who the actor answers to, who can stop it, which alliances it leans on, and how it behaves toward power. Looks for: veto players named in the record, co-issued rules (each co-signer can stop a text), trips to capitals, meetings followed within days by decisions, suspensions and sunsets around summits, and posture toward rivals and patrons. For a company this lens reads its regulators; for a ministry it reads its principals and its peers.

**Domain expert.** Reads the industry-specific pattern that a general reader would miss. For chips: redesign-to-the-limit cycles, cluster-versus-single-chip strategies, roadmap timing, foundry workarounds, software ecosystems. For cloud models: release cadence, licence flips, price wars, distillation terms. For Chinese regulators: the draft-to-order-to-filing-list legislative habit, calendar-driven campaigns, batch approvals. This lens supplies the craft knowledge that makes an inference from one row plausible or absurd.

The four lens names are fixed (`psychologist`, `economist`, `political_scientist`, `domain`) even where the reading is adapted — a regulator's "economist" reads fines and licence regimes, an individual's "economist" reads his market commentary and his share sales.

## Hard rules

1. **Action language only.** Every claim uses verbs of doing, not adjectives of character. "CAC waits for a case, then fines within a year" — never "the actor demonstrates enforcement-oriented response patterns." No "aggressive", "cautious", "strategic" as characterisations; if a trait matters, state the actions that show it.
2. **Every claim cites rows.** Each claim carries the row id(s) in that actor's `rows.json` (or its `context.json` / `data/context-events.json` where the persona uses them) that support it. A claim with no citation is deleted, not repaired.
3. **No claim goes beyond its cited rows.** The lens may not add facts, numbers or actors the rows do not contain. Inference is marked as inference, and at most once per lens, in the form "the record does not show X, which given Y suggests Z" — where X's absence and Y are both visible in cited rows.
4. **Empty stays empty.** If the record lacks a fact, the lens says the record does not show it. It does not fill the gap with industry knowledge, base rates or plausibility. A domain expert may explain what a cited row means; it may not invent what the actor did.
5. **Pre-cutoff only, written once.** Lenses are built only from rows dated on or before the persona's cutoff. Post-cutoff rows (held-out test events) are never read, and simulation output never updates a lens. The lens layer is frozen at generation time.

## How routing works

`spec/topics.json` defines the question taxonomy (topics such as export controls, regulation, open source, with their poles and audiences). For each actor, every topic is mapped to the one lens best suited to answer questions on that topic *for that actor's record* — the same topic can route to different lenses for different actors (export controls routes to the economist for a chip seller and to the political scientist for a commerce ministry). Actors whose persona declares an explicit topic list route only those topics; all others route the full taxonomy. At question time, only the matching lens is attached to the plain record — the other three stay on the shelf — so the answering step sees one expert's margin notes, not a committee.
