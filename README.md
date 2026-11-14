# Lattice Yang–Mills theory: papers and Lean 4 formalisations

Papers on lattice gauge theory and on related model problems, with the Lean 4 developments that check their machine-checked statements, by **Yoshikazu Hosomura**.

No paper in this repository claims a continuum limit or a mass gap for four-dimensional Yang–Mills theory. Each paper says which of its statements are checked in Lean, and has a section listing what it does not claim.

## Papers

Each directory holds `paper.pdf`, `paper.tex` and, where one exists, `statements.md` (a list of the statements with their Lean declarations, in Japanese; the correspondence is also given in each paper).

| Directory | Title | Pages | Date |
|---|---|---:|---|
| `papers/ym-su2-strong-coupling-lean` | *Classical theorems on four-dimensional SU(2) Wilson lattice gauge theory, machine-checked in Lean 4* | 15 | 2026-11-14, text revised 2026-11-15 |
| `papers/ym-fractional-instanton-rate` | *An area-law bound for SU(2) lattice gauge theory on a twisted small torus whose rate is the action of a flux-carrying column* | 13 | version 2, 2026-11-14, text revised 2026-11-15 |
| `papers/ym-onelink-bakry-emery` | *One-link integration before Bakry–Émery for SU(2) lattice Yang–Mills* | 25 | 2026-09-25, revised 2026-11-14, text revised 2026-11-15 |
| `papers/ym-gap-bridge` | *The inverse squared spectral gap bounds the Langevin Poincaré constant of Euclidean path measures from below* | 12 | 2026-10-09, revised 2026-11-14, text revised 2026-11-15 |
| `papers/ym-coarse-chain-poincare` | *Convex blocks and a coarse Dobrushin chain: a Poincaré bound for the core of the double-well path measure with constants polynomial in ħ* | 18 | 2026-10-17, revised 2026-11-14, text revised 2026-11-15 |
| `papers/ym-h1b-margin-interval` | *An interval-arithmetic certificate for the (T1) margin of the one-dimensional double well for ħ ∈ [0.00195, 0.005]* | 13 | 2026-10-29, revised 2026-10-30 and 2026-11-14, text revised 2026-11-15 |
| `papers/ym-flux-network-blocking` | *Tree-level blocking of an abelian-linearised lattice gauge action as a flux network: the coarse coupling Σf², the quartic contraction Σf⁴/Σf², and their bounds* | 15 | 2026-10-15, revised 2026-11-14, text revised 2026-11-15 |
| `papers/ym-hierarchical-chain` | *An interval-arithmetic chain for the Migdal–Kadanoff flow of SU(2) plaquette weights, from β = 128 to a strong-coupling region* | 21 | version 2, 2026-10-30, revised 2026-11-14, text revised 2026-11-15 |
| `papers/ym-one-row-renormalisation` | *A one-dimensional model of SU(2) convolution renormalisation: the curvature term 2/5, the prefactor fixed point 37/76, and a shape remainder uniform in the number of steps under a computed one-step inequality* | 18 | version 2, 2026-10-30, revised 2026-11-14, text revised 2026-11-15 |
| `papers/ym-boundary-mixed-derivative` | *A boundary observable compared in U(1) and SU(2) lattice gauge theory: one loop, a strong-coupling sign and Monte Carlo* | 12 | 2026-10-29, revised 2026-11-14, text revised 2026-11-15 |
| `papers/ym-face-sum-rule` | *A one-plaquette Schwinger–Dyson identity and a multi-level sum rule for the coarse stiffness in SU(2) lattice gauge theory, with machine-checked arithmetic* | 11 | 2026-10-30, revised 2026-11-14, text revised 2026-11-15 |
| `papers/ym-two-colour-polymer` | *A machine-checked two-colour polymer gas on ℤ⁴: encoding, adjacency degrees, the box stage, and the Kotecký–Preiss condition down to Dobrushin* | 14 | 2026-10-30, revised 2026-11-14, text revised 2026-11-15 |

Files that belong to a single paper are kept beside it: the interval certificates of `ym-coarse-chain-poincare` (`certificates/`), the certificates of `ym-hierarchical-chain` (`ym-hierarchical-chain-certificates-v2.tar.gz`: interval certificates, programs and logs) and the figure of `ym-boundary-mixed-derivative` (`fig-h.pdf`).

## Lean

| Directory | Cited by | Modules | `#print axioms` lines |
|---|---|---:|---:|
| `lean/ym-three-volumes-2026-11-13` | `ym-su2-strong-coupling-lean`, `ym-fractional-instanton-rate` | 400 (one archive) | 682 |
| `lean/ym-fractional-instanton-rate` | `ym-fractional-instanton-rate` (three algebraic steps) | 1 | 5 |
| `lean/ym-onelink-bakry-emery` | `ym-onelink-bakry-emery` | 7 | 580 |
| `lean/ym-gap-bridge` | `ym-gap-bridge` | 1 | 17 |
| `lean/ym-coarse-chain-poincare` | `ym-coarse-chain-poincare` | 9 | 75 |
| `lean/ym-h1b-margin-interval` | `ym-h1b-margin-interval` | 1 | 15 |
| `lean/ym-flux-network-blocking` | `ym-flux-network-blocking` | 12 | 78 |
| `lean/ym-hierarchical-chain` | `ym-hierarchical-chain` | 5 | 44 |
| `lean/ym-one-row-renormalisation` | `ym-one-row-renormalisation` | 7 | 61 |
| `lean/ym-boundary-mixed-derivative` | `ym-boundary-mixed-derivative` | 1 | 9 |
| `lean/ym-face-sum-rule` | `ym-face-sum-rule` | 6 | 64 |
| `lean/ym-two-colour-polymer` | `ym-two-colour-polymer` | 13 | 518 |

- Lean 4 `v4.33.1`, Mathlib `v4.33.1` (commit `0df444a3`, pinned in each `lake-manifest.json`).
- The eleven directories other than `lean/ym-three-volumes-2026-11-13` are Lake projects. Their modules import only Mathlib and do not import each other. Except in `lean/ym-gap-bridge`, the root module of a project imports none of its modules (in some projects several modules restate definitions under the same names), and the library is built through the glob in `lakefile.lean`.
- `lean/ym-three-volumes-2026-11-13` holds one Lean package as an archive; see the README in that directory.
- No `sorry`, no `axiom` declaration, no `native_decide`. `axioms.txt` in each project (for the archive, `axioms-ym-three-volumes-2026-11-13.txt`) is the `#print axioms` output; every line is `propext`, `Classical.choice`, `Quot.sound`, a subset of these, or no axiom.
- `lean/SHA256SUMS` lists the checksums of all files under `lean/`.

Build one project:

```
cd lean/ym-gap-bridge
lake exe cache get
LEAN_NUM_THREADS=1 lake build
```

Plan for 16 GB of RAM.

**What Lean checks.** Lean checks that each formal statement follows from its hypotheses. Which statements of a paper have a Lean counterpart, and which steps are proved on paper or computed numerically only, is stated in the paper (its Lean section and its section on what is not claimed) and in `statements.md`.

## History

Eleven of the twelve papers are revised versions of papers kept until November 2026 in the repository [principia](https://github.com/yoshikazuhosomura-sys/principia) (release v1.1.0 and earlier, archived at Zenodo, doi:[10.5281/zenodo.23296340](https://doi.org/10.5281/zenodo.23296340)). On 2026-11-15 the text of all twelve papers was rewritten for readability; each paper names the corrections made on that occasion in its revision paragraph. The Lake projects under `lean/` were moved from that repository; only README files were changed. `papers/ym-su2-strong-coupling-lean` and version 2 of `papers/ym-fractional-instanton-rate` were not in principia.

Editions of the same papers are published on the website [computo ergo sum](https://computoergosum.com/en/principia/papers/index.html), where the author writes under the pen name *Kiichi* and the AI agents used are listed by name as co-authors. The mathematical content of the two editions is the same; apart from corrections that reach one edition before the other, they differ in the author line, in what is said about the use of AI and about review, in the addresses of the Lean developments and certificates, and in the instructions for checking them.

One further paper of the series, *A conditional theorem: weak ultraviolet existence of four-dimensional SU(2) lattice Yang–Mills theory in a small box, with a machine-checked chain from per-step hypotheses*, was withdrawn on 2026-11-13 and is not part of this repository. The withdrawal notice is `papers/ym-weak-uv-chain/WITHDRAWN.md` in principia.

## Use of AI

This research was carried out with the assistance of Claude Code (Anthropic). The constructions, proofs, computations, the Lean formalisations and the texts of the papers were developed with the AI system under the author's direction. Separate sessions of the system then re-checked the Lean developments and compared the papers with them. The author reviewed the arguments, checked the Lean developments and their axiom logs, and takes full responsibility for the content.

The papers have not been refereed. The separate sessions belong to the same AI system and share its blind spots. What the Lean kernel checks is checked; everything else rests on the author's word.

## License

Apache License 2.0 — see `LICENSE`.
