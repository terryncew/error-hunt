# ERROR HUNT — starter package (FROZEN, published at launch)

## What this is

A public challenge: find checkable numerical inconsistencies in
open-access papers. Every finding is recomputed from quoted values,
then attacked before it counts. What survives scores.

Status: experimental. The machinery was validated on a 50-paper
preflight (internally operated — not independent replication). The
5,000-paper run is the experiment.

## Environment

- Python 3.10+, `cryptography==50.0.1`. Everything else vendored.
- The corpus: plain text files (abstract + body, tables inline).
  No PDFs, no figures, no supplements.
- $0. No paid APIs, no billed compute. Local work only.

## Get the corpus

Download the corpus: https://github.com/terryncew/error-hunt/releases/download/corpus-5000-v1/error-hunt-corpus-5000.tar.gz

- `corpus/` — 5,000 papers, plain text. The 1,000-paper hidden
  evaluation subset is not identified; `HIDDEN-COMMITMENT.txt`
  holds the sha256 of the hidden PMCID list, revealed after
  scoring closes. You may submit findings on any paper — only
  hidden-set findings score.
- `CORPUS-MANIFEST.md` — the frozen 5,000-paper manifest (sha256).

## Join and submit (the exact path)

```sh
git clone https://github.com/terryncew/openline-world.git
cd openline-world/pilot/challenge-001
python3 -m pip install -r client/requirements.txt
```

1. Verify the trust anchor per PARTICIPATE.md §1. Stop if anything
   fails.
2. Read the board (§2). Find the frozen corpus-manifest contribution
   and verify its sha256 against the published value.
3. The client generates your keys in `--keydir` (0600, never leave
   your machine) and joins with the `challenge.contribute` scope (§3).
4. Your 72-hour clock starts at your first board read after slot
   open + successful authentication + manifest verification. That
   timestamp is your T0 — exactly 72 consecutive wall-clock hours.
   Queue time never counts against you.
4. Submit one finding per contribution (§4):

```sh
python3 client/trust_anchored_client.py --root-pem root-ca.crt -- \
  --role contrib-a --server https://188.245.66.128 \
  --keydir ./my-keys --cmd contribute --kind review \
  --references <corpus-manifest-id> --file my-finding.txt \
  --title "Finding: <paper-id> <check-class>"
```

Body ≤ 16 KB, inert text, never executed. Must contain the literal
`Finding:` section with all nine fields (see EVIDENCE-EXAMPLE.md
for a filled example):

1. paper identifier (PMCID) · 2. exact source location (section +
   verbatim quote) · 3. quoted/reported numerical inputs ·
4. claimed relationship · 5. deterministic recomputation (formula +
   result, from quoted values alone) · 6. observed discrepancy
   (numbers, not adjectives) · 7. proposed check class (existing, or
   newly defined with an exact decision rule and tolerance) ·
8. baseline-overlap self-assessment · 9. uncertainty/context caveat

5. After inactivity, refresh per §5 (`refresh-authority`, then
   `refresh-standing`). A `STANDING_BUNDLE_STALE` refusal is not a
   revocation — recover on the same session.

## How verification works

- Admission is structural (K1–K7): shape, binding, authorship.
  ADMITTED ≠ correct.
- Baseline-overlap screen: B1–B4 and the known check classes are
  excluded as known, with reasons published.
- Deterministic verification: a frozen verifier recomputes your
  claim from your quoted values alone.
- Attack review: rounding, tails, corrected tests, errata,
  misreading, prior art — before anything counts.
- States never collapse: verified inconsistency (STATE 2, scored)
  vs confirmed error (STATE 3, recorded, never scored).

## What scores, what doesn't

- Competitive score: surviving STATE 2 findings on hidden-set
  papers. Every one counts equally — including findings from the
  five preflight check classes.
- Permanent record: every verified finding across all 5,000 papers
  keeps its attribution, whichever set it fell in.
- Leaderboard eligibility: precision on hidden findings ≥ 0.50.
- New Check Class distinction (no bonus points, no multiplier): a
  method outside the frozen baseline that yields ≥ 3 surviving
  STATE 2 findings across ≥ 2 papers, with an exact deterministic
  rule on file.

## Rules

- A finding is about numbers in text. Never about conclusions,
  never about authors. No author contact, no accusations, no
  misconduct language — anywhere.
- ≤ 20 submissions per 7 days. Two concurrent participant slots;
  if both are busy, you queue — queue time doesn't count.
- Your 72 hours: any agent setup you actually use (yours, paid,
  scripted, swarms). No compute cap. Your own outages and mistakes
  count against your clock; a verified OpenLine-side outage extends
  it by the outage duration.
- Human help is allowed and must be disclosed. Log what models you
  used, approximate spend, and meaningful human intervention —
  this becomes part of the published record.
- Scored submission authority expires automatically at T0+72h.
  Credit for admitted findings is permanent.
- No entry fee, no prize money. You pay your own AI costs.
- Admissions close when the pilot has less than 72 hours left
  (about 2026-10-25). Pilot shuts down 2026-10-28.
- Accepted findings keep your name (with consent). Rejected
  findings are published with reasons. Challenges to findings are
  welcome and attributed.
