# Controlled vocabulary — preferred terms and discouraged alternatives

Deliverable 4 of the research phase; reviewed by S 2026-08-05/06. Grows only via the organic feedback loop.

This follows the STE dictionary *mechanism* — one preferred word per concept, with
discouraged alternatives mapped to it — without adopting STE's closed 875-word list.
Scope: our prose (responses, docs, plans, comments). It never applies to code,
identifiers, quoted output, or established domain terms (`exception-policy.md`).

A discouraged word is not banned when it is the exact technical term in context:
"terminate" is discouraged as a synonym for "end," but `SIGTERM` "terminates a
process" is correct usage and stays.

## Verbs — prefer the plain one

| Preferred | Discouraged alternatives |
|---|---|
| use | utilize, leverage, employ, make use of |
| start | initiate, commence, kick off, spin up (unless the tool's own term) |
| stop / end | terminate*, cease, halt* (*fine as exact technical terms: SIGTERM, CPU halt) |
| show | demonstrate, illustrate, surface, expose (unless API-visibility sense) |
| help | facilitate, assist, aid |
| make / create | generate*, construct, fabricate (*fine for generated artifacts/code) |
| get | obtain, acquire, retrieve* (*fine as the API/db term) |
| send | transmit, dispatch |
| tell / say | indicate, articulate, communicate |
| check | verify*, validate*, examine (*keep when the distinction matters — see Note 1) |
| fix | remediate, rectify, resolve* (*fine for tickets/DNS, the domain senses) |
| change | modify, alter, adjust |
| need | require*, necessitate (*"required" as a schema/API property stays) |
| try | attempt, endeavor |
| speed up | accelerate, optimize* (*keep when it means real optimization work, not "improve") |
| look at / read | examine, inspect*, review* (*keep for `docker inspect`, code review) |
| think about | consider, contemplate |
| find | locate, identify*, discover* (*keep for service discovery, identifier senses) |
| explain | delve into, unpack, elaborate on |
| improve | enhance, refine, polish |

## Fillers and formality — delete or shorten

| Write | Not |
|---|---|
| to | in order to |
| before / after | prior to / subsequent to |
| if | in the event that, should it be the case that |
| now | at this point in time, currently (when redundant) |
| about | approximately, roughly, in the neighborhood of, on the order of |
| because | due to the fact that, owing to, as a result of the fact that |
| can | is able to, has the ability to, is capable of |
| (delete) | it is worth noting that, note that*, it should be mentioned that (*keep "Note:" as a labeled callout) |
| (delete) | essentially, basically, fundamentally, effectively |
| (delete) | robust, comprehensive, seamless, elegant, sophisticated, powerful — as unsupported praise |
| (delete) | very, quite, rather, fairly — before technical claims |
| also | additionally, furthermore, moreover |
| but | however* (*fine at sentence start when the contrast is the point), nevertheless |
| so / thus | consequently, accordingly, hence |
| many / most | a significant number of, the majority of |
| some | a subset of (unless the mathematical sense is meant) |

## Hedging — one hedge, or none

| Write | Not |
|---|---|
| can | may potentially, could potentially |
| probably | it is likely that it may |
| I think / I infer | it would seem that it might be reasonable to suppose |
| fails | may not always behave as expected |
| I don't know | it is unclear at this juncture |

State uncertainty once, with a calibrated word (certain / probably / possibly /
unknown), then say the thing plainly (TW-5).

## Agent-prose patterns to stop

These are the habits the charter names — each maps to a standard rule:

- Burying the verdict under qualifications → state the verdict first (TW-1).
- Re-explaining the same conclusion in new words → once, in order (TW-4).
- Elegant variation ("the function… the routine… the helper…") → one term per
  concept (TW-22).
- Abstraction stacking ("the mechanism underlying the behavior of…") → name the
  concrete thing (TW-15, TW-19).
- Adjective inflation ("a robust, comprehensive solution") → report what it does
  and what was verified (TW-24, TW-50).
- Caveat accumulation (a clean result followed by a limitation, a "sharp edge,"
  an optional re-check, and a coverage note) → keep only the caveats that change
  what the reader does; one that costs the reader nothing gets one clause or
  nothing (TW-1, TW-5). TW-1 orders a sentence and TW-5 governs a single claim,
  so a passage can satisfy both and still read as unresolved risk.

## Note 1 — words we keep separated on purpose

Some near-synonyms carry real technical distinctions. Do not collapse them:

- **verify** (confirm a specific expected result) vs **validate** (check against a
  schema/ruleset) vs **check** (general look).
- **error** (operation failed) vs **warning** (operation succeeded with a concern)
  vs **failure** (test/assertion did not pass).
- **argument** (value passed) vs **parameter** (name in the signature).
- **authentication** (who you are) vs **authorization** (what you may do).
- **concurrency** vs **parallelism**.

The rule is STE 9.2's: use each kept term only in its precise sense.

## Growth policy (decided 2026-08-05)

- No bulk extraction of the STE word list — the curated table above is the
  vocabulary. This also moots the copyright question flagged in
  `summaries/00-overview.md`.
- The table grows only from observed friction — when a review flags a word
  repeatedly — not by speculative bulk additions.
