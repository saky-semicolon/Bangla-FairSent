# Bangla-FairSent

A multi-dialect Bengali sentiment dataset built for studying **dialect- and gender-driven fairness
gaps** in sentiment analysis. 13,610 labeled sentences across five dialect groups (Standard,
Chittagonian, Sylheti, Rangpuri, Mymensingh), each with a sentiment label (Positive/Negative/Neutral)
and a gender-reference label (Male/Female/Neutral), assembled from four contributors' own
collection plus one merged external dataset.

**File in this package**: `bangla-fairsent.csv` — the complete, cleaned, ML-ready dataset.

## Why this dataset exists

Sentiment analysis models for Bengali are trained almost entirely on Standard Bangla / Dhaka-region
text. Bangladesh has several regional dialects (Chittagonian, Sylheti, Rangpuri, Mymensingh, and
others) spoken by tens of millions of people, each with distinct phonology, morphology, and
vocabulary. This dataset exists to make it possible to measure — not assume — whether sentiment
models perform worse on these dialects, and whether they perform worse on text that refers to
women vs. men. A baseline experiment run on this exact data already shows both gaps are real (see
"Known baseline results" below).

## Composition

| Dialect | Rows | % of dataset | Positive | Negative | Neutral |
|---|---|---|---|---|---|
| Chittagonian | 6,571 | 48.3% | 1,001 | 1,497 | 4,073 |
| Standard | 3,375 | 24.8% | 1,570 | 1,051 | 754 |
| Rangpuri | 1,702 | 12.5% | 89 | 408 | 1,205 |
| Sylheti | 1,045 | 7.7% | 168 | 200 | 677 |
| Mymensingh | 496 | 3.6% | 157 | 188 | 151 |
| Other/Unclassified | 421 | 3.1% | 245 | 88 | 88 |
| **Total** | **13,610** | | **3,230** | **3,432** | **6,948** |

`Other/Unclassified` is text whose original dialect label didn't map cleanly onto the five core
groups (e.g. "Noakhailla", "Barishal", "Kolkata" — genuine Bengali variants, just not part of this
project's core comparison set). Kept for completeness; exclude it if you want a strict 5-way
comparison.

**gender_reference**: Neutral 5,534 · Male 1,012 · Female 519 · Unknown 6,538 (all from the merged
external Chittagonian data — see below — which wasn't annotated for gender reference) · Other 7.

**style**: Informal 5,241 · Formal 1,740 · Unknown 6,538 (same external-data caveat) · Other 91.

## Where the data comes from

Two distinct sources, merged:

1. **Original 4-contributor collection** (7,072 rows in this file, identifiable via `source_type` *not* starting with `External:`)
2. **ChattogramSent** (6,538 rows, all Chittagonian)

## Known baseline results (bias-detection sanity check)

A simple TF-IDF (char n-gram) + Logistic Regression classifier trained on this data (75/25
stratified split, political-content rows excluded from training) shows:
- **Overall**: 72.4% accuracy, 0.709 macro-F1.
- **18.3-point dialect accuracy gap**: Rangpuri 83.3% (best) vs. Mymensingh 65.0% (worst);
  Chittagonian 68.1% (n=1,643 test rows — a real, trustworthy number, not noise).
- **6.4-point gender accuracy gap**: Male-referenced text 76.7% vs. Female-referenced 70.3%.

## Suggested uses
- Dialect- and gender-fairness evaluation of Bengali sentiment classifiers (its primary intended use).
- Bengali dialect identification (the `dialect` column, independent of `sentiment`).
- Low-resource/regional Bengali NLP more broadly — with the limitations above disclosed.
slot-filled-template block, removed embedded/duplicate header rows and bare
dictionary/academic-reference entries, deduplicated exact-text repeats, recomputed length fields,
and normalized the dialect/gender/style category vocabularies.
