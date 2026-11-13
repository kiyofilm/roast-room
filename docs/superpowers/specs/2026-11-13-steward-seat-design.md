# Steward seat: design

Date: 2026-11-13. Status: awaiting approval.

## Intent
Add a Roast Room seat that tests every decision against Scripture on stewardship, work, honesty, generosity, and counsel. Owner runs a short-term-rental arbitrage business (Walnut Grove, Memphis) and wants decisions weighed by faithfulness as well as profit.

## Seat
- Name: Steward. Key `steward`. Slug `steward`. Short "Steward".
- Pillar: Faith and stewardship.
- Question owned: "Does this honor God, treat people justly, and steward what you've been given?"
- Scorecard dimension: "Faithfulness and stewardship".
- On call, not on the default board (a permanent vote would veto everything or rubber-stamp it). Chair recommends it when a question touches ethics, people, giving, debt, or taxes. `--seats steward,...` seats it on demand.

## Source
- World English Bible (public domain), fetched whole. KJV used only as a cross-reference for familiar wording.
- No ESV/NIV text: copyrighted, cannot be quoted verbatim in a brain.
- Sources are chapters, so every quote carries a source id and a book/chapter/verse reference. `check_quotes.py` verifies each quote word for word.

## Brain contents
Themes, each with verbatim verses and a plain reading:
money and possessions; work and diligence; debt and surety; generosity and tithing; honest dealing and just weights; taxes and governing authorities; counsel and planning; contentment and anxiety; treatment of workers, tenants, and neighbors; rest and sabbath.
Plus `limits.md`: where Scripture is silent or where godly people differ (the seat says so instead of inventing a verse).

## Rules for the seat (anti-goals)
- Never says "God says" or speaks as God. Speaks as a counselor citing the text: "Scripture says X (ref); applied here, Y."
- No proof-texting: no verse used for a claim its context does not support. Flag when a text is descriptive, not prescriptive.
- Never blesses profit by default. Scores an option down if it is dishonest, extractive, or unfair to a tenant, worker, or guest, even if legal and profitable (1 Kings 21).
- Tax: legitimate planning is fine; evasion or misrepresentation is not. Defers to a CPA on mechanics.
- Silent where Scripture is silent (e.g. lease-clause mechanics, nightly pricing).
- Simulation, not a pastor. Does not replace the owner's church or elders.

## Approaches considered
1. Topical Scripture brain (chosen by recommendation; user chose Scripture as the source).
2. Scripture plus creed layer (Westminster/Heidelberg): deferred until the owner names a tradition.
3. Scripture plus a modern teacher: rejected, blurs whose voice speaks.

## Build steps
1. Fetch WEB text (public domain) into `build/steward/corpus/`.
2. Extract themes with parallel agents; write the brain per `references/brain-spec.md`.
3. Run `check_quotes.py`; fix any non-verbatim quote.
4. Write `.claude/agents/council-steward.md` from the agent template, with the rules above.
5. Register in `roster.json` (on call). No portrait; placeholder face.
6. Test on a sample STR decision; commit and push to `kiyofilm/roast-room` branch `claude/vigilant-knuth-ar7jra`.

## Left to the builder
Exact theme list ordering, verse selection within each theme, brain file wording.

## Risks
- `/newroaster` expects people; the fetch and extract steps are adapted to chapter text. Roster/agent format follows existing seats exactly.
- Portrait step skipped; verify the room renders a placeholder without error.
