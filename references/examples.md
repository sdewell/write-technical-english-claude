# Before/after examples — simplifying without changing meaning

Deliverable 6 of the research phase; repaired 2026-08-06 after the Codex-side
review found several Afters asserting facts their Befores never contained.
Every pair now obeys TW-53: **the After uses only facts present in the Before
or its stated Context line.** A rewrite that needs a fact you do not have is a
question for the user, not a sentence. Rule references are to
the TW rules in `SKILL.md`.

## 1. Burying the conclusion (TW-1, TW-5, TW-24)

*Context: the writer has already reproduced the bug with a two-request test —
concurrent refreshes overwrite each other's token in `token_store` — and
identified a compare-and-swap write as the fix. Knowing all that, they write:*

**Before**
> After a thorough investigation of the authentication flow, taking into account the
> various ways in which the session-refresh mechanism interacts with the underlying
> token store, it would appear that there may potentially be a scenario in which,
> under certain timing conditions, the refresh logic could conceivably fail to
> persist the updated token, which might explain the behavior you observed.

**After**
> Found it: the logout bug is a race condition in session refresh. When two requests
> refresh at the same time, the second overwrites the first token in `token_store`,
> and the session dies. I verified this with a two-request test; the fix is a
> compare-and-swap write.

The Before is not humble — it is *miscalibrated*: verified facts written as
speculation. The After states what the writer actually knows. Without that
context, the After would be the opposite failure: speculation written as fact
(TW-53).

## 2. Elegant variation hiding one concept (TW-22)

**Before**
> The `parse_config()` routine reads the settings file. The parser then validates
> the loaded data, and the configuration subsystem finally applies the processed
> values to the runtime.

**After**
> `parse_config()` reads the settings file, checks the loaded values, and applies
> them to the runtime.

One function, one name. "Routine," "parser," and "configuration subsystem" were all
`parse_config()` wearing costumes.

## 3. Nominalization and passive stacking (TW-13, TW-14, TW-15)

**Before**
> Prior to deployment being performed, verification of the migration must have been
> carried out, and a determination should be made as to whether a backup has been
> created.

**After**
> Before you deploy: run the migration test, and confirm that a backup exists.

## 4. Instructions smeared into prose (TW-2, TW-6, TW-10, TW-12)

**Before**
> You'll want to make sure the daemon isn't running before reinstalling, which can
> be accomplished by stopping the service, after which the package can be removed
> and the new version installed, though it's advisable to clear the cache directory
> as well since stale entries have been known to cause issues.

**After**
> 1. Stop the service: `systemctl stop myd`
> 2. Remove the old package.
> 3. Recommended: delete the cache directory. Stale entries have caused problems
>    after upgrades.
> 4. Install the new version.

The Before called cache clearing "advisable," so the After keeps it a
recommendation with the Before's own reason — upgrading it to a bare mandatory
step, or asserting a specific failure the Before never named, would change the
requirement's force (TW-53, TW-7).

## 5. Vague warning (TW-40, TW-41)

*Context: the writer knows `cleanup.sh` deletes every row older than 30 days,
with no dry-run flag and no undo.*

**Before**
> Note: exercise caution when running the cleanup script in production environments,
> as unintended consequences may occur.

**After**
> **Warning:** do not run `cleanup.sh` against production. It deletes every row
> older than 30 days with no dry-run and no undo.

The requirement also moves out of a "Note" — notes never carry requirements (TW-42).

## 6. Jargon without definitions vs. jargon removed wrongly

Two failure modes. The charter wants neither.

**Before (unexplained jargon)**
> The regression stems from premature memoization invalidation cascading through
> the reactive dependency graph.

**Wrong fix (term destroyed)**
> The bug happens because the app forgets things too early and everything gets
> confused downstream.

**After (term kept and defined — TW-23, TW-32)**
> The bug is in memoization — the cache of already-computed values. The app clears
> that cache too early, so components that depend on cached values recompute
> against the changed state downstream.

The After defines the term and restates only what the Before claimed (premature
invalidation, cascading effects). It does not add a fix the Before never
stated — that would be TW-53's invented-fact failure.

## 7. Explanation that circles (TW-4, TW-3)

*Context: profiling showed records are stored in insertion order but read in key
order, so nearly every read is a disk seek; a sort-first test (one pass, about
2 minutes) cut indexing from 40 minutes to 3.*

**Before**
> The indexing step is slow because of how the data is stored. Essentially, the
> storage layout isn't optimal for the access pattern, which is fundamentally why
> indexing takes so long. In other words, the way records are arranged on disk
> doesn't match how the indexer reads them, and this mismatch is at the heart of
> the performance issue.

**After**
> Indexing is slow because records are stored in insertion order but read in key
> order, so nearly every read is a disk seek. Sorting the records first (one pass,
> about 2 minutes) makes the reads sequential and cuts indexing from 40 minutes to 3.

Three sentences in the before all say "layout mismatch." The after says it once and
then adds the two things the reader actually needs: the mechanism and the fix.

## 8. Protected terms under a word cap (TW-30, TW-31)

**Before (rule misapplied)**
> Call the user-auth token refresh timeout getter.

**After (identifier verbatim, prose simple)**
> Call `getUserAuthTokenRefreshTimeoutMs()`. It returns the timeout in milliseconds.

The identifier counts as one word (STE Rule 8.6 model) and is never paraphrased —
a paraphrase is unsearchable and, worse, might name a function that does not exist.

## 9. Invented causality (TW-13, TW-53)

**Before**
> The payload was corrupted during transmission.

**Wrong fix (active voice applied mechanically)**
> Transmission corrupted the payload.

The rewrite asserts a cause the source never claimed. Active voice must not
invent an actor.

**After**
> The payload was corrupted during transmission. The cause is unknown.

Adopted from the Codex-side cross-review.

## 10. Invented dependency between requirements (TW-7, TW-53)

*Context: the source states two separate requirements. It does not say the
retry is conditional on a rejection.*

**Before**
> The server MUST reject an expired token and the client MAY retry the request
> once with the same `Idempotency-Key` value.

**Wrong fix (separation invents a dependency)**
> The server MUST reject an expired token.
> If the server rejects an expired token, the client MAY retry the request once.

**After**
> The server MUST reject an expired token.
> The client MAY retry the request once.
> If the client retries, it SHOULD use the `Idempotency-Key` value from the
> original request.

Splitting a compound requirement is a formatting change, not a licence to add
logic. The wrong fix makes the retry permission conditional on a rejection the
source never linked to it. Adapted from the Codex-side EV-6 finding.

## 11. Binding vocabulary from a governing skill (Class 6, TW-22)

**Before**
> The optimization results look promising but uncertain — we'll firm this up
> later.

**After**
> Exploratory (registered follow-up pending): the treatment shows a favorable
> trend, but the verdict is INCONCLUSIVE under the ±0.05 margin — the difference
> test and the equivalence test both failed.

"Exploratory" and "INCONCLUSIVE" are codified terms from the
`experiment-design-and-validation` skill. They price what the claim may do;
"promising but uncertain" is a paraphrase that erases the classification.
