# Workspace Inventory

*Phase 0 of the target-discovery protocol. Evidence-only: every field is either a
direct observation of a checked-out repository or GitHub API metadata retrieved
this session. Fields that cannot be observed (private repos / out of session
scope) are marked **n/a (no access)** rather than guessed. No architecture is
inferred from repository names.*

## Observability boundary

- **Artifact-level access (files readable):** `ksdz`, `omega-core`, `EmiDob-22`
  (checked out under `/home/user`).
- **Metadata-only (GitHub API; cannot read files):** `JKL-Quantum-Engine`,
  `Kompresja`, `ksdz-edge-optimizer`, `Owner-avatar-gemini-cli` — not in the
  session's repository scope, and three of four are private.

This boundary is itself a finding: the repositories with the most *unknown*
content are precisely the ones that cannot currently be audited.

## A. Repositories with artifact-level access

| field | ksdz | omega-core | EmiDob-22 |
|:--|:--|:--|:--|
| visibility | public | public | public |
| primary language | Python | — (none) | Markdown |
| tracked files | 21 | 1 | 2 |
| code size (tracked) | ~132 KB | 2 KB | 3.3 KB |
| Python LOC | 748 | 0 | 0 |
| tests present? | **no** (no unit tests; `benchmarks/` is an eval harness) | no | no |
| CI present? | **no** (`.github/` absent) | no | no |
| mathematical content? | **yes** — operator model, rate–distortion, compressibility, literature (6 docs) | no | no |
| active development? | yes — 11 commits, last 2026-06-24 (this engagement) | minimal — 2 commits, last 2026-06-23 | minimal — 4 commits, last 2026-06-23 |
| documentation quality | high — `CLAUDE.md`, `README`, `benchmarks/README`, `docs/` ×6 | placeholder only (`CLAUDE.md`) | profile README + `CLAUDE.md` |
| what it is (observed) | lossy FFT spectral-truncation codec + reproducible benchmark suite + math docs | empty repository (one placeholder doc) | GitHub profile README repo |

Notes (observed, not inferred):
- `ksdz` tracked composition: 9 `.md`, 7 `.py`, 2 `.json`, 1 `.txt`, `LICENSE`,
  `.gitignore`. Its maturity (docs, schema-validated benchmarks) was largely
  produced during the prior research cycle, not pre-existing.
- `omega-core` contains exactly one tracked file (`CLAUDE.md`); no code, build,
  tests, or CI. It is empty in the research sense.
- `EmiDob-22` is a profile repository (`README.md` + `CLAUDE.md`); not a research
  artifact.

## B. Repositories with metadata only (no file access)

Observable GitHub metadata (retrieved this session); all file-level fields are
**n/a (no access)** because these repos are outside session scope / private.

| field | JKL-Quantum-Engine | Kompresja | ksdz-edge-optimizer | Owner-avatar-gemini-cli |
|:--|:--|:--|:--|:--|
| visibility | public | private | private | private |
| language (GitHub-detected) | Python | none detected | Python | HCL |
| open issues | 1 | 16 | 2 | 20 |
| created | 2025-10-05 | 2025-11-17 | 2025-11-24 | 2025-07-03 |
| last updated | 2025-10-06 | 2025-11-17 | 2025-11-25 | 2025-11-18 |
| activity span (created→updated) | ~1 day | same day | ~1 day | ~4.5 months |
| files / size / tests / CI / math / docs | n/a (no access) | n/a (no access) | n/a (no access) | n/a (no access) |

Observed metadata signals only (not content claims):
- `JKL-Quantum-Engine`: the only **public**, file-potentially-accessible
  candidate; GitHub language Python; created and last-updated one day apart
  (no observed activity since 2025-10-06).
- `Kompresja`: private; GitHub detected **no language** (consistent with little
  or no code, but unverifiable); created and updated the same day; 16 open issues.
- `ksdz-edge-optimizer`: private; Python; ~1-day activity span; 2 open issues.
- `Owner-avatar-gemini-cli`: private; **HCL** (an infrastructure/config language,
  per GitHub's own detection); the longest activity span and most open issues
  (20). Description string "DO ABACUS" is recorded but interpreted as nothing.

## Summary

- Exactly **one** repository in the workspace is a non-empty research artifact
  with executable code and mathematical content: **`ksdz`** — and it has already
  been the subject of a complete research cycle.
- `omega-core` is empty; `EmiDob-22` is a profile.
- Four further repositories exist on the account but are **not auditable from
  this session** (out of scope / private); only their metadata is observable.

*Reproduce: `git ls-files`/`git log` in each checked-out repo; GitHub
`search_repositories user:EmiDob-22` for the metadata table.*
