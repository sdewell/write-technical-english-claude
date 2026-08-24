# Vocabulary

Control ordinary prose without flattening technical distinctions.

## Contents

- [Replacement method](#replacement-method)
- [Preferred ordinary prose](#preferred-ordinary-prose)
- [Requirement terms](#requirement-terms)
- [Protected technical distinctions](#protected-technical-distinctions)
- [Abbreviations and short forms](#abbreviations-and-short-forms)

## Replacement method

Before replacing a word:

1. Identify its intended meaning and part of speech.
2. Check whether it belongs to exact, quoted, standard-defined, or approved domain text.
3. Keep protected text unchanged.
4. Use the preferred term only when it preserves meaning.
5. Rewrite the sentence when direct substitution changes meaning or grammar.

## Preferred ordinary prose

| Prefer                       | Discourage in ordinary prose         | Exception                                                                             |
| ---------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------- |
| `alternative`                | `alternate` as an adjective          | Keep an exact name or defined domain use.                                             |
| `permitted`                  | `acceptable`                         | Keep a standard-defined acceptance category.                                          |
| `prevent`                    | `avoid`                              | Keep `avoid` when `prevent` changes the meaning.                                      |
| `start`                      | `begin`, `commence`                  | Preserve lifecycle states, commands, methods, events, and quotations.                 |
| `make sure`                  | `ensure` in ordinary instructions    | Keep a distinct domain operation or identifier. Use `verify` for formal verification. |
| A direct precise verb        | Generic `perform`                    | Use the established operation, such as `compile`, `deploy`, or `validate`.            |
| `but`                        | `however`                            | Keep quoted or externally controlled text.                                            |
| `primary`                    | `main` as a generic adjective        | Preserve `main` in branch names, entry points, functions, and official terms.         |
| `can` for capability         | `may` for capability                 | Preserve source `may` when it carries possibility, uncertainty, permission, or normative force. |
| `part`                       | `portion`                            | Keep a defined domain distinction.                                                    |
| `because`                    | Causal `since`                       | Keep `since` for time.                                                                |
| `thus` or `as a result`      | `therefore`                          | Select the connector that states the real relationship.                               |
| `use`                        | `utilize`                            | Keep exact names and quotations.                                                      |
| `through`                    | `via`                                | Keep protocol, route, or API terminology when it is precise.                          |
| `at the same time`           | `simultaneously`                     | Keep formal concurrency language when timing semantics matter.                        |
| `for example`                | `e.g.`                               | Keep exact citations.                                                                 |
| `that is`                    | `i.e.`                               | Keep exact citations.                                                                 |
| An explicit list or phrase   | `etc.`                               | Omit it when it adds no information.                                                  |
| `do not`, `is not`, `cannot` | Contractions in controlled artifacts | Permit natural contractions in conversation and exact text.                           |

## Requirement terms

- Use `must` for an unconditional requirement when no governing standard defines another convention.
- Preserve `MUST`, `SHOULD`, and `MAY` when an applicable standard defines their force.
- Keep `required` and `necessary` only when they express the intended obligation.
- Use `can` for capability. Preserve source `may` when it carries possibility, uncertainty, permission, or normative force.
- Use `may` for ordinary permission only when the context cannot give it normative force. Otherwise, use the governing keyword or state that the action is permitted.
- Do not add `must` before an imperative command merely for emphasis.

## Protected technical distinctions

Do not normalize these terms without a domain decision:

| Terms                                                                                | Protection                                              |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------- |
| `test`, `check`, `verify`, `validate`                                                | Preserve distinct levels or methods of evaluation.      |
| `initialize`, `instantiate`, `execute`, `run`                                        | Preserve distinct lifecycle and runtime operations.     |
| `serialize`, `deserialize`, `encode`, `decode`                                       | Preserve each data transformation and contract.         |
| `authenticate`, `authorize`                                                          | Preserve the security distinction.                      |
| `compile`, `link`, `load`                                                            | Preserve build-time and runtime stages.                 |
| `async`, `await`, `binding`, `borrow`, `closure`, `coroutine`, `event loop`, `trait` | Preserve established language and platform terminology. |
| `main`, `rotate`, `stream`, `route`, `mount`                                         | Preserve identifiers and precise domain meanings.       |

Add a project term when it names a necessary concept or process, has an authoritative source, and improves precision. Record its canonical form, meaning, context, part of speech where relevant, approved short form, and one example.

## Abbreviations and short forms

- Write a required long term in full at first use when the context does not already define it.
- Define one approved abbreviation or short form when it helps the reader.
- Use that form consistently.
- Do not invent an abbreviation for a short term merely to reduce length.
- Do not fill procedures with abbreviations when complete terms are clearer.
- Preserve official capitalization and punctuation.
