# Artifact profiles

Apply the smallest profile that matches the passage. Apply more than one profile only when an artifact genuinely mixes text types.

## Contents

- [Orthogonal modifiers](#orthogonal-modifiers)
- [Reports and technical documents](#reports-and-technical-documents)
- [Procedures and agent instructions](#procedures-and-agent-instructions)
- [Plans, specifications, and requirements](#plans-specifications-and-requirements)
- [Code-related prose](#code-related-prose)
- [Technical conversation](#technical-conversation)
- [Hazard notices](#hazard-notices)

## Orthogonal modifiers

Apply these modifiers with the matching artifact profile. They do not replace a
profile or create a new top-level artifact type.

### Record mutability

- Treat registered designs and completed result records as fixed factual records.
  When the repository permits in-place editorial cleanup, correct only a non-factual
  prose defect with the minimum necessary diff and a stricter semantic-equivalence
  check.
- Preserve the body of a record designated historical or immutable. Also preserve a
  completed record's body when correcting a recorded number, result, date, status, or
  other fact. Put that correction in a dated, append-only companion erratum limited
  to the available evidence.
- Create a companion erratum only when the user, request, or repository defines its
  destination. Otherwise, propose the path and ask before creating it.
- Revise current authoritative documents under their normal profile.
- Do not present a correction as a rerun or a new result.

### Public-facing prose

- Use an output allowlist. Omit private-document references, internal decision
  attribution, review-round history, branch names, and inaccessible development
  context from public output.
- Selecting this modifier authorizes those omissions from the public output under
  the semantic claim inventory. Preserve the technical claims needed to understand
  the public behavior.
- Redact credentials and secret values from public output without exception. Use a
  non-sensitive marker when the surrounding text requires a visible redaction. Remove
  personal identifiers, private URLs, and local user paths unless the public output
  requires them and the user authorizes their disclosure. Report an omission when it
  changes a technical claim.
- Do not treat the public output boundary as permission to rewrite private source
  records.

### Cross-host parity

- Identify the semantics shared across hosts and record intentional differences.
  Reject accidental semantic divergence without forcing identical wording. Allow
  host-specific metadata, installation, and sandbox details to differ.
- Put intentional differences in the requested artifact or a visible companion note
  that a reviewer can inspect.

## Reports and technical documents

Use this profile for findings, analyses, explanations, architecture documents, decision records, manuals, and descriptive sections.

- Lead with the result, subject, or purpose.
- Give information gradually from context to detail.
- Keep one main topic in each sentence.
- Use 25 words as a sentence review target.
- Start each paragraph with its topic.
- Keep one topic in each paragraph.
- Use six sentences as a paragraph review target. Split only at a real subtopic.
- Repeat exact key terms to connect related sentences and paragraphs.
- Use explicit connectors for contrast, sequence, cause, and result.
- Separate evidence, inference, decision, and recommendation when their status differs.
- Preserve source labels, sample sizes, units, qualifications, and uncertainty.

Completion check: A reader can scan the headings and topic sentences to recover the document's logic without losing necessary evidence.

## Procedures and agent instructions

Use this profile for steps, runbooks, setup instructions, operational commands, and task checklists.

- Start each instruction with an imperative action verb.
- Put one independently performed instruction in each sentence.
- Do not equate a sentence with a work step. A work step can contain more than one sentence when actions occur together or when an immediate result, limit, or acceptance criterion belongs with the instruction.
- Put separate sequential actions in separate numbered steps when the procedure
  needs explicit prose sequencing. An already ordered command block can express a
  valid procedure; do not add numbered prose mechanically when its order,
  prerequisites, and acceptance criteria are unambiguous.
- Combine actions only when they are concurrent or operationally inseparable.
- Put a prerequisite condition before its command and separate it with a comma.
- Keep an immediate result, verification, limit, or acceptance criterion in the same numbered work step as the action it evaluates. Use separate sentences inside the step when necessary; do not create a new step only for that result or criterion.
- Use 20 words as a sentence review target.
- Put warnings at the point of risk.
- Use a note only for optional supporting information.
- Read the procedure without its notes. Move required information into the applicable step.

Completion check: A reader can perform the procedure correctly and in order without relying on notes.

## Plans, specifications, and requirements

Use this profile for implementation plans, product requirements, technical specifications, acceptance criteria, and policy statements.

- Identify the component, system, role, or actor that owns each behavior.
- Preserve normative keywords and their defined capitalization.
- Distinguish obligation, recommendation, permission, capability, and prediction.
- State each condition, required behavior, constraint, limit, and observable result explicitly.
- Keep acceptance criteria next to the behavior they verify.
- Use stable requirement verbs and stable domain nouns.
- Separate independently reviewable requirements.
- When splitting a compound requirement, do not add a trigger, sequence, dependency, or object that the source and context do not state.
- Do not convert a normative statement to an imperative when the change would hide ownership or requirement force.
- Do not simplify a standard-defined term or schema field.

Completion check: Each requirement has an identifiable owner, trigger or condition, behavior, and verifiable result where applicable.

## Code-related prose

Use this profile for comments, docstrings, diagnostics, help text, commit or release notes, and prose around examples.

- Apply the rules to natural-language prose, not to code syntax.
- Preserve every identifier, token, command, option, path, literal, and output string exactly.
- Mark literal names with the artifact's normal code formatting.
- Use an identifier as the sentence actor only when it truly performs the action.
- Preserve distinctions among language, framework, API, protocol, and schema terms.
- Explain one purpose, invariant, precondition, or consequence at a time.
- State the current invariant or reason. Do not narrate PR, review, task, issue,
  or edit history.
- Prefer the reason or invariant over a line-by-line restatement of obvious code.
- Preserve existing comments by default. Never remove a suppression, tool directive,
  compliance tag, security or safety assumption, required test rationale, generated
  documentation input, or other comment that repository controls consume, including
  a comment referenced by a machine-parseable build, test, or documentation manifest.
- Remove a comment that only narrates adjacent code or duplicates a clear test name
  only when the user targets that comment. Do not polish it into shorter narration.
- Split the surrounding prose when an exact name makes a sentence long.

Completion check: The prose is clearer, and every executable or externally defined token remains unchanged.

## Technical conversation

Use this profile lightly for an explicit request for clearer technical language or an explanation intended for a broad or mixed audience.

- Lead with the answer.
- Define only necessary unfamiliar terms.
- Keep exact technical terms and use them consistently.
- Use short paragraphs and direct verbs.
- Preserve a natural conversational voice.
- Permit contractions and ordinary conversational transitions when they do not create ambiguity.
- Do not impose sentence counts, paragraph counts, or document formality mechanically.
- Do not invoke this profile for casual chat or brainstorming without a clear technical-communication need.

Completion check: The explanation is accurate on first reading without sounding like a maintenance procedure.

## Hazard notices

Use this profile only with the risk vocabulary required by the applicable project, domain, or standard.

- Identify the approved risk level.
- Put the preventive command or prerequisite condition first.
- State the specific harm or possible result.
- Put the notice immediately before the risky action.
- Do not hide destructive, safety-critical, security-critical, or data-loss information in a note.
- Do not equate software log levels with safety signal words unless the project defines that mapping.
- Do not invent a severity or consequence without a risk analysis.

Completion check: The notice identifies the approved level, prevention, and consequence without relying on formatting alone.
