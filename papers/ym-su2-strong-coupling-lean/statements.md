# Statements — Classical theorems on four-dimensional SU(2) Wilson lattice gauge theory, machine-checked in Lean 4

The rows below are exactly the rows of the correspondence table of `paper.tex` (§11), in the same order, with
hypotheses, file:line in the bundle `principia-ym-three-volumes-2026-11-13.tar.gz` (Lean v4.33.1, Mathlib v4.33.1;
the archive is in the directory `lean/ym-three-volumes-2026-11-13` of the repository https://github.com/yoshikazuhosomura-sys/lattice-yang-mills),
and the record of the axioms. "log" = a line of `axioms-ym-three-volumes-2026-11-13.txt` (same directory) reading
`[propext, Classical.choice, Quot.sound]`; "none" = neither a line of the log nor a `#print axioms` line of its own.
Notation: `t(β) = 18 tanh|β|`, `q = 1 − e^{−2β}`, `P_{N,β}` / `μ_{N,β}` the normalised / unnormalised Wilson
measure on `(ℤ/N)⁴`, `Q_{n,β}` the periodic lift of `P_{2(n+1),β}` to `ℤ⁴`, `v(r)` the Haar volume of a cap.
Auxiliary statements (the two reflection-positivity statements are inputs to Theorems 7.1 and 5.2; the first three kinds are also present in the public OpenAI
construction for general gauge groups) are marked *aux*.

主定理の言明と条件の一覧。各行の日本語は一行訳（条件を落とさない）。

| # | Statement (with hypotheses) | Lean declaration | File:line | Axioms | 日本語の一行訳 |
|---|---|---|---|---|---|
| Thm 4.1, ρ=0 (*aux*) | `N = 2M`, every real `β`, `f` bounded measurable of the closed positive half: `∫ f(Θω) f(ω) dμ_{N,β} ≥ 0` | `TorusRP.wilson_rp` | `Lattice/TorusDecV2.lean:847` | log | 時間方向の格子点の面の鏡映正値性（全ての実の β） |
| Thm 4.1 (*aux*) | the same in each direction `ρ` (Θ conjugated by the exchange of directions 0 and ρ) | `PeierlsPerm.wilson_rp_dir` | `Peierls/PermRPV2.lean:174` | log | 四方向それぞれで格子点の面の鏡映正値性 |
| Thm 4.2(i) (*aux*) | `N = 2M`, `M ≥ 2`, `β ≥ 0`, `F` bounded measurable, gauge invariant, of the crossing links and the open positive side: `∫ F(ω) F(Θ′ω) dμ_{N,β} ≥ 0` | `MidRP.wilson_rp_mid` | `Lattice/MidRPV2.lean:249` | log | ゲージ不変な関数について結合の真ん中の面の鏡映正値性 |
| Thm 4.2(ii) (*aux*) | same `N, M, β`; `H` bounded measurable of the open positive side: `∫ H(Θ′ω) H(ω) dP_{N,β} ≥ 0` | `FullT.full_rp_torus` | `Infvol/FullTV2.lean:211` | log | 開いた正の側の関数なら、ゲージ不変を仮定せず真ん中の面の鏡映正値性 |
| Thm 4.3 (RP) | `N ≥ 1`, `L_t ≥ 1`, `j ∈ ℕ`, `m > −1`, `β ∈ ℝ`; time circle `2L_t` × `(ℤ/N)³`; `φ(c,a₊)` bounded measurable: `∫ φ(c,a₊) φ(c,a₋) e^{−βS_W} Re((det D_W)^{2j}) ∏ dHaar ≥ 0` | `WilsonGauge.site_reflection_positive_wilson_full` | `Gauge/WilsonFullV7c.lean:377` | log | m > −1 で、ゲージの重みとフェルミオンの行列式の重みの積の格子点の面の鏡映正値性 |
| Thm 4.3 (Z>0) | same lattice, every `β, m ∈ ℝ`, every `j`: `∫ e^{−βS_W} Re((det D_W)^{2j}) ∏ dHaar > 0` | `WilsonGauge.partition_pos_wilson_full` | `Gauge/WilsonFullV7c.lean:416` | log | 全ての β・m・j で分配関数は正 |
| §4, global gauge invariance of det D_W | `det physDirac(g·ω·g⁻¹) = det physDirac(ω)` for every `g ∈ SU(2)` | `GaugeDet.physDirac_det_conj` | `FermionLane/GaugeDetV9c.lean:274` | log | 行列式は大域ゲージ変換で不変 |
| Thm 4.3, D_W = std4 | `0 < L_t`: `physDirac` equals the `std4` matrix of the split configuration | `WilsonGauge.physDirac_eq_split` | `Gauge/WilsonFullV7c.lean:479` | log | 物理の添字の作用素と分割データの std4 は等しい |
| Thm 4.3, entries of D_W | the entries of `physDirac`: `m+4` on the diagonal and Wilson hopping terms with antiperiodic signs | `WilsonGauge.physDirac_apply` | `Gauge/DirectEntriesV7a.lean:33` | log | physDirac の成分は r=1・反周期の Wilson–Dirac 作用素のもの |
| Thm 5.1 (*aux*) | `N = 2m`, `m ≥ 1`, every real `β`, block functions, family `F`: `|V(F)|^{N⁴} ≤ ∏_w V(const F(w))` | `FoldWilson.wilson_chessboard_even` | `FoldChess/WilsonChessV1.lean:118` | log | 偶数の辺のトーラスでチェス盤の評価 |
| Thm 5.2 (*aux*) | `β ≥ 81`: `q₁ = e^{−0.88β}/v(1/20)⁴ < 1`; for `m ≥ 2`, `N = 2m`, `X ⊆ P_N`: `∫ ∏_{p∈X} 1[Re U_p < 0] dμ ≤ μ(all)·q₁^{⌊|X|/6⌋}` | `FoldCap.rarity_explicit` | `FoldChess/ExplicitV1.lean:47` | log | β ≥ 81 で大きい面の稀さ（体積に一様、m ≥ 2、弱結合） |
| §5, step (4) | `N = 2m`, `m ≥ 2`, `β ≥ 0`, `r > 0`, `q ≤ 1`, every `X`: bound `μ(all)·q^{⌊|X|/6⌋}`, `q = e^{β(48r²−y)}/v(r)⁴` | `FoldMix.rarity_all_mix` | `FoldChess/MixAllV1.lean:74` | log | 任意の面の集合で率 1/6 |
| §5, step (5) | `K ≥ 2`, `2/K < r`: `v(r) ≥ (2K+1)^{−4}` | `FoldCap.ballQ_ge` | `FoldChess/CapV1.lean:149` | log | 球帽の Haar の体積の下界 |
| Thm 6.1 | `λ ≥ 0`, `e^λ t(β) < 1`; `F` bounded by `c_F`, measurable, on links at time distance `≤ r`; `G` bounded measurable with one-link oscillations `δ_y`: `|E[FG] − E[F]E[G]| ≤ 2c_F e^{λr} Σ_y e^{−λd(y)} δ_y` | `LinkSpec.wilson_cov_dist` | `Sweep/DistDecayV1.lean:364` | log | 時間の距離による共分散の減衰（N に依らない） |
| §6, second form | window `24(1 − e^{−4|β|}) < 1`, supports separated by `r+2+d`: covariance `≤ 2c_Fc_G·6|A|·c(24c)^d/(1−24c)`, `c = 1 − e^{−4|β|}` | `TorusRP.wilson_strong_coupling` | `Lattice/TorusDecV2.lean:1967` | log | 別の窓での減衰の版 |
| Thm 7.1 | `β > 0`, `t(β) < 1`, `m_β = −½ ln t(β)`: ∃ `ν_β` with (a) `Q_{n,β} → ν_β` (whole sequence), (b) translation invariance, (c) reflection positivity on `W`, (d) datum on `W`: `‖T − P_Ω‖ ≤ e^{−m_β}`, variance of `F₀` `≥ e^{−12β}/4`, unit vector `⊥ Ω`, `T[F₀] = 0`, `T ≥ 0`, (e) the same on `W_gi` (variance of `F_p`, no `T[F₀] = 0`), (f) clustering in each direction | `InfMain2.wilson_infvol_main2` | `Infvol/MainV2.lean:23` | log | 全列の弱収束・並進不変・鏡映正値、再構成の ‖T − P_Ω‖ ≤ (18tanhβ)^{1/2}・T ≥ 0（全体とゲージ不変な部門）、四方向のクラスター性 |
| Thm 7.1(a) | `β ≠ 0`, `t(β) < 1`: ∃! weak limit of the whole sequence (∃! carries no information beyond existence) | `InfVol.wilson_infvol_unique` | `Infvol/CauchyV2.lean:196` | log | 全列の弱収束 |
| Thm 7.1(a),(b) | `β ≠ 0`, `t(β) < 1`: the limit is invariant under the four unit translations | `TransI.wilson_infvol_translation` | `Infvol/TransV2.lean:113` | log | 極限の並進不変性 |
| Thm 7.1(d), subsequence form | `β ≠ 0`, `t(β) < 1`: ∃ subsequential limit with the datum on `W`, gap `m_β`, variance bound, unit vector | `WilsonLimit.wilson_massGap_dob_exists` | `Lattice/WilsonDobV1.lean:187` | log | 部分列の極限での再構成とギャップ |
| Thm 7.1(d), T ≥ 0 | `β ≥ 0`, `λ > 0`, `e^λ t(β) < 1`, any subsequential limit: datum on `W` with gap `λ`, variance bound, unit vector, `T ≥ 0` | `FullT.wilson_Tpos_full` | `Infvol/FullTV2.lean:317` | log | W 上の再構成で T ≥ 0 |
| Thm 7.1(e), subsequence form | `β ≠ 0`, `t(β) < 1`: ∃ subsequential limit with the gauge-invariant datum, gap `m_β`, variance bound | `GaugeZ.wilson_massGap_gauge_exists` | `Lattice/GaugeSectorV1.lean:436` | log | ゲージ不変な部門の再構成とギャップ |
| Thm 7.1(f), subsequence form | `λ ≥ 0`, `e^λ t(β) < 1`, any subsequential limit, supports in `0 ≤ x_i ≤ R`, `k ≥ R`: `|Cov(F, G∘S_i^k)| ≤ 4‖F‖‖G‖|S_G| e^{−λ(k−R)}` | `WilsonLimit.cluster_limit` | `Lattice/ClusterV1.lean:180` | log | 極限点での四方向のクラスター性 |
| Thm 7.3 | `β ≠ 0`, `t(β) < 1`: ∃ `ν` with `Q_{n,β} → ν`, the lifts from tori of every size `→ ν`, and along every `s(k) → ∞` (for `β > 0`, `ν = ν_β` of Thm 7.1 by uniqueness of weak limits) | `AllN.wilson_infvol_allN` | `Infvol/AllNV1.lean:160` | log | 全ての大きさのトーラスから同じ極限 |
| Thm 8.1, 441 | `β ≥ 0`, `441q < 1`, `1 ≤ R < N`, `1 ≤ T < N`, any corner and plane: `|E Re W(∂(R×T))| ≤ 6(441q)^{R·min(T,N−T)}/(441(1−441q))` | `AreaLaw.area_law_wilson_general_sharp` | `Area/SharpConstV1.lean:217` | log | 441q < 1 で任意の位置・向きの長方形の面積則 |
| Thm 8.1, 4096 | same with `4096q < 1` and `(16, 4096)` | `AreaLaw.area_law_wilson_general` | `Area/RectMoveV1.lean:168` | log | 4096q < 1 の版 |
| Thm 8.1, corner 0 | corner 0, plane (0,1), `4096q < 1`, `(16, 4096)` | `AreaLaw.area_law_wilson` | `Area/AreaMainV1.lean:63` | log | 原点・(0,1) 面の版 |
| Thm 8.1, max exponent | corner 0, plane (0,1), `441q < 1`: exponent `max(R·min(T,N−T), T·min(R,N−R))` | `AreaLaw.area_law_wilson_max_sharp` | `Area/ExponentMaxV1.lean:89` | log | 指数を二つの向きの大きい方に |
| Thm 8.2 | `β > 0`, `t(β) < 1`, `4096q < 1`: ∃ `ν`, `Q_{n,β} → ν`, and for all `R, T ≥ 1` (rectangle at the origin, plane (0,1)): `|∫ Re W dν| ≤ 16(4096q)^{RT}/(4096(1−4096q))` | `AreaLaw.area_law_infvol` | `Area/InfVolV2.lean:122` | log | 無限体積の極限での面積則（原点の長方形） |
| Thm 8.2, subsequences | `β ≥ 0`, `4096q < 1`, every subsequential weak limit: same bound | `AreaLaw.area_law_limit_sub` | `Area/InfVolSubV1.lean:21` | log | 部分列の極限でも同じ |
| Thm 8.3 | `(ℤ/N)²×(ℤ/M)²`, `β ≥ 0`, `441q < 1`, every `n₁₂`: `|Z(n₁₂,0) − Z(n₁₂,1)| ≤ N²(441q)^{M²}/(441(1−441q))·(Z(n₁₂,0) + Z(n₁₂,1))` | `VortexStrongMN.vortex_floor_MN_sharp` | `Area/VortexMNSharpV1.lean:137` | log | 捩れた分配関数との差は、和に比べて N²(441q)^{M²} の程度以下 |
| Thm 8.3, (ℤ/N)⁴ | the analogous bound on `(ℤ/N)⁴` in the ball realisation, `441q < 1` | `VortexStrong.vortex_floor_sharp` | `Area/SharpConstV1.lean:275` | log | (ℤ/N)⁴ の版 |
| §3, bridge (i) | `TorusRP.wilsonMeasure N β` is the push-forward of the sphere-valued measure of `TwistedWilson` (`M = N`, no twist) | `WilsonBridge.wilsonMeasure_eq_map` | `Bridge/WilsonTwistV1.lean:145` | log | 閉球と球面の二つの定義の橋 |
| §3, bridge (i), total mass | `TorusRP.wilsonMeasure N β (univ) = Z(0,0)` | `WilsonBridge.wilsonMeasure_univ` | `Bridge/WilsonTwistV1.lean:191` | log | 全質量は捩れなしの分配関数 |
| §3, bridge (ii) | `2L_t > 1`: the torus Wilson measure (copy in `Chain.BoxWilsonV2`) equals `e^{6β(2L_t)⁴}` times the push-forward of the pure-gauge measure `e^{−βS_W} ∏ dHaar` | `WilsonGauge.wilsonMeasure_eq_map` | `Box/FermionBaseV8a.lean:562` | log | フェルミオン側の純ゲージの測度との橋（写しの定義に対して） |
| §3, t(β) | definition `18 (e^{2|β|} − 1)/(e^{2|β|} + 1)` | `WilsonLimit.dobConst` (def.) | `Lattice/WilsonDobV1.lean:23` | none | 定義 |
| §3, mass gap | definition `‖T − P_Ω‖ ≤ e^{−m}` | `OSGap.Datum.HasMassGap` (def.) | `Lattice/GapG.lean:809` | log | 定義 |

What is not claimed (§10 of the note): nothing about the continuum limit, a continuum theory or a continuum
mass gap; nothing claimed as new mathematics; Theorem 7.1 is convergence of one periodic family, not uniqueness of
Gibbs measures; the mass is bounded below only; the area law is an upper bound, stated in infinite volume only
for the rectangle at the origin in the plane (0,1); the fermion statement is a positivity property of the weight
only; reflection positivity, the chessboard estimate and subsequential limits are not results of this note.
主張しないこと：連続極限・連続の理論・連続の質量ギャップについては何も言わない。数学として新しいとは言わない。
定理 7.1 は周期の族の一つの列の収束で、Gibbs 測度の一意性ではない。質量は下界だけ。面積則は上界だけで、無限体積では
原点の (0,1) 面の長方形だけ。フェルミオンは重みの正値性だけ。鏡映正値性・チェス盤・部分列の極限はこの論文の結果ではない。
