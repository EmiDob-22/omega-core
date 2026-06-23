# CLAUDE.md

Guidance for AI assistants (Claude Code and others) working in this repository.

## Current state

`omega-core` is currently an **empty repository** — it has no commits and no
tracked files yet (this CLAUDE.md is among the first). There is no source code,
build system, tests, or CI to document. Do not invent structure or describe
files that do not exist; verify the actual contents (`git ls-files`) before
making claims.

## Context within the ecosystem

This repo belongs to the `EmiDob-22` / **OMEGA** project family. Sibling repos:

- **`ksdz`** — the KSDZ v4.0 "OMEGA" spectral compression engine (working Python
  code). Its demo module is named `omega_16d_quantum.py` and uses the "OMEGA"
  brand, so `omega-core` is most likely intended to host the broader OMEGA
  system that KSDZ plugs into.
- **`EmiDob-22`** — the owner's GitHub profile README repo.

Treat "OMEGA core" as the probable intent, but confirm scope with the user
before scaffolding a project here.

## Conventions to carry over (when code is added)

If/when this repo gains code, follow the conventions established in the sibling
`ksdz` repo unless the user says otherwise:

- Python 3 + NumPy numerical style; short, comment-light code.
- An AGPLv3 copyright header at the top of each source file.
- Default license is **AGPLv3** with a dual-licensing commercial option
  (consistent with the rest of the `EmiDob-22` projects).

## Git workflow

- Active development branch for assistant work: `claude/claude-md-docs-sron7y`.
- Default branch: `main` (not yet created — repo has no commits).
- Commit with clear, descriptive messages; push with `git push -u origin <branch>`.
- Do **not** open a pull request unless the user explicitly asks.
