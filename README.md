# Bangla-FairSent
A Bias-Aware Bengali Sentiment Analysis Dataset Annotated across Gender, Dialect, and Writing Style.

## 🔍 Overview
Bangla-FairSent is the first multidimensional fairness-focused Bengali sentiment dataset 
designed to measure bias across:
- Gender references
- Major Bengali dialects (Standard, Sylheti, Chittagonian, Kolkata)
- Writing styles (formal vs informal)

## 📁 Dataset Structure
- Raw data
- Annotated CSV files
- Annotation guidelines
- Lexicons (gender, dialect)

## 🧪 Experiments
- Logistic Regression baseline
- BanglaBERT / mBERT / XLM-R fine-tuning
- Counterfactual Data Augmentation
- Fairness metrics evaluation

## 📊 Bias Metrics
- Accuracy Gap
- FNR Gap
- Precision Gap
Bangla-FairSent/
│
├── README.md
├── DATACARD.md
├── CITATION.cff
├── LICENSE
├── CONTRIBUTING.md
├── CHANGELOG.md
│
├── dataset/
│   ├── raw/
│   │   ├── youtube_raw.csv
│   │   ├── twitter_raw.csv
│   │   ├── facebook_raw.csv
│   │   └── manual_sentences.csv
│   │
│   ├── cleaned/
│   │   ├── normalized.csv
│   │   ├── deduped.csv
│   │   └── filtered.csv
│   │
│   ├── annotated/
│   │   ├── annotated_sentiment.csv
│   │   ├── annotated_gender.csv
│   │   ├── annotated_dialect.csv
│   │   ├── annotated_style.csv
│   │   └── merged_annotations.csv
│   │
│   ├── splits/
│   │   ├── train.csv
│   │   ├── val.csv
│   │   └── test.csv
│   │
│   └── metadata/
│       ├── dataset_description.json
│       ├── annotation_guidelines.pdf
│       ├── variables_description.csv
│       └── stats.json
│
├── scripts/
│   ├── collect/
│   │   ├── youtube_scraper.py
│   │   ├── twitter_scraper.py
│   │   ├── facebook_scraper.py
│   │   └── manual_sentences_creator.py
│   │
│   ├── clean/
│   │   ├── normalize_unicode.py
│   │   ├── remove_noise.py
│   │   ├── deduplicate.py
│   │   └── filter_short_texts.py
│   │
│   ├── annotate/
│   │   ├── auto_label_sentiment.py
│   │   ├── auto_label_gender.py
│   │   ├── auto_label_dialect.py
│   │   ├── auto_label_style.py
│   │   ├── merge_annotations.py
│   │   └── quality_check.py
│   │
│   ├── finalize/
│   │   ├── merge_all_data.py
│   │   ├── create_final_split.py
│   │   ├── validate_schema.py
│   │   └── generate_stats.py
│   │
│   └── utils/
│       ├── text_normalizer.py
│       ├── language_detector.py
│       ├── helpers.py
│       └── constants.py
│
├── models/
│   ├── baseline_logreg.pkl
│   ├── banglabert_finetuned/
│   ├── mbert_finetuned/
│   └── xlmr_finetuned/
│
├── results/
│   ├── metrics_before.json
│   ├── metrics_after.json
│   ├── bias_charts/
│   │   ├── gender_gap.png
│   │   ├── dialect_gap.png
│   │   ├── style_gap.png
│   │   └── fnr_gap.png
│
└── docs/
    ├── paper_draft.md
    ├── methodology.md
    ├── figures/
    └── tables/



## 📜 License
MIT or CC BY 4.0 (for dataset)

## 📣 Citation
Please cite using the provided CITATION.cff
