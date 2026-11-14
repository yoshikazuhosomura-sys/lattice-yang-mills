# lean/ym-three-volumes-2026-11-13

One Lean 4 package, kept as an archive.

| File | Contents |
|---|---|
| `principia-ym-three-volumes-2026-11-13.tar.gz` | the package: Lake package `ympremisefirst`, library `YMPremiseFirst`, 400 modules (115,217 lines), with `lakefile.lean`, `lake-manifest.json`, `lean-toolchain`, `MODULES.tsv`, `DECLS.tsv`, `axioms.txt` and a README in Japanese |
| `principia-ym-three-volumes-2026-11-13.tar.gz.sha256` | sha256 of the archive: `f8a444517b2f013a287ec20075977cb0afa71c019de2d3c3da577118c05aea62` |
| `axioms-ym-three-volumes-2026-11-13.txt` | 682 lines: a declaration, a tab, and its `#print axioms` result. Every result is `[propext, Classical.choice, Quot.sound]`, a subset of it, or `[]` |

Lean 4 `v4.33.1`, Mathlib `v4.33.1` (commit `0df444a3`, pinned in `lake-manifest.json`).

## Papers that cite it

- `papers/ym-su2-strong-coupling-lean`: all Lean statements of the paper are declarations of this package.
- `papers/ym-fractional-instanton-rate` (version 2): the declarations listed in its Lean section. Three finite algebraic steps of its Theorem A are in `lean/ym-fractional-instanton-rate` instead.

Each paper's `statements.md` lists the declarations with their modules.

The package contains more than these two papers use. It was assembled for an online textbook in Japanese on the website computo ergo sum, and the same archive is distributed there; `DECLS.tsv` inside the archive refers to the chapters of that textbook.

## How to check

Unpack the archive. In the unpacked directory run `lake exe cache get`; then, in the order of the import column of `MODULES.tsv` (dependencies first), compile each module with

    LEAN_NUM_THREADS=1 lake env lean -o <dir>/<module>.olean <file>

adding `<dir>` to `LEAN_PATH`; then run `lake env lean` on the files `checks/AxAll_*.lean` and `checks/AxNew_*.lean`, which print the `#check` and `#print axioms` output for the 682 declarations, and compare with `axioms-ym-three-volumes-2026-11-13.txt`.

This module-by-module compilation, followed by a re-check of every compiled module with Lean's kernel checker (`leanchecker`), is how the package was checked when it was made. Building with `lake build` through the `lakefile.lean` of the package has not been tried. A single module can need about 12 GB of memory.

Ten groups of modules carry the same declarations under the same names and cannot be imported into one file together; no module of the package imports two modules of one group. The README inside the archive lists the groups.
