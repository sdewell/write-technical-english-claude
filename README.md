# Write Technical English for Claude Code

`write-technical-english` is a Claude Code skill for consolidating terminology and
replacing unnecessary jargon in technical prose. It favors consistent terminology
and direct language while preserving technical meaning, exact identifiers,
requirement force, evidence scope, and uncertainty.

The skill applies principles adapted from ASD-STE100 Simplified Technical English to
software and general technical writing. It does not claim strict ASD-STE100
compliance.

## Install

For a personal installation available across projects, run:

```bash
mkdir -p ~/.claude/skills
git clone --depth 1 --branch v0.1.0 \
  https://github.com/sdewell/write-technical-english-claude.git \
  ~/.claude/skills/write-technical-english
```

The clone command stops without changing an existing installation at that path. If
the skill does not appear after installation, restart Claude Code.

## Use

Invoke the skill explicitly with `/write-technical-english`. Automatic invocation is
disabled so that the skill does not change ordinary conversation or unrelated work.

Examples:

```text
/write-technical-english Revise README.md for a mixed technical audience.
```

```text
/write-technical-english Review this release note for ambiguity. Report issues, but
do not edit the file.
```

```text
/write-technical-english Review this specification and implementation plan, then
draft a report from these results. Preserve requirements, measured values, evidence
limits, and uncertainty at their original strength.
```

## What it does

The skill:

- Identifies the audience, artifact type, and governing terminology.
- Consolidates competing terms for one concept and replaces unnecessary jargon only
  when a simpler term preserves the meaning.
- Protects identifiers, commands, paths, formulas, quotations, and canonical labels.
- Preserves actors, conditions, evidence scope, uncertainty, requirement force, and
  technical meaning.
- Applies writing profiles for reports, procedures, specifications, and code-related
  prose.
- Uses a null edit when the source has no demonstrated correctness or clarity defect.
- Respects named passage and file boundaries.

It can help with documentation, reports, plans, specifications, procedures, agent
instructions, code comments, diagnostics, release notes, and terminology reviews for
broad or mixed audiences.

## Compatibility

This release targets Claude Code. It uses `disable-model-invocation`, a Claude
Code-specific field that keeps the skill explicit-only. Direct claude.ai skill uploads
accept only the portable Agent Skills frontmatter fields, so this repository is not a
claude.ai upload bundle.

## Limitations

This skill is a writing aid. It does not:

- Replace technical review or subject-matter expertise.
- Certify text as ASD-STE100 compliant.
- Apply the complete ASD-STE100 controlled dictionary.
- Override project terminology, schemas, standards, or other governing sources.
- Invent or expand technical content from sparse source material.
- Apply to code, casual conversation, or unrelated brainstorming.

For strict ASD-STE100 interpretation or compliance work, obtain the current standard
from the [official ASD-STE100 downloads page](https://www.asd-ste100.org/STE_downloads.html).

## Package contents

`SKILL.md` contains the workflow and routes Claude to the supporting files under
`references/` only when they are relevant.

## License

The project-authored files are available under the [MIT License](LICENSE).

## Independence and trademarks

This independent project is not affiliated with, endorsed by, certified by, or
approved by ASD or the ASD Simplified Technical English Maintenance Group (STEMG).
ASD-STE100 Simplified Technical English is a registered trademark of ASD.
