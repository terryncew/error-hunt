# Evidence example — worked finding (FROZEN, published at launch)

Preflight evidence from internally operated agents
(ERROR-HUNT-PREFLIGHT-001, Flag 0, STATE 2, survived attack review).
Not independent external review. Shown so participants can see exactly
what a complete submission looks like.

## Finding:

1. **Paper identifier:** PMC7781377 (PLOS ONE, 2021). Preflight
   corpus paper — sacrificial, permanently excluded from the
   challenge corpus.

2. **Exact source location (section + quote):** Results, Table 1,
   "Ownership" rows. Verbatim from the extracted text:
   `Kennel 12128 883 7.3 (6.8-7.8) --`
   `Owned 658 489 74.3 (70.8-77.6) 4.4 (3.6-5.3) ***`
   Reading: Kennel — 883 positive, 11,245 negative of 12,128
   (7.3%); Owned — 489 positive, 169 negative of 658 (74.3%).

3. **Quoted/reported numerical inputs:** univariable odds ratio,
   Owned vs Kennel: 4.4, 95% CI (3.6–5.3).

4. **Claimed relationship:** Methods: "odds ratios (OR) and the 95%
   confidence interval (CI) were estimated by univariable logistic
   regressions." For a binary predictor, the univariable OR equals
   the crude 2×2 odds ratio from the table counts.

5. **Deterministic recomputation (formula + result):**
   a = 489 (Owned positive), b = 169 (Owned negative),
   c = 883 (Kennel positive), d = 11245 (Kennel negative).
   OR* = (a·d)/(b·c) = (489 × 11245)/(169 × 883)
       = 5498805/149227 = **36.85**.
   Cross-check: the flipped-counts OR = (169 × 11245)/(489 × 883)
   = 4.4007 → 4.40; SE(ln OR) = 0.09583;
   95% CI = (3.645, 5.312) → (3.6–5.3) — exactly the reported
   point estimate and CI.

6. **Observed discrepancy (numbers):** |4.4 − 36.85| = 32.45.
   Both the reported OR and its CI match the flipped-counts
   computation to the reported precision.

7. **Proposed check class:** C12 (crude-OR recomputation). Decision
   rule: for a 2×2 table with a reported univariable OR, recompute
   OR = (a·d)/(b·c) from the quoted counts; flag iff
   |reported − recomputed| > 0.05 after rounding. Novel relative to
   B1–B4 (none covers odds ratios).

8. **Baseline-overlap self-assessment:** none. B1–B4 do not cover
   ORs; no preflight baseline flag exists on this paper at this
   location.

9. **Uncertainty/context caveat:** assumes the table counts are the
   analysis counts — supported by the CI reproducing exactly from
   them. This is a claim about numbers in text: not a claim that the
   paper's conclusions are invalid, and not a claim about the authors.

## Why this is the example

Every input is quoted. The recomputation uses only the quoted
values. The discrepancy is a number. The check class has an exact
rule. The caveat says what could make it wrong. That is the whole
game.
