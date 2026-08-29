# Exception policy — terminology that must remain exact

Deliverable 5 of the research phase; reviewed by S 2026-08-05/06 and refined through the cross-review and dry-run rounds.

This policy defines what the writing standard may never simplify, reword, respell,
or split. It adapts three STE mechanisms: technical nouns and technical verbs
(Rules 1.5, 1.12), the quoted-text carve-out (Rules 8.6, 1.14), and company-glossary
precedence (Rule 1.8). The standard simplifies *explanation*; it protects *names*.

## Class 1 — Verbatim identifiers (never altered, set in code spans)

Exact reproduction of spelling, capitalization, and punctuation, because the text is
or refers to a machine interface:

- Function, method, class, type, trait, struct, enum, and variable names
- Module, package, crate, namespace, and import paths
- Commands, subcommands, CLI flags, and their arguments (`git rebase -i`, `--dry-run`)
- Configuration keys, environment variables, and their literal values
- File names, paths, URLs, ports, schemas, table and column names
- API endpoints, HTTP methods and status codes, protocol fields
- Enum values, status strings, signal names (`FAILED`, `SIGTERM`), version strings
- Error messages, log lines, terminal output, and UI strings (quote exactly, then
  gloss in plain language if the reader needs it)
- **Mathematical expressions, equations, formulas, notation, and units** —
  including variable names and index letters. Renaming an index or changing a
  summation domain silently breaks any parallel the surrounding prose draws
  between two expressions.

**Copy protected blocks first.** Before revising the prose, reproduce every
protected block — equation, command, log excerpt, quoted string, table of
values — unchanged into the draft. Then write around them. This is procedural,
not advisory: a block that was copied cannot be accidentally paraphrased, and
one that was retyped usually is. Change a protected block only when the user
explicitly targets it.

Rules that yield to Class 1: word choice (TW-21), noun-cluster limits (TW-19),
"-ing" and part-of-speech restrictions, hyphenation conventions, spelling, and word
counts (each token counts as one word, per STE 8.5–8.7).

## Class 2 — Language and platform terminology (kept, defined at first use)

The established vocabulary of the languages and platforms we use is correct
terminology, not jargon to remove. Examples by ecosystem:

- **Python**: virtual environment, GIL, decorator, generator, wheel, `asyncio`
- **Rust**: borrow checker, lifetime, ownership, trait bound, crate, `unsafe`
- **C/C++**: undefined behavior, translation unit, linker, header, RAII
- **JavaScript/Node.js**: event loop, promise, closure, hoisting, npm workspace
- **General**: race condition, deadlock, cache invalidation, idempotent, mutex

Handling: keep the term, define it in a short clause at first use for a
non-engineer reader (TW-23), then use it consistently (TW-22). Do not substitute a
"simpler" near-synonym that changes the meaning.

## Class 3 — Proper names and standards (exact official form)

Product, project, organization, standard, and specification names in their official
spelling and casing: PostgreSQL, ASD-STE100, ISO 1087, macOS, Node.js, ruff, uv.
When an official name conflicts with our style rules (leading lowercase, internal
capitals, hyphens), the official name wins.

## Class 4 — Application-domain terms (project glossary governs)

Established terminology from our application areas — for example bioacoustics and
species identification (birdIdDash), GPU/Metal programming, statistics and
experiment design (estimand, power analysis), audio/DSP (impulse response). These
follow STE Rule 1.8: the field's official term is used, not an invented plainer one.
Each project's glossary (its CLAUDE.md, LEARNINGS.md, or docs) is the authority;
this repo does not maintain a central list.

## Class 5 — Settled technical verbs and phrasal terms (allowlist)

STE bans noun↔verb conversion and invented phrasal verbs (1.7, 1.13, 9.3). Software
has settled conversions that read as normal usage and must not be "corrected":

- to cache, to email, to script, to merge, to fork, to clone, to commit, to deploy,
  to ping, to grep, to diff, to lint, to vendor, to backport
- roll back (a migration), check out (a branch), spin up (an environment, when it is
  the tool's own term), back up (data), opt in / opt out

This is an allowlist, grown case by case — not a license for ad-hoc conversions
("let's action that") which stay banned.

## Class 6 — Skills and codified methods (the skill is the source of truth)

When a skill codifies a method — its name, steps, parameters, trigger text, and
internal conventions — that codification is authoritative. The standard never
rewrites it:

- The method itself ("method X") is not restyled, renamed, or "clarified" in
  place. We are not changing method X; we are explaining it.
- A skill's description and trigger text is a retrieval surface — keyword density
  is functional. Do not rewrite it for elegance; a beautiful description that
  stops triggering is a regression.
- A skill's internal formatting conventions (checklists, tables, terse
  imperatives) are part of the method and stay.

The standard governs the prose *around* the method: what we use method X for, the
results of using it, and how it must be used in conjunction with something else.
If following the standard would require changing a skill's codified content, that
is a conflict to report, not an edit to make.

A skill's codified vocabulary also *binds* the prose written under it. When a
governing source defines canonical terms, classifications, statuses, verdict
labels, required phrases, or prohibited phrases, that vocabulary is binding in
the resulting artifact: use the prescribed term and form wherever it carries the
defined meaning, and do not substitute a synonym or paraphrase unless the
governing source permits it. Tier names ("confirmatory," "exploratory,"
"blue-sky"), verdict labels ("INCONCLUSIVE," "practically equivalent"), markers
(`[unverified]`), and stamps (`Preflight-Review:`) are load-bearing — "promising
but uncertain" in place of "Exploratory — INCONCLUSIVE" changes what the claim
is allowed to do, not just how it sounds. Where a skill codifies its own
reporting language (for example the verdict grid and banned-phrases list in
`experiment-design-and-validation`, `COMPARISON_STATISTICS.md` §8), that
language wins over this standard's phrasing preferences for those reports.

## Text types outside the prose standard

Some whole text types have a job other than being read as prose. The standard
does not apply to their bodies:

- Skill descriptions and trigger text (retrieval surfaces — Class 6)
- LEARNINGS entries (telegraphic density is a feature of the format)
- Frontmatter, config files, schemas, and structured metadata
- Tables where density is the point
- Commit subject lines and trailers (git conventions govern; commit *bodies* and
  PR descriptions follow the document register)
- Taglines and one-line descriptors (a README's opening line, a package
  description field) — fragment style there is a convention, not a defect
- Quoted logs, errors, and command output (Class 1)

## Class 7 — Normative keywords (standard-defined force)

When a standard or project defines requirement keywords — MUST, SHOULD, MAY per
RFC 2119, or a project's own convention — keep the keyword, its capitalization,
and its force exactly. Do not swap in an ordinary synonym ("needs to," "can"),
and do not convert a normative statement into an imperative when the conversion
hides which component or actor owns the requirement (TW-7).

Where no convention governs, plain "must" states an unconditional requirement —
and TW-43 limits it to steps with real consequences.

The relationships among requirements are protected the same way as their
wording. Separating a compound requirement into parts must not introduce a
trigger, sequence, dependency, or object that the source left unstated —
adjacency is not conditionality. When the source is genuinely ambiguous about a
relationship, ask; do not resolve it by domain inference (TW-53).

## Precedence

1. Class 1 verbatim text — with Class 6 codified skill content and Class 7
   normative keywords — beats every other rule.
2. Official names (Class 3) and field glossaries (Class 4) beat our vocabulary
   preferences.
3. Our vocabulary (`vocabulary.md`) governs everything that remains — the
   explanatory prose around the protected terms and methods.

## The test

Before simplifying any term, ask: **if I change this word, does anything break or
become false?** A build, a lookup, a citation, a colleague's search, a precise
technical distinction. If yes — protected, keep it exact and define it. If no — it
is explanation, and the standard applies.
