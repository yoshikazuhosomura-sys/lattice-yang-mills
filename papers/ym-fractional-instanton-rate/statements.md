# statements — 分数インスタントンの率（版 2、2026-11-14）

全て SU(2)・Wilson 作用・格子 (ℤ/N)²×(ℤ/M)²・小さな T²_N に捩れ n₁₂=1・θ=(Z(0)−Z(1))/(Z(0)+Z(1))（平面の流束 n₃₄ の二区画の偏り）。N に一様な言明は、弱い下界 S_min(N,N) ≥ 1/2 だけ（M≫N には届かない）。連続極限は取らない。

Lean の宣言は束 `principia-ym-three-volumes-2026-11-13`（sha256 `f8a444517b2f013a287ec20075977cb0afa71c019de2d3c3da577118c05aea62`。リポジトリの `lean/ym-three-volumes-2026-11-13/` に tar.gz のまま置き、公理の記録 `axioms-ym-three-volumes-2026-11-13.txt` も同じ所）。各宣言の axiom は `[propext, Classical.choice, Quot.sound]`。ColumnChessboard の 5 宣言だけは版 1 のモジュール（リポジトリの `lean/ym-fractional-instanton-rate/`、lake のプロジェクト。ファイルは `FractionalInstanton/ColumnChessboard.lean`、`#print axioms` の出力は `axioms.txt`）。束の注釈は日本語で独自の番号を使う。別の機械での建て直しの記録は版 1 のモジュールだけで、新しい束は束全体の公理の記録を別に取り直して一致を確かめた。

## 量の対応（§2、照合は紙）

| 紙 | Lean | 理由 |
|---|---|---|
| 重み e^{−βS^z}、S^z_p = 1 − ½ z_p tr U_p | `TwistedWilson.ZW` = ∫ exp(β Σ z Re U) | 差は e^{β·6N²M²}、二区画で同じなので θ・ΔF で消える |
| 捩れ n₁₂（各 (1,2) 面に一枚）・n₃₄（N² 枚の板） | `TwistedWilson.zt`（(x₁,x₂)=(0,0)・(x₃,x₄)=(0,0)） | 同じ（q=(0,0)） |
| θ(N,M,β) | `TwistBlocks.thetaM` | 背景 n₁₂=1 |
| S_*(N,ℓ)（ℓ≥2） | `TwistBlocks.Svortex N ℓ` | 枠だけの升は真空の枠で 0（`actB_vac_one`）、枠でないリンクは升の根もとの塊（`blk_l1`〜`blk_l4`） |
| S_N = inf_{ℓ≥2} S_* | `TwistBlocks.SN`（inf_{ℓ≥1}） | ℓ=1 は 2N²（`actB_vac_flip`）で、S_* ≤ 2N² なので同じ |
| S_min(N,M) | `ThetaLimit.Smin` = inf `TwistFlat.defect11` | 背景 (1,1) の作用、達成される |

## 言明

| 論文 | 言明（条件は同じ文に） | 札 | Lean |
|---|---|---|---|
| Theorem A（陽な面積則・柱の率） | N≥2・ℓ≥2・β≥1・M∈2ℓℕ で θ ≤ exp(−(M²/2ℓ²)c₀^{n_B}e^{−6n_B}β^{−3n_B}exp(−βS_*(N,ℓ)−L_∂√(βL(β)/c_R)))。c_R(N,ℓ)>0 は存在だけ。チェス盤は引用。M は偶数なので θ≥0（Prop 7.1）、「θ>0 の所で」の断りは不要 | 紙＋引用 | 有限の代数の三段だけ（版 1 の ColumnChessboard の 5 宣言） |
| Lemma 3.8（平らな枠） | 平らな枠は二つのゲージ軌道。Lean は各切り口の分類と固定群 ±1 だけ、混合の升・二つの軌道・不変量は紙 | 紙＋機 | `TwistBlocks.rigidT_all`・`stab_vacT` |
| Lemma 3.9（枠の二次の剛性） | c_R の存在（Morse–Bott） | 紙 | — |
| Theorem B（固定 M の陽な逆向き） | N,M≥2・β≥1・x=2exp(−βS_min+N²M²(12lnβ+34)) ≤ ½ なら θ>0 かつ −lnθ ≤ 2x | 紙 | — |
| Corollary C（固定 M の率） | 全ての N,M≥1 で、大きい β で 0<θ<1、lim_{β→∞} −ln(−lnθ)/β = S_min(N,M)（**等式**。版 1 は区間 [S_min, S_*]） | 機＋紙（最後の一段） | `ThetaLimit.tendsto_logratio_div`・`TwistFlat.minDefect11_pos`・`ThetaLimit.tendsto_theta_one` |
| Theorem D（太い渦の面積則） | 全ての N≥1・ε>0 で、ある β₀ が在り β≥β₀ ごとに M₀ が在って M≥M₀ で \|θ\| ≤ exp(−M² e^{−β(S_N+ε)})。閾は陽でない。S_N ≤ S_*(N,ℓ)、M は 2ℓℕ に限らない。チェス盤・二次の剛性を使わない | 機 | `TwistBlocks.thick_vortex_floor`（形は \|θ(N,M+1,β)\|） |
| Theorem D（正値） | δ_N>0 で全ての ℓ≥2 に S_*(N,ℓ) ≥ δ_N、S_N>0（δ_N は陽でない） | 機 | `VortexPos.Svortex_ge_unif`・`SN_pos` |
| Theorem D（証明書） | S_*(2,8) ≤ 6.67401・S_*(3,8) ≤ 9.09321・S_*(4,4) ≤ 12.02057、S_N<2N²（N=2,3,4）。計算機の証明書（Cayley の形 q=(s²−\|t\|²,2st)/(s²+\|t\|²)、s=2^16 の有理数の配位、上への丸め、`decide +kernel`）。N=4 の 12.02057 ≈ 1.218π² は π² を越える（π² 未満は Lean でない未収束の冷却の値 9.580 ≈ 0.971π² だけ） | 機（計算機の支え） | `VortexCert.Svortex_*_le`・`SN_*_lt`・`TwistBlocks.thick_vortex_floor_two/three/four`（率 6.675・9.094・12.021） |
| Proposition 6.1（薄い渦の面積則） | 全ての N,M≥1・実の β で \|θ\| ≤ tanh(N²\|β\|)^{M²}。β>0 で \|θ\| ≤ e^{−σ₀M²}、σ₀=−ln tanh(N²β)（ここまで機）。σ₀ ≥ 2e^{−2βN²} は紙の一行（版 1 は M 偶数・指数 M²/4）。全ての M で立つのはこちら | 機 | `TwistedWilson.twisted_vortex_bound_abs`・`thin_vortex_floor` |
| S_* の性質 | 達成・≤2N²・ℓ に非増加・S_*(N,ℓ) ≥ S_min(N,kℓ)・S_min ≤ 2N²、lim_ℓ S_* = S_N > 0 | 紙（正値・S_min>0 は機） | `VortexPos.Svortex_ge_unif` |
| S_min の下界 | 全ての N,M≥1 で S_min ≥ 2N²M²/(N²+M²)²、S_min(N,N) ≥ 1/2。連続の値 π² の 20 分の 1 ほど、M/N→∞ で 0 に近づき M≫N では効かない | 機 | `TwistFloor.defect11_ge_two`・`defect11_sym_half` |
| Proposition 7.1（θ の符号） | M 偶数・全ての実の β・N≥1 で Z(1) ≤ Z(0)、θ ≥ 0（x₄ の鏡映の鏡映正値性） | 機 | `TwistBlocks.theta_nonneg`・`HalfSplit.Z1_le_Z0` |
| Proposition 7.2（Polyakov ループの対） | M≡0 (mod 4)・全ての実の β・b,b′・0≤T≤M で \|⟨P_b(0)P_{b′}(T)⟩₀\| ≤ 2 tanh(N²\|β\|)^{M·min(T,M−T)}。横 N の管の中の下界で N に一様でない。β=1 で右辺が ¼ 未満になるのは M·min(T,M−T) > 3099（N=2）、> 6.8·10⁷（N=3）〔計〕 | 機 | `PolyakovT.polyakov_pair_all` |
| 計算機の値（冷却） | S_*(2,12) ≤ 6.67348665542・S_*(3,12) ≤ 9.07284242009・S_*(4,8) ≤ 9.57961427901（未収束）。周期トーラスの冷却の値は S_min の上界（S_min(3,16) ≤ 9.072494） | 計（機械検査なし） | — |

## 主張しないこと（§8）
- (G1) M に一様な逆向き（希薄な気体の下界）。正確な書き換えと (Pos) も主張しない。
- (G2) lim_M S_min(N,M) が在って S_N に等しいこと。固定 M の率は S_min(N,M)、M に一様な率は S_N（上界の側）。
- (G3) N→∞ で π²（数値だけ）。N に一様なのは S_min(N,N) ≥ 1/2 だけで、M≫N では効かない。
- (G4) c_R と、Theorem A が薄い評価に勝つ β は非明示。Theorem D の閾と δ_N も非明示。
- (G5) 面積則から質量ギャップは出ない。

## 一行訳（日本語）
固定した小さな捩れた T² の上の SU(2) 格子ゲージ理論で、平面の流束の偏りは面積則に従う。その率は、枠を真空に固定した柱に流束を一つ入れたときの最小作用 S_* 以下で（陽な形は紙、β と M が十分大きい所での率 S_N = inf_ℓ S_* の形は Lean）、固定した平面の大きさでは率はちょうど S_min(N,M) である。S_* を分数インスタントンと読むのは半古典の水準で、lim S_min = S_N の同定は開いている。
