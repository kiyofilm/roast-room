# Steward Seat Implementation Plan

> For agentic workers: follow `.claude/skills/newroaster/SKILL.md` steps 3 to 9, adapted as below. Native execution.

**Goal:** Add the on-call `steward` seat (faith and stewardship) built from the World English Bible.
**Architecture:** Corpus = 66 WEB books as sources S001 to S066 (verse numbers as superscripts, ignored by the quote checker). Five extraction agents on focus passages, three writers, hand-written `_hot.md` and agent, registered with `add_seat.mjs`.
**Tech Stack:** Node (newroaster scripts), Claude sub-agents.
**Spec:** `docs/superpowers/specs/2026-11-13-steward-seat-design.md`

## Global Constraints
- Quotes verbatim from WEB, under 45 words, with source id; `check_quotes.mjs` passes on the whole brain.
- Seat never says "God says"; cites book chapter:verse; flags silence and disagreement among believers.
- On call, not default. No portrait (placeholder).
- No em dashes. Do not touch other seats.

## Review Focus
- A verse quoted for a claim its context does not support (proof-texting).
- Profitable but unfair option (tenant, worker, guest) must score down.
- Tax question: legitimate planning vs evasion; defers to a CPA.
- Question where Scripture is silent (lease mechanics, pricing): seat says so.
- Roster has no portrait for `steward`: room must still load.

## Tasks
1. Corpus: 66 books added to `build/steward` (done; 756,030 words).
2. Extract: five batches (wisdom/epistles, Torah, history/prophets/Psalms, Gospels, Acts/Paul). Verify: `check_quotes.mjs build/steward build/steward/notes` clean.
3. Brain: writers A/B/C, then `_hot.md`. Verify: `check_quotes.mjs` on brain folder passes.
4. Agent `.claude/agents/council-steward.md` with the never-list above.
5. Register: `add_seat.mjs --key steward ...` (no `--default`); add tension lines to `references/seats.md`.
6. Test: sample STR consult; answer saved, quotes checked; `npm run smoke`.
7. Commit and push to `claude/vigilant-knuth-ar7jra`.
