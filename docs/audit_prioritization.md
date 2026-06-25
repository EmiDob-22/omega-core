# Audit Prioritization & Recommendation

*Phases 1–3 of the target-discovery protocol. Built only on the observable
evidence in `workspace_inventory.md`. Where evidence is absent (private /
out-of-scope repos), the assessment says so and does not substitute speculation.
Architecture is never inferred from a repository's name.*

## Phase 1 — Research-value assessment

Five axes: engineering maturity, mathematical novelty, verification status,
explicit claims, executable artifacts. Classified Mature / Experimental /
Speculative / Empty — and **Unknown** where there is no file access (a class the
original protocol omits but the evidence requires).

| repo | eng. maturity | math novelty | verification | explicit claims | executable artifacts | class |
|:--|:--|:--|:--|:--|:--|:--|
| ksdz | moderate (no CI/tests/packaging) | low (Phase 7: α is classical) | **high** (executed, schema-validated) | present, normalized | **yes** (benchmarks run) | **Experimental** (well-verified) |
| omega-core | none | none | n/a | none | none | **Empty** |
| EmiDob-22 | n/a (profile) | none | n/a | licensing text only | none | **Empty** (non-research) |
| JKL-Quantum-Engine | n/a (no access) | n/a | n/a | n/a | language=Python (metadata) | **Unknown** |
| Kompresja | n/a (no access) | n/a | n/a | n/a | n/a | **Unknown** |
| ksdz-edge-optimizer | n/a (no access) | n/a | n/a | n/a | language=Python (metadata) | **Unknown** |
| Owner-avatar-gemini-cli | n/a (no access) | n/a | n/a | n/a | language=HCL (metadata) | **Unknown** |

Only one repository can be classified on artifact evidence as a research project
(`ksdz`, Experimental/well-verified). Two are Empty. Four are Unknown for lack of
access — they cannot honestly be called Speculative or Mature without reading
them.

## Phase 2 — Prioritization by expected epistemic value of a full audit

Expected value of an audit ≈ (remaining unknown) × (what could be learned) ×
(feasibility of actually performing it). The decisive constraint is feasibility:
an audit that cannot be started yields nothing until access is granted.

**Top 5 candidates:**

**1. JKL-Quantum-Engine** — *highest expected value, conditional on access.*
- Why worth auditing: it is the **only public** un-audited candidate (files
  potentially readable if added to session scope), and GitHub reports it as
  **Python**, so executable artifacts may exist. Maximal remaining unknown among
  potentially-accessible repos.
- Currently unknown: everything at file level — whether it contains real code,
  tests, claims, or mathematics. The name is not evidence and is disregarded.
- Realistically learnable (once scoped): file/test/CI inventory, whether it makes
  measurable claims, and whether it implements an identifiable operator — i.e. a
  full Phase 0–4 identification, exactly as done for ksdz.

**2. ksdz-edge-optimizer** — *high potential, blocked by access.*
- Why: GitHub language **Python**; the name shares the `ksdz` token, so it *may*
  relate to the already-understood codec — but that is a hypothesis to test, not
  a fact, and cannot be checked without access.
- Unknown: all file content; whether it reuses or diverges from `ksdz_core`.
- Learnable (if access granted): whether the codec is deployed/optimized
  elsewhere, and whether any performance claims there are reproducible.

**3. Kompresja** — *thematically central, but weak observable signal.*
- Why: a "compression" repo is on-theme for this account's work.
- Unknown: GitHub detected **no language** and the repo was created and updated
  the same day with 16 open issues — observably consistent with little code, but
  unverifiable. Could be near-empty or issue-only.
- Learnable (if access granted): whether it contains anything beyond issues.

**4. Owner-avatar-gemini-cli** — *most sustained activity, likely non-research.*
- Why: longest observed activity span (~4.5 months) and most open issues (20).
- Unknown: all content. GitHub language is **HCL** (infrastructure/config), which
  observably points away from a mathematical research artifact, though content is
  unconfirmed.
- Learnable (if access granted): whether it is infrastructure tooling rather than
  a research codebase — likely low math yield.

**5. ksdz** — *fully auditable, but low remaining unknown.*
- Why (and why ranked last for *new* value): it is the only repo I can audit
  right now, but it has already undergone a complete cycle (operator model,
  benchmarks, rate–distortion, compressibility, literature, retrospective).
- Unknown: little remains except the open questions already enumerated in its own
  `docs/` (e.g. the Lorenz>Gaussian inversion, renormalisation-corrected error
  law). These are research extensions, not identification gaps.
- Learnable: only incremental refinement of an already-characterised system.

**The central tension (stated explicitly):** remaining-unknown and
feasibility are *anti-correlated* here. The highest-unknown repos (JKL, the two
privates) are inaccessible; the only fully-accessible research artifact (ksdz) is
already understood.

## Phase 3 — Recommendation (exactly one)

**Within the strictly-available workspace, the only non-empty research artifact
is `ksdz` — and a *new* full audit of it has low expected yield because it is
already characterised. Therefore the single highest-expected-value audit target
is `JKL-Quantum-Engine`, conditional on it being added to the session's
repository scope.**

Justification, on observable evidence only:
- It is the **only public** candidate, so access is plausibly grantable (unlike
  the three private repos).
- GitHub reports it as **Python**, so executable artifacts — required for the
  identification workflow (Phase 3 tests, Phase 4 operator, Phase 6 independent
  estimator) — may exist. (This is a metadata fact, not a content claim.)
- It is **entirely un-audited**, so the expected information gain of a first-pass
  identification is maximal among candidates that could realistically be opened.
- I explicitly do **not** assume what it is from its name; the recommendation is
  to *identify* it, not to presume a "quantum engine" architecture.

**Blocking condition:** `JKL-Quantum-Engine` is not in the current session scope.
The recommendation is therefore actionable only after it is added (e.g. via the
session's add-repo mechanism). If access cannot be granted, the fallback is that
**no new full audit is warranted** — the workspace's only accessible research
artifact (`ksdz`) is already audited, and the remaining work there is the set of
open research questions already documented in `ksdz/docs/`, not a fresh
identification.

Per the protocol: auditing is **not** begun here. This document stops at the
recommendation.

*Evidence basis: `workspace_inventory.md`. No file content of any
metadata-only repository was assumed; classifications for those repos are
`Unknown` by construction.*
