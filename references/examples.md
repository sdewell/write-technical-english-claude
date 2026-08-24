# Examples

Use these patterns as semantic examples, not as mechanical templates.

## Direct actions and sequence

Before:

> Prior to making the change, ensure that an examination of the current configuration has been performed and then proceed with the service restart.

After:

1. Examine the current configuration.
2. Make the change.
3. Restart the service.

### Already ordered command block

An ordered command block can already express a valid procedure when its sequence
and acceptance condition are clear:

```sh
uv run pytest tests/release/test_manifest.py -q
npm run build:release
node scripts/check-release.mjs dist/release.json
```

The release is ready only when the test succeeds, the build completes, and the
checker reports `status=ready`.

## One topic and stable terminology

Before:

> The cache stores responses for five minutes, while the response store reduces requests, and this data is removed when it expires.

After:

> The cache stores each response for five minutes. The cache reduces repeated requests. The cache removes the response after five minutes.

## Long noun stack

Before:

> Add account access token expiration validation.

After:

> Add validation for the expiration time of the account access token.

Keep `AccountAccessTokenExpirationValidation` unchanged if it is an exact class name.

## Normative force

Before:

> Expired tokens should not be accepted by the server.

After, when the governing standard defines `MUST`:

> The server MUST reject an expired token.

## Governing vocabulary

Governing source:

> Tier: Exploratory. Verdict: INCONCLUSIVE.

Unsafe paraphrase:

> This preliminary result is promising but uncertain.

Accurate use:

> Tier: Exploratory. Verdict: INCONCLUSIVE.

Keep canonical classifications and verdict labels when another active skill, standard, glossary, or schema defines them.

## Known actor

Before:

> Temporary entries are removed by `cleanup()`.

After:

> `cleanup()` removes temporary entries.

## Unknown cause

Before:

> The payload was corrupted during transmission.

Unsafe rewrite:

> Transmission corrupted the payload.

Accurate revision:

> The payload was corrupted during transmission.

Do not add a cause or state that the cause is unknown unless the source or context
establishes that claim.

## Bounded hypothesis

Before:

> The same request succeeded five minutes later. The most likely explanation is a short-lived mismatch between the catalog and execution service, but the logs do not establish the cause.

Unsafe revision:

> The later success does not establish the cause.

Accurate revision:

> The later success makes a short-lived mismatch between the catalog and execution service the most likely explanation, but the logs do not establish the cause.

Preserve a supplied hypothesis at its stated strength. Do not turn it into a fact, weaken it to an unranked possibility, or remove it in favor of a generic uncertainty statement.

## Modal polarity

Before:

> State only assumptions that affect the result. Otherwise, the agent may narrate routine assumptions.

Unsafe revision:

> State only assumptions that affect the result. This prevents the agent from narrating routine assumptions.

Accurate revision:

> State only assumptions that affect the result. Otherwise, the agent may narrate routine assumptions.

Do not change a possible undesirable outcome into a guarantee that the guidance prevents it.

## Evidence scope

Before:

> I checked the package reference but could not find a documented guarantee that retrying `submit_batch()` is idempotent.

Unsafe revision:

> The package reference does not guarantee that retrying `submit_batch()` is idempotent.

Accurate revision:

> I could not find a documented guarantee in the package reference that retrying `submit_batch()` is idempotent.

Preserve the difference between an unsuccessful search and a fact about what exists or is available.

## Notation contract

Before:

> \[
> R = \frac{m}{N_{\text{eligible}}}
> \]
>
> `m` is a matching-record count. `N_{\text{eligible}}` is the count of all eligible records, not the set of records.

Unsafe revision:

> `N_{\text{eligible}}` is the set of all eligible records.

Accurate revision:

> `m` is a matching-record count. `N_{\text{eligible}}` is the count of all eligible records, not the set of records.

Protect an equation together with its symbol definitions, units, domains, constraints, and undefined cases.

## Conclusion and supporting evidence

Before:

> The trace shows that the service loaded an expired certificate. The same request succeeded after the previous certificate was restored. The expired certificate caused the failed connection.

Unsafe revision:

> The expired certificate caused the failed connection.

Accurate revision:

> The trace shows that the service loaded an expired certificate. The same request succeeded after the previous certificate was restored. The expired certificate caused the failed connection.

Preserve supporting and corroborating observations. A verified conclusion does not make its evidence repetitive.

## Condition before command

Before:

> Delete the temporary file if the checksum is valid.

After:

> If the checksum is valid, delete the temporary file.

## Acceptance limit with its action

Before:

> Run the latency test.
>
> NOTE: The p95 latency must not exceed 250 ms.

After:

> Run the latency test. The p95 latency must not exceed 250 ms.

## Ambiguous pronoun

Before:

> The worker sends the record to the queue after it validates it.

After, when the worker validates the record:

> The worker validates the record. Then, the worker sends the record to the queue.

Resolve the meaning before revising when the intended actor or object is unknown.

## Exact user-interface text

Before:

> Select the option for creating a pull request.

After:

> Select `Create Pull Request`.

## Domain term at first use

Before:

> Enable backpressure.

After:

> Enable backpressure, a flow-control mechanism that limits incoming work.

## Hazard structure

Context: The project defines `DATA LOSS` for irreversible data deletion. The command permanently deletes customer records from the production database.

Before:

> NOTE: Be careful with this command on production.

After:

> DATA LOSS: Do not run this command on the production database. The command permanently deletes customer records.

## Historical correction

Preserve the completed record and create a dated companion erratum when audit
evidence shows that a historical statement was false. Do not edit the original
record body. For example, the companion erratum can contain:

> 2026-08-22 erratum: The record states that the run used 10 seeds. Audit
> evidence shows that the run used 8 seeds. The original record remains unchanged.

## Conversational explanation

Before:

> Serialization is a process whereby an object is subjected to conversion into a format that is able to be stored or transmitted.

After:

> Serialization converts an object into a format that a system can store or transmit.
