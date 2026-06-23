# CLAUDE.md

Guidance for AI assistants (Claude Code and others) working in this repository.

Keep observation and interpretation on separate levels in this file. The
sections below are deliberately labelled **Observed** (facts verifiable from the
repo) vs **Hypothesis** (inference that must be confirmed before acting).

## Observed

- `omega-core` is an **empty repository**: no commits, no tracked files yet
  (this CLAUDE.md is among the first). Verify with `git ls-files` /
  `git log` before making any claim.
- There is no source code, build system, tests, or CI to document.
- Sibling repos in the same GitHub account (`EmiDob-22`): **`ksdz`** (a working
  Python spectral-compression engine whose demo module is `omega_16d_quantum.py`
  and which uses the "OMEGA" brand) and **`EmiDob-22`** (the owner's profile
  README repo).

Do not invent structure or describe files that do not exist.

## Hypothesis (unconfirmed)

- Given the shared "OMEGA" branding and that `ksdz` plugs into an
  `omega_16d_quantum` system, `omega-core` *may* be intended to host the broader
  OMEGA core that KSDZ depends on.

This is inference, not fact. Confirm scope with the user before scaffolding
anything here; do not let it harden into documented architecture.

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
