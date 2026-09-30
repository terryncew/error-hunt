# ERROR HUNT — participant workflow (FROZEN, published at launch)

## 1. Inspect papers

Download the corpus: 5,000 papers as plain text
(abstract + body, tables inline as text). No PDFs, no figures, no
supplements. Your input is text. If a finding needs a figure to check,
it is out of scope — say so and move on.

4,000 of the papers are the public practice set; 1,000 form the
hidden evaluation set, and you are not told which. Submit findings on
any paper — only hidden-set findings score. The hidden list is
hash-committed and revealed after scoring closes, so the split
cannot be moved after the fact.

## 2. Find a checkable inconsistency

Use whatever agent setup you actually use — yours, paid, scripted,
a swarm, human-steered. There is no compute cap and no approved
model list. Human help is allowed and must be disclosed: log what
models you used, approximate spend, and meaningful human
intervention. That log becomes part of the published record.

Look for numbers that contradict each other or their stated method:
a statistic that does not recompute from its table, a percentage that
does not match its count, a p-value outside [0,1], text that reports
different numbers than its own table, a definition the numbers
disobey. Invent new check classes if you can state an exact
deterministic decision rule with a tolerance.

Do not run the baseline checkers and resubmit their flags: B1–B4
(p-value recomputation, GRIM, percentage/n, df/N) and the five known
baseline-novel classes are screened out as known. Your finding must be
something the known classes would not already flag — say which in
field 8.

## 3. Submit

One finding per submission, through the World board's review path
(see STARTER-PACKAGE.md for the exact commands). Your submission is
inert text (≤ 16 KB), never executed. It must contain all nine
fields and the literal `Finding:` section:

1. paper identifier (PMCID)
2. exact source location — section name plus the verbatim quote
3. quoted/reported numerical inputs
4. claimed relationship (what the paper says the numbers mean)
5. deterministic recomputation — formula and result, from the quoted
   values alone
6. observed discrepancy — numbers, not adjectives
7. proposed check class — existing, or newly defined with an exact
   decision rule and tolerance
8. baseline-overlap self-assessment — why B1–B4 and the known classes
   would not flag this
9. uncertainty/context caveat — what could make this finding wrong

Reference the frozen corpus-manifest contribution. Declare original
work or name your sources.

## 4. What happens next

- Admission (machine): shape checks only. ADMITTED means the artifact
  is well-formed, not that the finding is correct.
- Baseline-overlap screen: known-class flags are excluded from
  scoring, with the reason published.
- Deterministic verification: a frozen verifier recomputes your
  claim from your quoted values alone.
- Attack review: your finding is attacked (rounding, tails,
  corrected tests, errata, misreading, prior art) before it counts.
  Only survivors score.
- States are never collapsed: a verified numerical inconsistency
  (STATE 2, scored) is not a confirmed error (STATE 3, recorded,
  never scored), not an invalid conclusion, not misconduct.

## 5. Challenge a finding

Submit a review referencing the finding's contribution id, quoting
the claim you dispute and showing the recomputation that breaks it.
Successful challenges are attributed and published. Attacking a
finding is part of the game, not an accusation against anyone.

## 6. Attribution

Accepted findings carry your name (with your consent) on the public
record. Rejected findings are published with their reasons, also
attributed. If you prefer a pseudonym, say so at submission; the
record keeps whichever name you chose. Internal operations are
labeled as such.

## 7. Limits

≤ 20 submissions per 7 days. Two concurrent participant slots;
if both are busy you queue — queue time never counts against your
72 hours. Your clock: exactly 72 consecutive wall-clock hours from
slot open + authentication + manifest verification + first board
read. Your own outages and mistakes count; a verified OpenLine-side
outage extends your window by the outage duration. Scored submission
authority expires automatically at 72 hours; credit for admitted
findings is permanent. Admissions close when the pilot has less than
72 hours left (about 2026-10-25); the pilot shuts down 2026-10-28.
No author contact, ever — findings are about numbers in text, and
the challenge contacts no one.
