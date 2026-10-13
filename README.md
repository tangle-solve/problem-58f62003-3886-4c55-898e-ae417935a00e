<!-- solve-problem:58f62003-3886-4c55-898e-ae417935a00e -->
# Skolem problem

A [Tangle Solve problem](https://solve.tangle.tools/problems/58f62003-3886-4c55-898e-ae417935a00e).

## What is the problem?

The **Skolem problem** asks: given a linear recurrence sequence (LRS) — a sequence $(u_n)_{n\ge 0}$ of integers (or rationals) satisfying
$$u_{n+d} = a_1 u_{n+d-1} + \cdots + a_d u_n \quad \text{for all } n \ge 0,$$
with fixed integer coefficients $a_i$ and initial values — is it decidable to determine whether $u_n = 0$ for some $n$?

The LRS is "algebraic" in the sense that its characteristic polynomial has algebraic (here, integer/rational) coefficients; equivalently, each term has the form $u_n = \sum_{i=1}^k p_i(n)\alpha_i^n$ where the $\alpha_i$ are algebraic numbers (roots of the characteristic polynomial) and $p_i$ are polynomials with algebraic coefficients.

**Open case:** order/degree $d \ge 5$. The problem is decidable for $d \le 3$ (classical, via Baker's theorem on linear forms in logarithms and, in the degenerate case, geometry-of-numbers arguments). For $d = 4$ a decidability proof was announced by Vereshchagin (1985) and a full proof given recently by Lipton, Luca, Nesterenko, and Skubch (2016), but it has not been fully accepted as published/verified by all experts (verify). For $d \ge 5$ nothing is known — no algorithm, and no proof of undecidability.

Ambiguity note: the problem is over characteristic zero. Over finite fields or in positive characteristic it is trivially decidable (the sequence is eventually periodic).

## Why does it matter?

This is one of the oldest and most notorious open decidability problems in number theory and theoretical computer science, open since the 1930s. It gates a family of equivalent reachability questions: the **Positivity problem** (is $u_n \ge 0$ for all $n$?) and **ultimate positivity** reduce to and are intertwined with Skolem, and decidability of general **linear dynamical system reachability** ($\mathbb{Z}$- or $\mathbb{Q}$-matrices) hinges on it. LRS arise everywhere — combinatorics, generating functions, automata theory, model checking (e.g., weighted counter machines) — so an algorithm (or an undecidability proof) would have immediate consequences for verification and database query evaluation (e.g., provenance semirings).

## What's already known?

- **Decidability for $d \le 3$:** classical, via two cases. *Non-degenerate* (no quotient of distinct characteristic roots is a root of unity): Baker's theorem on linear forms in logarithms gives an effective bound on the index of any zero. *Degenerate:* reduces to finitely many non-degenerate subsequences via geometry of numbers (Schlickewei, Evertse).
- **Order 4:** Vereshchagin (1985) claimed decidability; Lipton–Luca–Nesterenko–Skubch (2016) gave a detailed proof using $S$-unit machinery. Status: believed correct but not universally regarded as fully settled (verify).
- **Subspace/Orbit problems:** the *Skolem Problem for the $k$-generalized setting*, the *Orbit Problem* (Kannan–Lipton, 1986: is $0$ in the orbit of a matrix acting on a vector — decidable), and *point-to-set* reachability (decidable in some formulations) — these are decidable even in high dimension, showing the difficulty is specifically about zero-testing sequences, i.e., linear forms in exponentials.
- **Hardness barriers:** Ouaknine and Worrell showed the Positivity problem at order 5+ (and even 6, depending on variant) is as hard as hard open problems in transcendence theory (Diophantine approximation of algebraic numbers, specifically variants related to the **four exponentials theorem** / Positivstellensatz for linear forms in logarithms of algebraic numbers). A resolution of Skolem would likely require effective results on linear forms in logarithms far beyond current Baker-type bounds.
- **Undecidability attempts** (e.g., encoding two-counter machines via exponential polynomials) have consistently failed because LRS zeros are too "rigid"; no reduction is known.

## What would count as solving it?

- **Positive solution:** an explicit algorithm that, given (rational/integer) LRS data of arbitrary order $d$, decides in finite time whether some $u_n = 0$, together with a termination/proof argument. Ideally with complexity bounds, but mere decidability suffices.
- **Negative solution:** a many-one reduction from a known undecidable problem to zero-detection for integer LRS of some fixed order $d$, with proof that the reduction is correct.
- **Partial progress that counts:** decidability at order 5; a conditional result (e.g., decidability under a stated effective version of the $p$-adic Subspace Theorem); or a proof that Skolem at some order implies a known-hard transcendence statement, thereby sharpening the barrier.

## How to start

1. Read Ouaknine–Worrell's survey *"On the Positivity Problem for Simple Linear Recurrence Sequences"* and the paper *"Positivity Problems for Low-Order Linear Recurrence Sequences"* (SODA 2014) — the cleanest modern account of the low-order techniques and the barrier landscape.
2. Master the low-order proof: Baker's theorem + the non-degenerate/degenerate split, then the Vereshchagin/LLNS order-4 argument. Ask: what specifically breaks at order 5? (Answer sketch: linear forms in *three* logarithms become unavoidable, and current transcendence/Diophantine-approximation tools give ineffective or wildly insufficient bounds.)
3. Consider the natural attack: reduce degenerate to non-degenerate (routine), then for non-degenerate sequences, express $u_n = 0$ as $\sum p_i(n)\alpha_i^n = 0$ and seek effective bounds on the largest zero index using Subspace Theorem-based zero-multiplicity estimates (Amoroso, Evertse, etc.). The obstacle: these bounds are currently non-effective or too weak at high order.
4. Alternative: pursue the hardness side — try to reduce Positivity/Skolem-hard sub-problems to known open transcendence conjectures, mapping exactly what "exponentially good approximation of logs of algebraic numbers" would be needed. This is a legitimate and publishable direction even without full resolution.

## Key references

- R. Lipton, F. Luca, J. Nesterenko, A. Skubch, *On the Skolem Problem for linear recurrence sequences* (2016, arXiv:1508.07602). Gives a full proof of decidability at order 4 using $S$-unit equations and Baker-type bounds. https://arxiv.org/abs/1508.07602
- J. Ouaknine, J. Worrell, *Positivity Problems for Low-Order Linear Recurrence Sequences* (SODA 2014). Decidability of positivity/ultimate positivity for orders up to 5–7, and identifies open transcendence barriers beyond. (verify exact orders per variant)
- R. Kannan, R. Lipton, *Polynomial-time algorithm for the Orbit Problem* (JACM 1986). Decidability of matrix-orbit reachability — the contrasting "easy" relative of Skolem.
- T. Tao blog post, *The Skolem problem and linear recurrences* (2018, terrytao.wordpress.com). An accessible modern overview of why the problem is hard and what transcendence input would be needed.
- H. P. Schlickewei, *The p-adic Thue–Siegel–Roth–Schmidt theorem*, and Evertse's work on $S$-unit equations — the degenerate-case machinery underlying all low-order results.
- Wikipedia, *Skolem problem* — a correct short overview: https://en.wikipedia.org/wiki/Skolem_problem

## Warnings

- **Do not trust "decidability at order 4" uncritically:** the Vereshchagin proof is a 1985 Russian announcement widely cited but hard to verify; the LLNS 2016 proof is detailed but its acceptance is not universal (verify before relying on it).
- The degenerate case (root ratios being roots of unity) is where amateurs slip; it must be handled, not assumed away.
- Beware "algebraic LRS": some literature allows algebraic coefficients and initial terms; the rational case is equally hard and is the standard formulation.
- A bound on the *number* of zeros (the Skolem–Mahler–Lech theorem) is known but **ineffective** — it does not by itself decide existence of a zero. Many false proofs conflate these.
- Undecidability is wide open; no plausible reduction is known, and several natural encodings provably fail.

---
*`ALGO-000221` · unverified*

## Acceptance guidance

- **Positive solution:** an explicit algorithm that, given (rational/integer) LRS data of arbitrary order $d$, decides in finite time whether some $u_n = 0$, together with a termination/proof argument. Ideally with complexity bounds, but mere decidability suffices.
- **Negative solution:** a many-one reduction from a known undecidable problem to zero-detection for integer LRS of some fixed order $d$, with proof that the reduction is correct.
- **Partial progress that counts:** decidability at order 5; a conditional result (e.g., decidability under a stated effective version of the $p$-adic Subspace Theorem); or a proof that Skolem at some order implies a known-hard transcendence statement, thereby sharpening the barrier.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/58f62003-3886-4c55-898e-ae417935a00e?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000221.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000221)
