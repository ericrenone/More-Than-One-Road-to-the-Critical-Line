# More Than One Road to the Critical Line

## The Riemann Hypothesis Proof Landscape, November 2026: Seven Strategies, One Certified Theorem, and the ERI Labs Record

**Eric Ren · ERI Labs · Jersey City, New Jersey · Compiled November 24, 2026**

> Working assumption of this document: there is not one proof of the Riemann Hypothesis. There is one *certified* proof, one *draft* proof by an entirely different route, one *partial* proof that reached 7/8 of the way by a third route, and at least four live research programs that were never going to be the first to the line but that still carry the question nobody has yet answered: *why* the zeros sit where they sit.

---

### Contents

1. [The thirty-second version](#1-the-thirty-second-version)
2. [Status board: every strategy on one page](#2-status-board)
3. [How to read a proof claim in 2026](#3-how-to-read-a-proof-claim-in-2026)
4. [Strategy I — The Stepanov transplant (Alpöge + Claude): certified](#4-strategy-i--the-stepanov-transplant)
5. [Strategy II — The trace formula (Masullo): human, unfinished, instructive](#5-strategy-ii--the-trace-formula)
6. [Strategy III — Metaplectic zero-free regions (OpenAI): 7/8 of the way](#6-strategy-iii--metaplectic-zero-free-regions)
7. [Strategy IV — Weil positivity and pair correlation: the proportion program](#7-strategy-iv--weil-positivity-and-pair-correlation)
8. [Strategy V — Spectral realization (Connes–Consani–Moscovici): the "why" program](#8-strategy-v--spectral-realization)
9. [Strategy VI — The de Bruijn–Newman heat flow: now closed at Λ = 0](#9-strategy-vi--the-de-bruijnnewman-heat-flow)
10. [Strategy VII — Physical routes: Hilbert–Pólya, CPT, and quantum phase transitions](#10-strategy-vii--physical-routes)
11. [The ERI Labs corpus, dissected](#11-the-eri-labs-corpus-dissected)
12. [What changed on November 21, and what did not](#12-what-changed-on-november-21-and-what-did-not)
13. [Watchlist, dated](#13-watchlist-dated)
14. [Sources](#14-sources)

---

## 1. The thirty-second version

**What is proved.** On November 20, 2026, Levent Alpöge (Anthropic; Harvard Society of Fellows) released a four-page note and a 14-part Lean 4 archive of about 17.4 million lines across 175,187 files. The archive proves the Riemann Hypothesis as stated in Mathlib, and the Generalized Riemann Hypothesis for Dirichlet L-functions, for every modulus and every character. On November 21 the Lean FRO and the Mathlib Initiative issued a joint statement certifying both the statement and the proof. Andrew Sutherland (MIT) published an independent verification ledger: all modules compile, the five headline theorems use only Lean's three standard axioms, and the exported proof is accepted by Lean's kernel and by independently written checkers (con-leche, con-ron, nanoda, lean4lean).

**What is not proved.** Nothing about Dedekind zeta functions, Hecke L-functions, or automorphic L-functions has been checked. The Extended Riemann Hypothesis and the Grand Riemann Hypothesis remain open. No human has read the proof. Alpöge's own prose draft, generated with Claude, ran past 250,000 pages and was withheld as unreadable. Three third-party reconstructions (Rubinstein, 164 pages; Zhang, ~70 pages; Adriazola, 66 pages) exist as of November 24, and each states plainly that it is conditional, incomplete, or partly AI-drafted from the Lean source.

**What the proof is.** A descendant of Stepanov's 1969 elementary proof of the Riemann Hypothesis for curves over finite fields, carried into the integers. The obstruction that stopped this route for fifty years is *multiplicity*: Stepanov makes an auxiliary polynomial vanish to high order at every point, and over the integers there is nothing to differentiate. The proof manufactures multiplicity by composing a chain of roughly √X theta lifts between definite unitary groups over an abelian CM field, controls the size of the resulting objects with Bost's slope inequality and Arakelov-style covolume bounds, controls denominators with Galois cohomology and Iwasawa theory, and lands on a one-sided bound for a smoothed prime sum that, by a Landau-type lemma and the functional equation, forces every zero onto the line.

**What else exists.** The same afternoon, Ravi Vakil posted Alessandro Masullo's 940-page, twelve-year, no-AI draft of GRH for Hecke L-functions over all number fields, by a Connes-style trace formula on the idele class group. Within hours, AI-assisted reviewers reported problems; a public Lean triage now lists about 750 errata and the chapter that would deduce GRH contains only placeholders. Six weeks earlier, OpenAI's internal model had proved the quasi-Riemann Hypothesis (no zeros with real part above 7/8) through metaplectic forms, in Lean. Three months earlier, an unreleased Claude build had lifted the proportion of zeros known to be on the line from 41.6% to 67.2% through Weil positivity and pair correlation, and the human community pushed that to 67.35% by October. Alain Connes' February survey and the Connes–Consani–Moscovici spectral triples remain the most developed attempt at a *spectral* explanation. Experimental physics has, since November 2025, a five-qubit demonstration tying the zeros to dynamical quantum phase transitions.

**What ERI Labs said in advance.** The register-crossing mechanism, the Lean-only format, the verification regime, the interpretation crisis, and the two-cultures split were all on the record by August 23, 2026, most of them 12–30 months ahead of ERI's own windows. The explicit miss was placing RH itself outside reach before 2031. ERI's separate *physical* program (the Page-time conjecture, the Cauchy–holography correspondences, the golden-ratio equilibrium) is examined in Section 11 with the same standard applied to everyone else: what is established, what is conjecture, and what was simply wrong.

---

## 2. Status board

Legend for *Form*: **Lean** = machine-checked formal proof · **MS** = human manuscript · **Program** = research framework with partial theorems · **Exp** = experimental/numerical.

| # | Strategy | Who | Form | Proves (as of Nov 24, 2026) | Verification | Still open |
|---|---|---|---|---|---|---|
| I | Stepanov transplant via theta lifts | Alpöge with Claude | Lean, 17.4M lines | RH; GRH for Dirichlet L-functions, all moduli and characters | Certified Nov 21 (Lean FRO + Mathlib); Sutherland ledger; multi-kernel | ERH, Grand RH; a human-readable proof; how much new theory is inside |
| II | Trace formula on the idele class group | Masullo (reviewed by Conrad; posted by Vakil) | MS, 940 pp | Claims GRH for Hecke L-functions over all number fields | ~750 errata in public Lean triage; Ch. 13 (deduction of GRH) empty; author calls it unfit for dissemination | Whether the trace formula (Thm 12.5.1.1) holds; whether Ch. 13 can be written |
| III | Metaplectic zero-free regions | OpenAI internal model; follow-ups by Liu, Kontorovich, Axiom Math | Lean (7/8); MS (11/12) | No zeros with Re(s) > 7/8 for ζ and Dirichlet L; Hecke/Dedekind extensions | 7/8 formalized; 11/12 human-edited, not formalized | Superseded for ζ and Dirichlet by I; still the live route for families I has not reached |
| IV | Weil positivity + pair correlation (proportions) | Claude research build; Alpöge–Furman; Lamzouri; later preprints | Lean + arXiv | ≥ 67.35% of zeros simple and on the line; ≥ 83.9% distinct | Lean library `zeta23`; Conrey and Goldston reviewed; human re-proof by Lamzouri | Method cannot reach 100%; now a historical stepping-stone and a library |
| V | Spectral realization: truncated Weil form, zeta spectral triples | Connes; Connes–Consani–Moscovici; Connes–van Suijlekom | Program | Criticality of truncated zeros is a theorem; numerical agreement to 10⁻⁵⁵ | Convergence to the true zeros unproved | A self-adjoint operator whose spectrum *is* the zeros; the "why" |
| VI | de Bruijn–Newman constant | Rodgers–Tao (Λ ≥ 0); Polymath 15 (Λ ≤ 0.22); 2026 computer-assisted refinements | Theorem + certified numerics | RH ⇔ Λ ≤ 0; with I, Λ = 0 exactly | Lower bound is a theorem; upper bounds certified numerically | Closed as a route to RH; remains a lens on zero dynamics |
| VII | Physical routes: Hilbert–Pólya, Berry–Keating, CPT gauging, DQPT | Betzios–Gaddam–Papadoulaki; Wei–Long et al.; many | Program + Exp | Correspondences, not proofs; 5-qubit DQPT signal at β = 1/2 only | Experimental; no operator with the zeros as exact spectrum | An actual Hamiltonian; whether RH *has* a physical reason |
| — | ERI Page-time conjecture (RH ⇔ σ_Page = 1/2) | ERI Labs | Program | A proposed equivalence and roadmap; no step proved | Not independently examined | Every step (Section 11) |

The single most important row is the gap between I and V. Strategy I settles *that* the zeros are on the line. Strategy V (and VII) ask *why*, in the Hilbert–Pólya sense of exhibiting the zeros as a spectrum. The certified proof produces no operator. That gap is where the next decade of this subject lives.

---

## 3. How to read a proof claim in 2026

Eight days before the Alpöge release, Kevin Buzzard (Imperial) published a checklist for any claim that a result is "checked in Lean." It became the standard the community applied on November 21, and it is worth internalizing because every strategy in this document will eventually be measured against it.

**The four questions.**

1. Does the Lean statement match the informal mathematical statement?
2. Does the code compile?
3. Does the code prove the theorem as stated, from standard axioms only? (Tool: `lake comparator`.)
4. Does the proof survive several independent kernels, at least one formally verified? (Tool: `lake comparator --paranoid`.)

**How the Alpöge archive answered them.** The RH statement was not written by Alpöge; it is Mathlib's own `RiemannHypothesis`, vetted by Lean and number-theory experts before any of this happened. A community file isolated that statement, importing only Mathlib, and two independent tools (`comparator` and `con-leche --compare`) confirmed the proven theorem matches it. Dozens of people reproduced the build and obtained an identical raw export. The export was then checked on an *inert* form, out of reach of any code in the proof sources, by Lean's kernel, by con-leche and con-ron (each carrying its own formal soundness proof relative to set theory), and by third-party checkers in other languages. The codebase depends directly only on Mathlib.

**What a green build does not tell you.** Three things, in increasing order of importance.

- *Mathlib's definitions mean what mathematicians intend.* This is the soft spot Sutherland names in his own caveats. A definition cannot be machine-checked against an idea in someone's head. In practice the risk is low for `riemannZeta` and `RiemannHypothesis`, which have been in Mathlib for years and were written for exactly this day; it is higher for the GRH statements about Dirichlet L-functions, which is why the ledger spells out "all moduli, all characters."
- *Scope.* "GRH" on Sutherland's page means Dirichlet L-functions and nothing broader. Dedekind zeta, Hecke, and automorphic L-functions are explicitly *not among* the checked statements. Press coverage routinely elides this.
- *Understanding.* A checked proof is not an explanation. As of November 24 nobody can say in ordinary mathematical prose why the theorem is true; Buzzard told Al Jazeera that understanding is currently absent and that people worldwide are translating pieces of the code into English. He expects a human account in weeks. If he is right, the proof was alien for a season. If he is wrong, mathematics has its first permanent epistemological artifact of the kind ERI described in August.

**Why the second claim of November 20 fails the same test.** Masullo's draft is a manuscript, not Lean, and so Buzzard's questions do not apply directly. But the community applied the spirit of them within hours: volunteers began formalizing the paper's statements, and an AI-assisted review (organized by Eric Naslund) tested specific theorems against specific test functions. The result is a public errata file, not a certificate. The contrast between the two November 20 events is the cleanest illustration available of why "formalize everything" became the norm.

## 4. Strategy I — The Stepanov transplant

**Status: certified. Scope: RH and GRH for Dirichlet L-functions. Author: Levent Alpöge, working with Claude. Released November 20, 2026; certified November 21, 2026.**

### 4.1 The claim, in the author's words and the community's

The note at `alpo.ge/remark.pdf` opens: "I believe I have, working with Claude, discovered a proof." It says the method already yields GRH, that the Extended Riemann Hypothesis should follow with more time, and that the arguments were formalized in Lean without assumptions. Only the Lean was released; the author judged a 250,000-page unreadable draft inappropriate to publish.

The Lean FRO and Mathlib Initiative statement of November 21 says: "We hereby certify that both the statement and the proof of the Riemann Hypothesis are correct."

Between those two sentences sit 41 days of dated work and 24 hours of community verification.

### 4.2 The timeline (from the note; compiled by Claude at Alpöge's request)

| Date | Step | What it is, in plain terms |
|---|---|---|
| Oct 6 | Stepanov determinant | The seed: a determinant that plays the role of Stepanov's auxiliary polynomial, interpreted first as "Stepanov with multiplicity one" |
| Oct 6 | Bost slope inequality | The size-control tool: lattice slopes bound how large an integer built from automorphic data can be |
| Oct 6 | Iwasawa tower via pigeonhole on F_qⁿ/F_q | The function-field analogy that suggests a tower of fields |
| Oct 8 | Weil-type positivity bound | A first result "greater than 1 − η": close to the line, not on it |
| Oct 9 | Divisibility on a CM curve for inert primes | Where the arithmetic gain comes from: inert primes, not split ones |
| Oct 14 | Determinants containing GGP periods; relative trace formula; Cauchy–Schwarz on a projected Poincaré series | The rank and orthogonality machinery |
| Oct 19 | Quadratic form and automorphy from theta on a sixfold cover of GL₅; choice of Iwasawa tower using Behrend | Specific arithmetic inputs, including an additive-combinatorics construction |
| Oct 20 | Switch to the von Mangoldt sum via the Guinand–Weil sign and a variance test-function trick | The statistic that will finally be bounded |
| Nov 15 | Iterated theta lifts between totally definite unitary groups, winning multiplicity m ≈ √X | The breakthrough: multiplicity manufactured by chaining lifts |
| Nov 15 | Norms, levels, cancellation of order-m terms; lower bound on divisibility of the m-fold lift; seesaw identifies the lift's period as a Bessel period; cost of each lift; integral structure across Hecke characters; weakening of Vandiver for classes not killed by twisting; covolumes and congruences | The day most of the proof closed |
| Nov 16 | GRH | Done |

Two features of this table matter for everything that follows. First, the *idea* steps (Oct 6–20) and the *closing* steps (Nov 15–16) are separated by almost four weeks, which matches Alpöge's description of a long confusion followed by a finish in which Claude far outpaced him. Second, the note names the human contribution precisely: Alpöge found two ideas in a toy setting, recognized the Stepanov structure in an OpenAI release that had quietly folded in a Siegel-type argument (he read it at once as Stepanov without multiplicity), and guided the collaboration to the right situation. Claude found the key step, the chain length, and carried the automorphic-forms work in which Alpöge says he has little mastery.

### 4.3 The architecture, in plain words

Three third-party documents now exist that try to read the Lean back into mathematics: Michael Rubinstein (Waterloo), *The Alpöge–Claude proof of the Riemann hypothesis explained for the Riemann zeta function* (164 pages); Robin Zhang (IHÉS), *A preliminary note on Alpöge's proposed proof of GRH* (~70 pages); Jimmie Adriazola (Arizona State), *An end-to-end reconstruction* (66 pages); plus an 11-page architecture guide. What follows is a synthesis of those documents. Each of them states caveats, repeated in 4.5 below, and none of them is the proof.

**Step 0 — The reduction.** RH follows from a *one-sided* bound on a smoothed prime sum. Define

G(x) = Σ_{n ≤ x} Λ(n)(x/n − 1) − x log x + (1 + γ)x

(the ramp-smoothed von Mangoldt sum with its main term removed). If G(x) ≤ x^{1/2 + η} for every η > 0, as an *upper* bound only, and only on a sparse sequence of intervals [Y, Y^{3/2}] with Y → ∞, then a Landau-type lemma excludes zeros with real part above 1/2. The functional equation ρ ↦ 1 − ρ excludes zeros to the left. That is the whole logical skeleton; everything else is proving the one-sided bound.

**Step 1 — Chebyshev's principle: divisibility bounds size, size bounds primes.** A nonzero integer divisible by p^{e_p} for many primes is at least as large as the product; conversely, an upper bound on its size bounds Σ e_p log p. This is the arithmetic analogue of Stepanov counting zeros with multiplicity: Stepanov builds a polynomial vanishing to order m at every point of a curve, and the degree bound then caps the number of points. The classical obstruction over the integers is that n! and its relatives have prime exponents with floor functions in them; the method needs an integer whose prime exponents are *smooth*, without rounding. Rubinstein's model case is instructive: derivatives of the lemniscate sine give integers whose exponents at inert primes of Z[i] grow like a·p/(p² − 1), while at split primes there is no gain at all (the formal group has height one, by Deuring). That asymmetry between inert and split primes, visible on October 9 in the timeline, is the first real idea.

**Step 2 — Three repairs.** (a) *Size:* use squared Gaussian norms so that the relevant size is about √(a!) rather than a!. (b) *Divisibility:* a large order a and a weight w turn the exponent at p into (a/p^h − w)₊, which is exactly the ramp kernel in G. (c) *Primes:* a character 1 − χ_d selects odd powers of inert primes; the relevant places form a two-row table coming from the field Q(ζ_N + ζ_N⁻¹, √−q, √−d).

**Step 3 — Theta lifts between definite unitary groups.** The objects are theta lifts between spaces of lattices over an abelian CM field, using totally definite unitary groups, where everything is finite-dimensional and the lift is literally a matrix of derivatives of theta functions. The comparison inequality is

e · log p ≤ log‖T‖ + μ_max(M) − μ(L),

with μ denoting lattice slopes in the sense of Stuhler and Grayson; the inequality is Bost's slope inequality. Covolumes of the lattices of automorphic forms are bounded through sections of Hodge bundles on moduli of CM abelian varieties, with arithmetic Hilbert–Samuel formulas (Gillet–Soulé, Zhang, Moriwaki), Yuan's bigness criterion, and height comparisons. Petersson norms of the lifts are expressed through special L-values and local integrals (Rallis; Gan–Qiu–Takeda); dimensions come from Weyl's formula and Siegel-mass-type lattice counts.

**Step 4 — Multiplicity by chain length.** This is the step that had no analogue over the integers. Composing m lifts costs an error of size x/m from the single ends and m from accumulation; balancing gives m ≈ √x and the exponent 1/2. Rubinstein notes the diagnostic: if the accumulated cost were m² rather than m, the balance would land at exponent 2/3 and the method would prove only a zero-free region, not RH. Alpöge's note records exactly this, an a priori stopping point near 2/3, on November 15, before the cost was brought down. In other words, the proof passed through the quasi-RH regime on the way to the line, and the reason it did not stop there is a specific estimate on how errors accumulate along the chain.

**Step 5 — Denominators and rank.** Projecting onto Hecke eigenspaces introduces denominators; these are controlled through congruences between Galois representations, with bounds on Selmer-type groups via Tate–Poitou duality, Taylor–Wiles deformation theory, Kato's Euler system, and the vanishing of the Iwasawa μ-invariant (Ferrero–Washington) across cyclotomic towers. Rank and approximate orthogonality of the images are handled by a trace formula. A Behrend-type construction (sets with no three-term progressions) selects complex places; the note speculates this may be unnecessary, but the reconstructions use it.

**Step 6 — Assembly.** The main inequality between divisibility and size of the theta-lift matrices (Rubinstein's "(M)"), together with two auxiliary estimates for Dirichlet characters, gives the one-sided bound on G, and Step 0 finishes.

### 4.4 What is certified, line by line

Sutherland's ledger lists five headline theorems: the Riemann Hypothesis in Mathlib's form, its equivalent formulations, and three GRH statements for Dirichlet L-functions (no zeros with real part above 1/2; all zeros in the critical strip on the line; for every modulus and every character). All five use only Lean's three standard axioms. All 175,187 modules compile under Lean v4.33.1 / Mathlib v4.33.1. nanoda and con-leche accept the full exported proof; lean4lean accepts every compiled module. As of November 23 one long-running check, a single-threaded replay of the original export by Lean's kernel, was still listed as in progress; the statement comparison and axiom check had passed.

Not checked, by Sutherland's explicit statement: Dedekind zeta functions, Hecke L-functions, automorphic L-functions. The author expects ERH with more time. Nothing about that expectation is verified.

### 4.5 What the reconstructions admit

Honesty about the state of human understanding requires quoting the reconstructions' own caveats, paraphrased:

- Rubinstein: the main inequality (M) is *not proved* in his paper; the argument is complete only conditionally on (M) and on several quoted Lean statements. Steps 4 and 6 of Alpöge's timeline were not found in the Lean development and were matched from the announcement alone; step 3 is largely absent; step 2's stated exponent could not be confirmed on the simplest example. A key identity was verified numerically to more than 400 digits but has no written proof. The authors have not compared the formalized statements with the published ones in detail. Some Galois-cohomology inputs could not be matched to published results.
- Zhang: most of the text from Section 2 onward was drafted by an AI model (GPT 6 Pro) reading the Lean, then rewritten by hand on November 20; he cannot claim fidelity to 17 million lines; the exposition is condensed and imperfect.
- Adriazola: not yet complete; internal dependencies and literature checks still under audit.

These are responsible documents doing exactly what the moment requires. They are also, collectively, the best evidence that "alien proof" is the correct description as of this date.

### 4.6 Open questions specific to Strategy I

1. **How much new theory is inside?** Estimates range from zero (a synthesis of existing automorphic, Arakelov, and Iwasawa machinery) to on the order of a thousand pages of material no one has written before. The answer determines whether ERI's August claim that RH "requires new structures" was misplaced or simply wrong.
2. **Can the chain be shortened?** Alpöge expects major simplification and says he may have baked suboptimal choices into the argument. A proof-golf project is already running against the upstream repository.
3. **Does the route extend?** Hecke L-functions over CM fields are the natural next target because the proof already lives over an abelian CM field. Dedekind zeta functions for general number fields are harder; automorphic L-functions of higher rank harder still.
4. **Is there an operator?** The proof uses theta correspondences, which are spectral objects, but it never exhibits a self-adjoint operator whose spectrum is the zeros. See Sections 8 and 10.

## 5. Strategy II — The trace formula

**Status: human draft, unfinished by the author's own account, with documented errors. Scope claimed: GRH for Hecke L-functions over every number field (which contains RH, Dirichlet GRH, and ERH). Author: Alessandro Maria Masullo. Posted by Ravi Vakil on November 20, 2026, hours after Alpöge.**

### 5.1 What was released and why it was released early

Vakil, writing on his *Math 216* page during an AMS board meeting, posted a 940-page PDF titled *The Music of the Primes*. He said the work is entirely human, that Brian Conrad (Masullo's doctoral adviser) had been reading it closely for months, and that the original plan called for roughly a year of polishing before any announcement. He explicitly declined to vouch for the strategy's soundness and invited the community to formalize and fill small gaps. The early release was a reaction to the Alpöge announcement.

Masullo's own statement, quoted by Baez: the paper is "in no way in a state that is fit for submission." He acknowledges many bugs, especially in the final chapters.

### 5.2 The strategy

Masullo follows the oldest spectral idea in the subject, in the form Connes gave it: realize the zeros as the spectrum of an operator and the primes as closed orbits on the other side of a trace formula, and read GRH off the formula.

Concretely, the draft works with functions on the idele class group of a number field. A test function defines an operator by convolution. On the spectral side each zero contributes a Mellin transform; on the geometric side the contributions are organized prime by prime, with Poisson summation killing the large primes and a local version of Connes' trace formula handling the finitely many that remain. Most of the 940 pages compute the geometric side. The chapter layout is: adelic theta functions (Ch. 2), idelic zeta functions (Ch. 3), spaces of adelic theta functions and idelic Z-functions (Ch. 5), Schauder bases of idelic zeta functions (Ch. 7), the spectral side (Ch. 10), the geometric side (Ch. 12), with the trace formula itself labelled Theorem 12.5.1.1 and called the main theorem of the work. Chapter 13 is meant to deduce that the zeros lie on the half-line, with a multiplicity bound. Chapter 14 discusses why the method does *not* extend to function fields.

The key move, in Baez's simplified telling: take the test function t^{−z} on t > 1. The spectral side becomes a sum of 1/(z − ρ) terms, i.e. the logarithmic derivative L′/L; the geometric side gives the prime sum. If the geometric side can be shown holomorphic to the right of Re(z) = 1/2, then L′/L has no poles there and GRH follows. The technical difficulty is that this test function is discontinuous and not compactly supported, so Masullo approximates with smooth cutoffs and needs uniform bounds to pass to the limit via Montel's theorem.

### 5.3 What has been found wrong

- **The prime-2 test.** An AI-assisted review organized by Eric Naslund tested one theorem on a test function near 2. The theorem predicts log 2; the review argues the limit is 0 because two required conditions cannot hold simultaneously.
- **The page-444 basis claim.** The draft extends terminology from Schauder bases to Markushevich bases and asserts the coordinate functionals are then bounded. That is apparently false in the Markushevich setting, and the claim may be used downstream.
- **Chapter 5.** The public Lean triage (the `riemann-masullo` formalization projects) reports that the structure theorem for spaces of adelic theta functions (Theorem 5.2.1.1) has a printed proof that does not work, and that later results depend on it.
- **The errata count.** As of November 22–24, the formalization's ERRATA file has about 750 entries: roughly 270 statements false as printed, 400 imprecise or wrongly justified, 50 placeholders or missing pieces, and 25 reports of parts not stated in Lean. Twenty-eight foundational steps have no working justification yet.
- **Chapter 13.** As released it contains the headings of three sections and placeholders. The main theorem of the chapter is not stated.
- Separately from the formalization, concerns have been raised about gaps in the proof of the trace formula itself (Theorem 12.5.1.1). Conrad has reportedly told *Scientific American* the manuscript is undergoing major revision.

### 5.4 Why it still matters

Three reasons, none of them sentimental.

First, scope. If the draft were repaired it would prove strictly more than Strategy I has certified: GRH for all Hecke L-functions of all number fields, which is the Extended Riemann Hypothesis and beyond. That is exactly the territory Sutherland's ledger marks as unchecked.

Second, independence. Baez's assessment is that Masullo's approach is quite unlike Alpöge's, so one does not make the other redundant. A second proof by a route that goes through an operator and a trace formula would be the first step toward a Hilbert–Pólya-type explanation of a theorem that is now known to be true.

Third, the inversion. Chapter 14 argues the trace-formula method does not extend to function fields. Strategy I is a transplant *from* function fields. The two November 20 documents are, in a precise sense, mirror images: one carries the finite-field proof into number fields and cannot yet reach beyond Dirichlet characters; the other works natively over number fields in full generality and cannot reach back to the finite-field case. Even if Masullo's draft never closes, understanding exactly where it breaks is worth having; Baez says as much.

### 5.5 What would resolve it

A repaired Theorem 5.2.1.1; a correct version of the Markushevich-basis claim or a route around it; a written Chapter 13; and, given the scale of the errata file, probably a Lean formalization that the author participates in rather than one done to him. The crowd formalization already running is Culture-A tooling applied to Culture-B output, which is one of the more interesting sociological facts of the week.

---

## 6. Strategy III — Metaplectic zero-free regions

**Status: partial result, formally verified. Scope: all nontrivial zeros of ζ and of every Dirichlet L-function have real part in [1/8, 7/8]. Author: OpenAI internal model. Dated September 30, 2026; released October 6, 2026 among 377 announced / 722 released results.**

### 6.1 What was proved

The quasi-Riemann Hypothesis asks for a strip strictly narrower than 0 < Re(s) < 1 containing all nontrivial zeros. Before October 2026 no such strip was known for ζ. OpenAI's 199-page paper proves Re(ρ) ≤ 7/8 (hence, by the functional equation, Re(ρ) ≥ 1/8), and the result was formalized in Lean. A second, 49-page manuscript dated October 5 proves the weaker 11/12 bound by similar techniques; it is the one humans have mostly studied, it is the only one of the 722 papers a person edited, and it was not formalized at release. Radziwiłł's observation, reported by Quanta, is that the great majority of the *consequences* of RH already follow from a quasi-RH of this kind.

### 6.2 How

The proof lives in the metaplectic register: forms on covers of GL, cubic Gauss sums, and a 2021 formula of Dunn and Radziwiłł on bias in cubic Gauss sums (Patterson's conjecture) as a key ingredient. Experts had believed this branch's tools insufficient and that a different part of number theory would be needed; the model's contrary conviction proved productive. Iwaniec had come near the right family in 2002 and missed it. Sarnak repurposed a Princeton course to study the proof. Lichtman called it "the most significant AI-for-math achievement so far, by quite a margin." Dunn's characterization is the one to remember: an unexpected synthesis of familiar ideas, introducing no new concepts.

Follow-on work arrived within weeks: improved zero-free half-planes for ζ and Dirichlet L (Liu, arXiv:2610.12234, with Lean); zero-free half-planes for Hecke L-functions over number fields (arXiv:2610.26835); a quasi-RH for Dedekind zeta functions (Cureton–Thorner / Axiom Math, with Lean); independent Lean formalizations of the 11/12 argument and of the zero-free half-plane for ζ (Kontorovich); and downstream uses, for instance in bounds on imaginary quadratic class numbers.

### 6.3 Where it stands after November 21

For ζ and Dirichlet L-functions the 7/8 result is now a corollary of Strategy I. For Hecke L-functions and Dedekind zeta functions it is *not*: those families are outside the certified perimeter, and the metaplectic zero-free regions are, as of this writing, the strongest unconditional statements available there. The quasi-RH program therefore survives as the frontier for exactly the L-functions Alpöge has not yet reached, and as a worked example of a register crossing (analytic → metaplectic) that the field had not thought to make.

One more connection. Alpöge's note credits an OpenAI release that had quietly folded in a Siegel-type argument, which he immediately recognized as Stepanov without multiplicity. The October 6 corpus is, on Alpöge's own account, where the seed of Strategy I was visible before anyone had planted it over the integers.

---

## 7. Strategy IV — Weil positivity and pair correlation

**Status: a family of unconditional proportion theorems, Lean-formalized, now superseded as a route to RH but historically decisive. Scope: lower bounds on the fraction of zeros that are simple and on the line.**

### 7.1 August 10, 2026

Anthropic's research post *Learning more about Claude's mathematical capabilities* reports that an unreleased research build, prompted in Claude Code by Jarred Sumner (a non-mathematician on staff) to make a serious attempt at RH, raised the proven lower bound on the proportion of zeros on the critical line from 41.6% (Pratt–Robles–Zaharescu–Zeindler, 2020) to 67.2%. Two sessions, 31 million output tokens. The first attempt generated 650 ideas that went nowhere. The second ran about 60 subagents for a day and a half: two developed the key ideas, thirteen contributed, thirty tried and failed, thirteen validated, two wrote the paper. Levent Alpöge and Ralph Furman examined the work internally; Brian Conrey and Dan Goldston examined it externally on short notice; Eric Easley produced a Lean formalization that passes `comparator`.

The method: form a function space carrying the quadratic form induced by Weil, with positive-definite subspaces tied to zeros on the line and negative-definite subspaces tied to zeros off it; use first- and second-moment information to bound the rank. The inputs are Montgomery's 1973 pair correlation, the unconditional pair-correlation theorem of Baluyot–Goldston–Suriajaya–Turnage-Butterbaugh (Acta Arithmetica, 2024), work of Aryan, and a 2000 paper of Bombieri. The post states: "We don't expect that the techniques Claude used will lead to proving the Riemann hypothesis."

That sentence was correct. The proof that arrived fourteen weeks later used none of this machinery.

### 7.2 The human aftermath

- **Alpöge–Furman, arXiv:2608.13637** — the write-up: more than two thirds of the zeta zeros are simple and on the critical line.
- **Lamzouri, arXiv:2609.02882 (Sep 2)** — a new, conceptually simpler, all-human proof of the 67.25% bound via a Hilbert-space inequality, plus two new unconditional estimates: at least 88.76% of zeros are simple or on the line (or both), and the average of the two proportions is at least 83.62%.
- **arXiv:2609.33043** — more than 83.69% of zeros are distinct.
- **arXiv:2610.08965** — more than 83.9% distinct and more than 67.35% simple and on the line, with a Lean 4 development built on the August library (`zeta23`) that formalizes the explicit formula, the Riemann–von Mangoldt formula, and the Montgomery–Vaughan inequality from Mathlib, and ships "Challenge" files with statements left open by design.

### 7.3 Why it mattered even though it could not finish

Three reasons. It established the Lean-first release pattern three months before the RH proof made that pattern mandatory. It created the formal library the later proportion papers extended. And it was the episode in which a model given an "unreasonable" prompt by a non-mathematician produced a result experts had not managed in fifteen years, which is the clearest available evidence for the claim (ERI, Aug 18) that mathematical reasoning in these systems scales without being targeted.

### 7.4 A note on a specific ERI claim

ERI's August document *Riemann and the Information Transition* asserted that 67.25% is "the tight bound for the current generation of analytic tools" and that exceeding it "requires new mathematical input." Within eight weeks the same tools gave 67.35%. The underlying point, that bandwidth-one pair-correlation information has a ceiling well short of 100%, is standard and correct; the specific number was not tight, and the phrasing overstated what was known. This is recorded here so that it is not repeated.

## 8. Strategy V — Spectral realization

**Status: research program with partial theorems and extraordinary numerics; the natural home of the "why" question. Principal authors: Alain Connes; Connes–Consani–Moscovici; Connes–van Suijlekom.**

### 8.1 The February letter

Connes' survey *The Riemann Hypothesis: Past, Present and a Letter Through Time* (arXiv:2602.04022, February 3, 2026) reviews 165 years of approaches and appends an original contribution written as a letter to Riemann using only mathematics available in 1859. The method: extremize a quadratic form Q(φ) built from the Riemann–Weil explicit formula, restricted to functions supported in a finite interval (the restriction of Weil's quadratic form, in modern language), subject to a normalization. The minimizer involves prolate-type functions in the tradition of Slepian, Pollak and Landau. Using only primes less than 13, the Fourier–Mellin zeros of the minimizer approximate the first fifty Riemann zeros with errors from 2.6 × 10⁻⁵⁵ for the first to about 10⁻³ for the fiftieth. The paper also records a connection between the Weil quadratic form and information theory, which it describes rather than develops.

### 8.2 Zeta spectral triples

Connes, Consani and Moscovici, *Zeta Spectral Triples* (arXiv:2511.22755, November 2025; EMS Series of Lectures in Mathematics, 2026) propose a strategy toward RH based on a spectral realization of the zeros. They construct self-adjoint operators D^{(λ,N)} as rank-one perturbations of the scaling operator on L²([λ⁻¹, λ], d*u) with periodic boundary conditions. The construction uses only the Euler product over primes p ≤ x = λ², and the spectra of the resulting operators coincide, with striking numerical accuracy, with the lowest nontrivial zeros of ζ(1/2 + is), even for small x. Theorem 1.1(iii) of that paper identifies the spectrum of D^{(λ,N)} with the zeros of the Fourier–Mellin transform of the ground state of the truncated Weil form. Self-adjointness is secured by an extension of the Carathéodory–Fejér theorem for Toeplitz matrices.

### 8.3 What is a theorem and what is not

This distinction is the one most often blurred in secondary accounts, including ERI's own August documents.

- **Theorem (Connes–van Suijlekom, arXiv:2511.23257):** for every finite cutoff c, the zeros of the Fourier–Mellin transform of the even-sector ground state of the truncated Weil form are *real*, i.e. the approximating zeros lie on the critical line by construction.
- **Open:** whether these approximating zeros *converge* to the actual Riemann zeros as c → ∞. If they do, RH follows by Hurwitz's theorem applied to the Mellin transforms (as spelled out in arXiv:2605.20224, *High-Precision Approximation of Riemann Zeros via the Truncated Weil Form*, which treats Section 6 of Connes' letter as an open question and documents 113 orders of magnitude of convergence numerically). The convergence is the whole content of RH in this framework, and it is unproved.
- **Conditional:** arXiv:2611.13129 (*The uncertainty operator, the Weil ground state and the zeros of zeta*) proves positivity of the Weil quadratic form under stated hypotheses and studies the ground state numerically.

So: the self-adjointness of D^{(λ,N)} does *not* force the Riemann zeros onto the line. It forces the *approximants* onto the line, and the question of whether the approximants are the zeros is exactly RH. ERI's June and August documents stated the stronger version; the stronger version is not what was proved. See Section 11.

### 8.4 What November 21 changes for this program

Less than one might think, and in one respect it makes the program more important.

RH is now a theorem. A spectral realization is therefore no longer needed to *prove* RH. But the Hilbert–Pólya question was never only about truth; it is about exhibiting an operator whose spectrum is the zeros, because such an operator would *explain* the Montgomery–Odlyzko GUE statistics, the Berry–Keating semiclassics, and the whole physics literature of Section 10. Strategy I provides no such operator. Strategy V remains the most developed candidate for one. The convergence question of 8.3 is unchanged by the Lean certificate; a proof of convergence would now be a proof that the Connes–Consani–Moscovici operators *are* a Hilbert–Pólya realization, which is a stronger and more interesting statement than RH.

There is also a practical consequence. Now that RH and Dirichlet GRH are known, every conditional result in the spectral program whose only hypothesis was RH is unconditional. The positivity results of 2611.13129, for example, should be re-read with that in mind.

---

## 9. Strategy VI — The de Bruijn–Newman heat flow

**Status: closed as a route to RH on November 21, with a clean corollary. Principal results: Rodgers–Tao (2018), Polymath 15 (2019), computer-assisted refinements in 2026.**

### 9.1 The setup

Deform the Riemann ξ-function by a backward heat flow with parameter t. De Bruijn (1950) and Newman (1976) showed there is a constant Λ ∈ (−∞, 1/2] such that the deformed function has only real zeros if and only if t ≥ Λ, and RH is equivalent to Λ ≤ 0. Newman conjectured Λ ≥ 0, i.e. that RH, if true, is "barely" true. Rodgers and Tao proved Λ ≥ 0 in 2018. Polymath 15 proved Λ ≤ 0.22 in 2019.

### 9.2 The 2026 refinements

Through the summer and autumn of 2026 a sequence of computer-assisted and partly AI-assisted upper bounds appeared: Λ ≤ 0.1787854 (Gomila, August); correlated and retuned translated probes giving Λ < 0.149 and a conditional Λ < 0.116 (Raymond, September–October); collective contraction in the heat flow (Planat, arXiv:2609.37164); a conditional Λ ≤ 0.13963 (arXiv:2610.12803); and a certified classical-strip comparison (arXiv:2610.18214) that explicitly computes what the OpenAI 7/8 result implies for the height of zeros of the deformed function. Several of these acknowledge AI assistance in their derivations and are unrefereed working notes.

### 9.3 The corollary

Since RH ⇔ Λ ≤ 0 and Λ ≥ 0 is a theorem, the November 21 certificate gives

**Λ = 0.**

Newman's conjecture is confirmed in its sharpest form: the Riemann Hypothesis is true and holds with no margin at all. None of the 2026 upper-bound papers can improve on this, and the program's open question is closed. What survives is the heat-flow picture as a tool for studying zero dynamics, Lehmer pairs, and the statistics of near-collisions, none of which the Lean proof addresses.

---

## 10. Strategy VII — Physical routes

**Status: correspondences, experiments, and conjectures; no proof, and after November 21 no need for one, but a live question that the certified proof leaves untouched. Representative works: Berry–Keating (1999); Bender–Brody–Müller (2017); Betzios–Gaddam–Papadoulaki (2021); Wei, Long et al. (2025–2026).**

### 10.1 The Hilbert–Pólya frame

The conjecture is that there is a self-adjoint operator whose eigenvalues, with multiplicity, are the imaginary parts of the zeros. Montgomery's 1973 pair correlation and Odlyzko's numerics give the zeros the level repulsion of the Gaussian Unitary Ensemble, which is the signature of a chaotic quantum system without time-reversal symmetry. Berry and Keating proposed H = xp (suitably regularized) as the semiclassical candidate, with the primes as periodic orbits. None of these constructions has produced the exact spectrum.

### 10.2 CPT as a gauge symmetry (Betzios–Gaddam–Papadoulaki)

*Black holes, quantum chaos, and the Riemann hypothesis* (arXiv:2004.09523; SciPost Physics Core 4, 032, 2021) explores gauging CPT as a quantum boundary condition in phase space. The authors find that this provides a natural semiclassical regularization and discretization of the continuous spectrum of a Hamiltonian related to the dilation operator, that the discretized spectrum is in correspondence with the zeros of the Riemann zeta and Dirichlet beta functions, and that the same Hamiltonian captures the near-horizon dynamics of the Schwarzschild scattering matrix. The paper's closing speculation, answering Landau's question to Pólya, is that the physical reason for RH is that CPT is a gauge symmetry in quantum gravity. This is a proposal, not a theorem, and the authors say so.

### 10.3 Dynamical quantum phase transitions (Wei, Zhai, Lu, Yang, Gao, Wei, Song, Nori, Xin, Long)

*The Riemann Hypothesis Emerges in Dynamical Quantum Phase Transitions* (arXiv:2511.11199, November 14, 2025; Nature Communications, 2026) establishes a correspondence between the nontrivial zeros and dynamical quantum phase transitions (DQPTs) in two realizable quantum systems. The authors' framing is that time, rather than energy, is the variable: the zeros appear as the moments at which a return amplitude collapses nonanalytically, and this happens only when the system's parameter sits at inverse temperature β = 1/2. The work includes a demonstration on a five-qubit processor in which the signal collapse matched the first five nontrivial zeros on the critical line and only there. It is an experiment and a correspondence; it is not a derivation that β = 1/2 is forced.

### 10.4 The proof with no Hamiltonian

A machine-checked proof of RH by theta lifts and Arakelov geometry tells us where the zeros are and nothing about whether they are eigenvalues of anything. This is the sharpest way to state what remains for physics after November 21: the truth of RH was never the obstacle to the physical program; the absence of an operator was, and still is. If Strategy V's convergence question is ever settled, it will supply the operator. If Strategy II's trace formula is ever repaired, it will supply the orbits. Until then, the physical literature's status is unchanged by the certificate: suggestive, numerically striking, and unproved as an explanation.

## 11. The ERI Labs corpus, dissected

The ERI corpus bearing on RH has two distinct parts that are usually read together and should not be. The first is a *forecasting* program (May 29 – August 23, 2026) about how AI-assisted mathematics would unfold. The second is a *physical* program (June 11 and August 2026) proposing that RH is equivalent to a statement about black-hole information. The first has a scorecard and did well. The second has no scorecard yet, and this section gives it one.

### 11.1 The forecasting program, re-scored against verified facts

Each entry below was checked against the primary record summarized in Sections 3–7. Where ERI's own November 24 scorecard was accurate it is kept; where it was generous it is corrected.

| ERI prediction (date, window) | Verified outcome | Verdict |
|---|---|---|
| **Alien proof**: a Lean-verified theorem whose strategy no human can explain (Aug 11, 2027–2029; Aug 12, by Q2 2028) | 17.4M lines certified Nov 21; author withheld 250,000-page draft; three reconstructions all self-described as conditional or AI-drafted; Buzzard: nobody yet knows why it is true | **Landed, ~15 months early.** Caveat: if a human account exists by January, "alien" was seasonal, which ERI's own Part XI listed as the open question |
| **Lean as validation standard** for claimed solutions to classical open problems (Aug 12, by 2028) | Aug 10 (Lean), Sep 8 (Lean), Sep 30 (Lean), Nov 20 (Lean *only*); Buzzard's Nov 12 checklist is the de facto gate | **Landed, ~2 years early** |
| **Interpretation** as a distinct class of mathematical work (Aug 23; venue by 2029) | Sarnak course on quasi-RH; Rubinstein, Zhang and Adriazola reconstructions plus an 11-page architecture guide; proof-golf project; crowd formalization of Masullo | **Partial, early.** Work exists; no institution yet |
| **Collaboration Pattern C**: formal verification + human interpretation (Aug 11) | Machine certified in 24h; humans begin weeks-to-months of interpretation | **Landed** |
| **Prestige transfers to verifiers/digesters** (Aug 23) | The public arbiters were Lean FRO, Mathlib, Sutherland, Buzzard. But Saha argued credit belongs to the human who steered and proposed a Fields Medal for Alpöge | **Mixed.** Verification became the arbiter of *truth*; credit for *discovery* still flowed to the named human. Both halves of the prediction have evidence |
| **Two coexisting cultures** (Aug 11, 2028–2031; Aug 23) | Lean-only AI-assisted proof and 940-page no-AI draft of the same theorem posted hours apart; Lamzouri's human re-proof of the August AI bound | **Landed, ~2 years early** |
| **Frontier-lab affiliation displaces institutional prestige** (Aug 12) | Alpöge (Harvard junior fellow) at Anthropic; the only two Millennium-class claims of 2026 came from inside labs | **Landed** |
| **Grokking-style multi-domain jump** 9–18 months after Aug 2026 (Aug 11) | Navier–Stokes claim (Sep 8), 722-paper release incl. quasi-RH (Oct 6), RH/GRH (Nov 20): three Millennium-class events in 11 weeks | **Direction right, window too conservative by ~a year** |
| **Corporate capture risk; "once in Lean no corporation owns it"** (Aug 23) | Lean release let an independent community certify RH in 24 hours with no dependence on Anthropic; Navier–Stokes credit dispute shows the other case | **Landed** |
| **Problem selection unpredictable from mechanism** (Aug 11) | Every public forecaster, ERI included, placed RH years out; it fell next | **Landed (meta)** |
| **w≥5 (automorphic/motivic) accessible via human–AI collaboration** (Aug 11 depth table) | The proof lives in theta correspondences, Galois representations, Iwasawa theory, Arakelov geometry; human steered, AI finished | **Landed** |
| **Mathematical reasoning emerges and scales without being targeted** (Aug 18) | Aug 10 result from a non-mathematician's prompt; Nov 20 finish by the model | **Landed** |
| **RH "requires new structures, not register crossing"** (Aug 11) | Quasi-RH: no new concepts (Dunn). RH: a transplant of Stepanov through existing machinery; amount of new theory unknown (zero to ~1,000 pages). Alpöge's note does describe one idea in the toy setting as new and shocking | **Missed as stated.** The route was cross-register. Whether a new *structure* sits inside is open; a new *idea* certainly does |
| **"AI will not solve these [Clay problems] before 2031"** (Aug 11, Aug 23) | RH and Dirichlet GRH certified Nov 21, 2026 | **Missed by ≥ 4 years.** Still the shortest horizon on the public record (Tao ~2050; Metaculus ~May 2035) |
| **Navier–Stokes open before 2031** (Aug 11) | OpenAI claimed finite-time blowup with *smooth forcing* on Sep 8, Lean-formalized; Clay still lists the problem unsolved; credit disputed with Buckmaster–Alpöge, whose own Lean-checked blowup results for related equations were posted the same week | **Pending.** The forcing term is the asterisk; not certified at the RH standard; the Clay formulation is not obviously settled |
| **67.25% is the tight ceiling of current tools** (Aug, *Information Transition*) | 67.35% by October with the same tools | **Missed** (minor, but recorded) |
| Prime gap < 100; sunflower; chromatic number ≥ 6; R(5,5) (May 29) | Not yet due | **Open** |

**Net.** Of fifteen scoreable calls, ten landed or landed early, two are mixed or partial, three missed. The misses share a shape: every one of them is a case where ERI treated a specific object (RH; the Clay list; a specific numerical bound) as structurally exempt from a mechanism the rest of the corpus called universal. The hits share the opposite shape: predictions about *process* (format, verification, culture, collaboration pattern). The lesson ERI should carry forward is its own Part II sentence, that mechanism is predictable and problem selection is not, applied without exceptions.

### 11.2 The physical program, examined

The documents are *On the Physical Proof Strategy for the Riemann Hypothesis* (June 11), *The Spectral Geometry of Unitary Evolution* (August), and *Riemann and the Information Transition* (August). They share a central claim, a set of correspondences, a golden-ratio thesis, and a list of predictions. Each is taken in turn.

#### 11.2.1 The central claim: RH ⇔ "σ_Page = 1/2 for every unitary black hole"

**What is asserted.** That the Riemann Hypothesis is the same statement as: every evaporating black hole in a unitary, UV-complete quantum gravity has its thermodynamic Page time at exactly half its Bekenstein–Hawking entropy. A zero at Re(s) = σ is said to correspond to a unitary theory whose information turning point is at fraction σ.

**What is established independently.** The Page time at S_BH/2 (in the thermodynamic limit) is Page's 1993 theorem for Haar-random pure states of a bipartite system: the entanglement entropy of the smaller subsystem is nearly maximal, so the radiation entropy turns over when the radiation Hilbert space becomes larger than the remaining black hole's, i.e. at half the entropy. The island formula reproduces this in JT gravity and elsewhere. None of this involves ζ.

**Consequence for the claim.** As of November 21, both sides of the proposed equivalence are known to be true: RH by Alpöge–Claude, and the half-entropy Page time by Page (under its hypotheses). An equivalence between two true statements is vacuous unless a *derivation* connects them. The four-step roadmap (QES-as-Cauchy-principal-value; Z₂ symmetry of the entropy arc; zeros as spectral resonances of a CFT partition function; closure) is the derivation that would give the claim content, and no step of it has been carried out, by ERI or anyone else. Step 3 in particular ("the spectral zeros of the boundary CFT partition function that determine the oscillations of S_rad(t) are the nontrivial zeros of ζ") is not a reformulation; it is a new conjecture with no stated model in which it holds. The certified proof does not help here, because it exhibits no operator and no partition function.

**Verdict.** Not falsified, because nothing in it has yet been made precise enough to falsify. Not supported, because the one testable component (Page time at half entropy) was already a theorem for reasons unrelated to primes.

#### 11.2.2 The Cauchy–holography correspondences

**What is asserted.** Twelve-plus structural identities: Cauchy integral formula = holographic principle; residue theorem = information extraction; argument principle = island formula; Hardy spaces = entanglement-wedge reconstruction; Hardy–Ramanujan = Bekenstein–Hawking via Cardy; Hardy–Littlewood circle method = island formula. The documents insist these are identities, not analogies.

**What holds up.** The Hardy–Ramanujan / Cardy correspondence is real and standard: Cardy's 1986 formula S ≈ 2π√(cL₀/6) is a modular-transformation asymptotic of exactly the Hardy–Ramanujan type, and through AdS₃/CFT₂ (Strominger 1998) it counts BTZ black-hole microstates. The "primon gas" reading of ζ as a partition function of a free boson gas with primes as single-particle energies, with a Hagedorn-type singularity at s = 1, is also standard (Julia; Spector; Bakas–Bowick). The observation that the functional equation s ↔ 1 − s and the time-reversal symmetry of the Page curve are both Z₂ symmetries fixing a midpoint is true and is the honest kernel of the whole program.

**What does not.** "Cauchy integral formula = holographic principle" is an analogy about boundary data determining interior data; the Cauchy formula is a statement about holomorphic functions on a disc, the holographic principle is a statement about Hilbert spaces of quantum gravity, and no map between them is given. The same applies to residues, to the argument principle, and to the circle method. The circle-method/island correspondence in particular assigns "major arcs = col(F)" and "minor arcs = ker(F)" without defining a Fisher matrix on either side. These are suggestive metaphors. Calling them identities, and dating them with "167-year gaps," is rhetoric, and it is the single feature of the physical documents most likely to cause a working mathematician to stop reading.

#### 11.2.3 Specific claims that are wrong or misattributed

These are listed because a research record that corrects itself is worth more than one that does not.

1. **"Connes and Consani proved that ... self-adjointness forces the spectrum to be real ... [so] the zeros must lie on Re(s) = 1/2."** (June 11, Section VI; August, §2.2.) Not what was proved. Connes–Consani–Moscovici construct self-adjoint operators whose spectra numerically match the low zeros; Connes–van Suijlekom prove the *approximating* zeros are real for every finite cutoff. Whether the approximants converge to the true zeros is open and is equivalent to RH in that framework (Section 8.3). The ERI text converts an open convergence question into a completed proof.
2. **"Alpöge & Furman (2026) prove ... with failure probability < 10⁻¹² for verification."** (August, §2.3, Datum 2.) No such figure appears in arXiv:2608.13637. The result is an unconditional theorem with a Lean formalization; there is no failure probability. The number appears to be a conflation with Connes' coincidence estimate (≈10⁻¹²³⁵) or with something else entirely.
3. **"The Page entropy fraction with QES corrections is 1 − ln φ ≈ 0.519."** (June 11, Section V; August, throughout.) No source in the island/QES literature gives this. The August *Information Transition* document itself undercuts it: in §8.3 it reports the classical-vs-quantum difference as "0.019 ≈ ln(φ)/25" and calls the match "not perfect but suggestive." A quantity cannot be both a derived equilibrium condition and a loosely matched prediction. As it stands, 1 − ln φ is an ERI conjecture with no derivation.
4. **"The 67.25% is the tight bound for the current generation of analytic tools."** Falsified by 67.35% within eight weeks (Section 7.4).
5. **Prediction IB-8: quasinormal-mode frequency ratios f_{n+1}/f_n → φ.** The Schwarzschild and Kerr QNM spectra have been computed to high precision for forty years (Leaver 1985; the Berti–Cardoso–Starinets tables). Overtones at fixed (ℓ, m) have slowly *decreasing* real parts and nearly equally spaced imaginary parts; a geometric ratio of φ in the real frequencies is not what those tables show. This prediction should be checked against the published tables before it is kept; on its face it is already in tension with known results.
6. **The 4/3 "submersion law."** The claim that the Bakry–Émery / log-Sobolev constant degrades across a Riemannian submersion as dim(F)^{−1/3}, and that mixing time therefore scales as dim(M)^{4/3}, is asserted with the sentence "this is not tunable, it is geometry." No theorem of Bakry–Émery, O'Neill, or anyone else is cited that produces a 1/3 power from the horizontal curvature tensor, and none is known. The grokking and AGN "confirmations" offered for it are a single 13-day variability timescale and an unpublished fit over ~50 runs. This is the weakest quantitative claim in the corpus.

#### 11.2.4 The golden ratio

The documents find φ in: the Sgr A* wind cone (half-angle 22.5° ≈ arcsin(1/φ²) = 22.46°); a primordial-black-hole capture bifurcation at mass ratio 1/φ² ≈ 0.382; an optical-depth transition at ln φ ≈ 0.481; the QES Page correction; Fisher eigenvalue spacing; the fine-structure of vacuum pair creation; the ratio of Compton-thick to Compton-thin AGN; and Fibonacci denominators in a continued-fraction "clock" during grokking.

The arithmetic is right: arcsin(1/φ²) is 22.46°, 1/φ² is 0.382, ln φ is 0.481. The inference is the problem. A published opening angle of "approximately 45°" with no quoted uncertainty, matched to a one-parameter family of candidate constants, is not a 0.2% coincidence; it is a post-hoc selection. The same is true of a 30/70 split "close to 1/φ." The standard that would make these claims science is the one ERI applies to everyone else in the forecasting documents: state the prediction *before* the measurement, with an error bar, and with the candidate constant fixed in advance. Prediction IB-6 (a 50-qubit simulator resolving 2,000 zeros to 10⁻¹⁰ by 2032) and Test B of §8.1 (vacuum-birefringence peaks at Im(ρ_n)) are at least stated that way; the astrophysical φ claims are not.

#### 11.2.5 What survives, and what to do with it

Three things in the physical program are worth keeping.

**The positivity analogy.** Weil's criterion says RH is equivalent to positivity of a quadratic form on test functions. Fisher information is a positive quadratic form. Entanglement entropy functionals are extremized by positivity conditions. Connes himself, in the February letter, records a connection between the Weil form and information theory without developing it. ERI's instinct that these three positivity statements rhyme is defensible as a *research question*. It is not defensible as the assertion that the Weil form *is* a holographic entropy functional. The right move is to write down, in one specific model (JT gravity with a matrix-integral dual is the obvious candidate, since Saad–Shenker–Stanford give its partition function as a GUE-type matrix ensemble and the zeros are GUE-distributed), a quadratic form on that model's test functions, and ask whether its positivity is Weil positivity for some L-function. That is a paper. "This is not analogy, this is identity" is not.

**The Z₂ observation.** The functional equation and the time-reversal symmetry of the Page curve are both reflections fixing a midpoint. If the Hilbert–Pólya operator is ever found, its CPT-type symmetry will be what pins the spectrum to the line, and Betzios–Gaddam–Papadoulaki's proposal is the nearest thing in the literature to a mechanism. ERI's version of the idea is compatible with theirs. It should cite them as the origin and build on their Hamiltonian rather than restating the idea in Cauchy's vocabulary.

**The forecasting discipline.** The reason the forecasting program scored well is that it dated its predictions, named its windows, and published a miss as a miss. The physical program should adopt the same practice: convert every "prediction" in Sections 5 and 8 of the August documents into a dated table with a stated falsification threshold, and retire the ones (IB-8; the 4/3 law; 1 − ln φ) that are already in tension with established results. ERI's own prescription, "formalize everything in Lean," applies to ERI: the one step of the June roadmap that is pure mathematics (Step 1, QES extremization as a Cauchy-principal-value regularization) could be stated as a precise theorem about a precise class of functionals, and either proved or shown false. Until a single step of the roadmap is in that form, the physical program is a set of analogies with a scorecard of zero, and should be described that way.

## 12. What changed on November 21, and what did not

### 12.1 Now unconditional

Everything proved "under RH" or "under GRH for Dirichlet L-functions" in the last century is now a theorem, subject to the usual care about which GRH a paper assumed. A partial list of the consequences that fall out immediately:

- **Prime number theorem with square-root error.** ψ(x) = x + O(√x log² x), with explicit constants from Schoenfeld; π(x) and Li(x) differ by O(√x log x).
- **Prime gaps.** p_{n+1} − p_n ≪ √p_n log p_n (Cramér's conditional bound).
- **Lindelöf.** |ζ(1/2 + it)| ≪ t^ε, and the same for Dirichlet L-functions.
- **No Siegel zeros.** Every Dirichlet L-function is zero-free on the real segment (1/2, 1), so Siegel's ineffective theorem is replaced by effective bounds throughout.
- **Primes in arithmetic progressions.** Error term O(√x log² x) uniformly in the modulus; the least prime in a progression mod q is ≪ φ(q)² log² q.
- **Miller's primality test** is a deterministic polynomial-time algorithm without hypothesis (its correctness proof assumed GRH for Dirichlet characters, with Bach's witness bound 2 log² n).
- **de Bruijn–Newman.** Λ = 0 exactly (Section 9).
- **Every conditional theorem in the spectral program** of Section 8 whose only hypothesis was RH.

### 12.2 Still open

- **ERH** (Dedekind zeta functions) and **GRH for Hecke L-functions**: Alpöge expects the former with more time; Masullo's draft claims the latter; neither is certified. Consequences that need these, such as Artin's primitive-root conjecture (which uses GRH for Dedekind zeta functions of Kummer fields), remain conditional.
- **Grand RH** for automorphic L-functions, and with it most of the Langlands-side conditional literature.
- **Hilbert–Pólya.** No operator. Strategy V's convergence question and Strategy VII's physical proposals are untouched.
- **A human-readable proof.** None exists. The three reconstructions are conditional, incomplete, or AI-drafted by their own description.
- **The Clay Millennium Prize.** Rules (revised 2018) require publication in a qualifying outlet, at least two years of availability for scrutiny, and general acceptance. No qualifying publication exists; the two-year clock has not started; the earliest conceivable award is late 2028. The Register reports Clay has moved the problem's status from "unsolved" to "active"; it is not listed as solved.
- **Journal handling.** Where and how a Lean-only proof is "published" in a qualifying outlet is itself an open institutional question, and one of the ERI forecasts (dual review tracks by 2028) now has a concrete test case.

### 12.3 The structural picture

Seven roads, one destination reached. The road that arrived was the one almost nobody was watching: an elementary finite-field argument from 1969, carried across by machinery (theta correspondences, Arakelov geometry, Iwasawa theory) that was built for other purposes, assembled by a human who chose the destination and a model that found the chain. The roads that did not arrive are not thereby closed. Two of them (II and V) are the only ones that could ever answer the question the certificate leaves open, and one of them (III) is still the frontier for the L-functions the certificate does not cover.

---

## 13. Watchlist, dated

| Item | What resolves it | Why it matters | Horizon |
|---|---|---|---|
| Human-readable account of Strategy I accepted by analytic number theorists | Alpöge's promised write-up; completion of Rubinstein's conditional (M) or Adriazola's audit | Decides "alien for a season" vs. standing epistemological shift | Buzzard: weeks; realistic: Q1 2027 |
| Amount of genuinely new theory inside the 17.4M lines | Expert audit of the architecture guides; proof-golf results | Decides how wrong "requires new structures" was | Q1–Q2 2027 |
| Extension to Hecke L-functions over CM fields; to Dedekind zeta | Sutherland ledger entries; new archive parts | Closes the gap between what is certified and what "GRH" means in common usage | Alpöge: "with more time" |
| Masullo Theorem 5.2.1.1 and Chapter 13 | Revised draft with Conrad; errata file trending to zero | Second, independent, spectral route; broader scope | Author planned ~1 year |
| Convergence of truncated-Weil-form zeros (Strategy V) | A proof, or a counterexample, in the Connes–van Suijlekom setting | Would supply a Hilbert–Pólya operator for a theorem now known to be true | Open-ended |
| Navier–Stokes: Clay-formulation status and credit | Independent certification at the RH standard; Clay statement | ERI's remaining Clay-list miss or hit | 2027 |
| Clay qualifying publication of Strategy I | A journal or equivalent outlet accepts a Lean-only submission | Starts the two-year clock; tests dual-track review forecast | 2027 |
| Metaplectic zero-free regions for Hecke/Dedekind families | Further Liu / Axiom Math preprints | Frontier for L-functions outside the certified perimeter | Rolling |
| ERI physical program: first precisely stated step (QES as CPV, as a theorem about a defined class of functionals) | A statement that can be proved or refuted; ideally in Lean | Converts a set of analogies into a research program with a scorecard | ERI's choice |
| ERI remaining Tier-2 bets: prime gap < 100, sunflower, chromatic number ≥ 6, R(5,5) | 2027 results | Tests the register-crossing framework on specific problems | 2027–2028 |

---

## 14. Sources

Only sources that bear directly on claims in this document are listed. Press coverage is cited only where it carries a primary quotation or a fact not available elsewhere.

### Primary: the November 20–24, 2026 record

- L. Alpöge, *Remark* (four-page note and Lean archive, parts 01–14), November 20, 2026 — alpo.ge/remark.pdf
- Lean FRO and Mathlib Initiative, *Lean verification of the Riemann Hypothesis* (joint statement), November 21, 2026 — leanprover-community.github.io/blog/posts/riemann-hypothesis/
- A. V. Sutherland, verification ledger and summary, updated November 21–23, 2026 — math.mit.edu/~drew/grh
- K. Buzzard, *…and the proof is checked in Lean*, Xena Project, November 12, 2026 — xenaproject.wordpress.com/2026/11/12/and-the-proof-is-checked-in-lean/
- M. Rubinstein, *The Alpöge–Claude proof of the Riemann hypothesis explained for the Riemann zeta function* (working draft, 164 pp.) — math.uwaterloo.ca/~mrubinst/alpoge_claude_grh/zeta-paper.pdf
- R. Zhang, *A preliminary note on Alpöge's proposed proof of the Generalized Riemann Hypothesis* (IHÉS, ~70 pp.), November 21–22, 2026 — ihes.fr/~rzhang/files/GRH%20note.pdf
- J. Adriazola, *An end-to-end reconstruction of the Alpöge–Claude route to the Riemann hypothesis* (66 pp.), November 21, 2026 (as cited by Baez)
- R. Vakil, announcement of A. M. Masullo, *The Music of the Primes* (940 pp.), Math 216 page, November 20, 2026; mirror at kskedlaya.org/masullo.pdf
- J. C. Baez, *Masullo on the Riemann Hypothesis*, Azimuth, November 22, 2026 — johncarlosbaez.wordpress.com/2026/11/22/masullo-on-the-riemann-hypothesis/
- Lean formalization and errata projects for the Masullo draft: github.com/mccorvie/riemann-masullo; github.com/ldgarcia/riemann-masullo; github.com/ityonemo/music-of-primes
- Al Jazeera, *Riemann hypothesis: Has the world's most famous maths problem been cracked?*, November 21, 2026 (Saha and Buzzard quotations)
- Scientific American, November 21 and 23, 2026 (independent verification; Conrad on Masullo revision)
- The Register, November 24, 2026 (Clay status; 250,000-page draft)
- The Decoder, November 22, 2026 (Tao ~2050; Metaculus ~May 2035)

### Primary: the 2026 run-up

- Anthropic, *Learning more about Claude's mathematical capabilities*, August 10, 2026 (updated August 13) — anthropic.com/research/riemann-zeta; companion preprint at www-cdn.anthropic.com/564f962e60643842f5fcb4a17c9dbc8f608f1c37.pdf; Lean library `zeta23` in github.com/anthropics/formal-math
- L. Alpöge, R. Furman, *More than two thirds of the zeta zeros are simple and on the critical line*, arXiv:2608.13637
- Y. Lamzouri, *A new proof that more than 2/3 of the zeros of the Riemann zeta function are simple and on the critical line*, arXiv:2609.02882
- *More than 83.69% of the zeros of the Riemann zeta function are distinct*, arXiv:2609.33043
- *More than 83.9% of the zeros of the Riemann zeta function are distinct and more than 67.35% are simple and on the critical line*, arXiv:2610.08965
- OpenAI, *The Quasi-Riemann Hypothesis: A Zero-Free Half-Plane Re(s) > 7/8*, dated September 30, 2026, released October 6, 2026 — github.com/openai/math; and the 11/12 manuscript dated October 5, 2026
- Quanta Magazine, *AI Proved the Quasi-Riemann Hypothesis. What Happens Now?*, October 19, 2026 (Radziwiłł, Dunn, Lichtman, Sawin, Bloom; Sarnak course)
- B. Liu, *Improved zero-free half-planes for the quasi-Riemann hypothesis*, arXiv:2610.12234 (with Lean)
- *Zero-free half-planes for Hecke L-functions over number fields and Quasi-Riemann Hypothesis*, arXiv:2610.26835
- D. Cureton, J. Thorner (investigators), *A quasi-Riemann hypothesis for Dedekind zeta functions*, Axiom Math report, 2026 (with Lean)
- OpenAI, *Finite Time Blowup for Navier–Stokes* (166 pp.) and Lean project, September 8, 2026; T. Buckmaster statement, September 8, 2026; Buckmaster–Alpöge preprints on IPM, Boussinesq and 3D Euler blowup with Lean, September 7–8, 2026

### The spectral program

- A. Connes, *The Riemann Hypothesis: Past, Present and a Letter Through Time*, arXiv:2602.04022 (February 3, 2026)
- A. Connes, C. Consani, H. Moscovici, *Zeta Spectral Triples*, arXiv:2511.22755; EMS Series of Lectures in Mathematics (2026)
- A. Connes, W. D. van Suijlekom, *Quadratic forms, real zeros and echoes of the spectral action*, arXiv:2511.23257
- A. Connes, C. Consani, *Spectral triples and ζ-cycles*, Enseign. Math. (2023), arXiv:2106.01715
- A. Connes, C. Consani, *Weil positivity and trace formula, the archimedean place*, Selecta Math. (2021), arXiv:2006.13771
- A. Connes, H. Moscovici, *Zeta zeros and prolate wave operators*, arXiv:2310.18423
- *High-Precision Approximation of Riemann Zeros via the Truncated Weil Form*, arXiv:2605.20224
- *A finite Guinand–Weil dictionary and archimedean tail order for the truncated Weil quadratic form*, arXiv:2607.02828
- *The uncertainty operator, the Weil ground state and the zeros of zeta: a numerical study and conditional positivity of the Weil quadratic form*, arXiv:2611.13129

### de Bruijn–Newman

- B. Rodgers, T. Tao, *The de Bruijn–Newman constant is non-negative*, Forum Math. Pi (2020)
- D. H. J. Polymath, *Effective approximation of heat flow evolution of the Riemann ξ function, and a new upper bound for the de Bruijn–Newman constant*, Res. Math. Sci. 6 (2019), arXiv:1904.12438
- M. Planat, *Collective contraction in the de Bruijn–Newman heat flow*, arXiv:2609.37164
- *A conditional bound Λ ≤ 0.13963 for the de Bruijn–Newman constant*, arXiv:2610.12803
- *A certified classical-strip comparison for the de Bruijn–Newman constant*, arXiv:2610.18214
- *On the Pólya Frequency Order of the de Bruijn–Newman Kernel*, arXiv:2602.20313

### Physical routes

- P. Betzios, N. Gaddam, O. Papadoulaki, *Black holes, quantum chaos, and the Riemann hypothesis*, SciPost Phys. Core 4, 032 (2021), arXiv:2004.09523
- S. Wei, Y. Zhai, Q. Lu, W. Yang, P. Gao, C. Wei, J. Song, F. Nori, T. Xin, G.-L. Long, *The Riemann Hypothesis Emerges in Dynamical Quantum Phase Transitions*, arXiv:2511.11199; Nature Communications (2026)
- M. V. Berry, J. P. Keating, *H = xp and the Riemann zeros* (1999); *The Riemann zeros and eigenvalue asymptotics*, SIAM Review 41 (1999)
- C. M. Bender, D. C. Brody, M. P. Müller, *Hamiltonian for the zeros of the Riemann zeta function*, Phys. Rev. Lett. 118 (2017)
- H. L. Montgomery, *The pair correlation of zeros of the zeta function*, Proc. Sympos. Pure Math. 24 (1973)
- P. Saad, S. H. Shenker, D. Stanford, *JT gravity as a matrix integral*, arXiv:1903.11115
- D. N. Page, *Average entropy of a subsystem*, Phys. Rev. Lett. 71 (1993); *Information in black hole radiation*, Phys. Rev. Lett. 71 (1993)
- E. Berti, V. Cardoso, A. O. Starinets, *Quasinormal modes of black holes and black branes*, Class. Quantum Grav. 26 (2009) (QNM tables referenced in §11.2.3)

### Classical inputs named in Strategy I

- S. A. Stepanov, *On the number of points of a hyperelliptic curve over a finite prime field* (1969)
- J.-B. Bost, *Périodes et isogénies des variétés abéliennes sur les corps de nombres* (slope inequality), Séminaire Bourbaki 795 (1996)
- S. A. C. Baluyot, D. A. Goldston, A. I. Suriajaya, C. L. Turnage-Butterbaugh, *An unconditional Montgomery theorem for pair correlation of zeros of the Riemann zeta-function*, Acta Arith. 214 (2024)
- E. Bombieri, *Remarks on Weil's quadratic functional in the theory of prime numbers* (2000)

### ERI Labs corpus (github.com/ericrenone)

- *The-Riemann-Hypothesis-and-the-ERI-Labs-Prediction-Record* — November 24, 2026
- *RIEMANN-PHYSICAL-PROOF-STRATEGY* — June 11, 2026
- *The-Spectral-Geometry-of-Unitary-Evolution* — August 2026
- *Riemann-and-the-Information-Transition-A-Universal-Law-of-Phase-Boundaries-in-Science* — August 2026
- *The-Mathematical-Discovery-Threshold-Register-Crossing-and-Bifurcation-in-AI-Assisted-Proof* — August 11, 2026
- *Mathematical-Structures-Reorganize-Entire-Systems* — August 12, 2026
- *Emergence-of-Mathematics* — August 18, 2026
- *The-Bifurcation-of-Mathematical-Practice* — August 23, 2026

---

*Document status: current to November 24, 2026. Next revision on the first human-readable account of the Alpöge–Claude proof accepted by analytic number theorists, on a Sutherland ledger entry for Hecke or Dedekind L-functions, on a revised Masullo draft, or on a Clay Institute statement, whichever comes first. Section 11.2 will be revised when ERI Labs converts one step of the physical roadmap into a precise statement; the rest of this document does not depend on that happening.*
