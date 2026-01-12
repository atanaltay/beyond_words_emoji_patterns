## Beyond Words: Emoji Patterns in Cross-Cultural Branding

## Overview

This repository contains the preprocessing and analysis code used to study **emoji usage and emotional signaling in branding-related communication on Platform X (formerly Twitter)** across **English and Turkish**.

The analyses are based on a large-scale dataset consisting of posts and consumer replies from a curated selection of **Fortune 500 companies** that actively maintained Platform X accounts in both languages. The sample includes **33 multinational brands** spanning multiple industries, including fast-moving consumer goods (FMCG), fast food, technology, automotive, apparel, retail, finance, and logistics.

All Platform X messages posted by these brands, together with corresponding consumer responses, were collected over a **five-year period (June 2016 – June 2021)**. The dataset captures both **brand-initiated communication** and **public engagement**, enabling large-scale analysis of **emoji usage patterns**, **emotional framing**, and **audience response dynamics** across languages.

Derived data products (emoji frequency matrices, seed-word frequency matrices, metadata, and row-to-tweet mappings) are archived on Zenodo and are required to reproduce the analyses in this repository:

- **Zenodo (derived dataset):** https://zenodo.org/records/18093119

---

## Repository Structure

The workflow follows two main stages:

1. **Preprocessing of raw data** (build counts, sparse matrices, seed-word lists, co-frequency tables)
2. **Analysis notebooks** (descriptive analyses and two study-specific analyses reported in the paper)

---

## 01_preprocess/ — Preprocessing of Raw Data

Preprocessing of raw text data for extracting counts of emojis, seed words, and co-frequency matrices of emotional seed words and emojis.

### Notebooks

#### 01_count_emoticons.ipynb
- **Uses:** raw data
- **Creates:**
  - `data/emoticon_analysis/tr_all_emoticon_counts.csv`
  - `data/emoticon_analysis/en_all_emoticon_counts.csv`

#### 02_analyze_en.ipynb and 03_analyze_tr.ipynb
- **Uses:** raw textual data  
- **Uses auxiliary file:**
  - `data/emoticon_analysis/emojis.csv`
- **Creates:**
  - `data/emoticon_analysis/tr_emoticon_groups_and_counts.csv`
  - `data/emoticon_analysis/en_emoticon_groups_and_counts.csv`
  - `data/count_matrices/tr/csc_count.npz`
  - `data/count_matrices/tr/feature_names.npy`
  - `data/count_matrices/en/csc_count.npz`
  - `data/count_matrices/en/feature_names.npy`

#### 04_generate_seeds.ipynb
- **Uses:** emotion lexicons
- **Creates:** seed lists of **top 90 scored words for each emotion** (per language)

#### 05_emoji_emotion_cofreq.ipynb
- **Uses:** groups-and-counts outputs, raw data, seeds
- **Creates:**
  - `data/cofrequency/en/cofreq_en.csv`
  - `data/cofrequency/en/relevance_en.csv`
  - `data/cofrequency/tr/cofreq_tr.csv`
  - `data/cofrequency/tr/relevance_tr.csv`

---

## 02_analysis/ — Descriptive Analysis of Emoji Use Across Languages

Python notebooks related to analyses and results in the paper.  
All notebooks use preprocessed outputs created in `01_preprocess/` as input.

### Notebooks

#### 01_prevalence.ipynb
- Prevalence of emojis across languages
- Comparison of emoji frequencies using **zero-inflated models**

#### 02_diversity.ipynb
- Emoji diversity across languages
- Type–token ratio (TTR) and cross-language comparisons

#### 03_permutationtest_diversity.ipynb
- Permutation simulation tests on TTR
- Tests whether differences are statistically significant

---

## study1/ — Study 1: Similarity of Preferred Emojis Across Languages

Notebooks for analysis and results of Study 1.

### Notebooks

#### 01_similarity_preferred_emojis.ipynb
- Similarity of preferred emojis across languages

#### 02_permutationtest_Jdistance.ipynb
- Popularity phases and **Jaccard similarity** analysis (with permutation testing)

---

## study2/ — Study 2: Semantic Emotional Representation of Emojis

Notebooks for analysis of emotional differences in the semantic usage of emojis across languages.

### Notebooks

#### 01_semantic_emotion.ipynb
- Semantic emotional representation of emojis  
- Co-frequency analysis of emojis and emotional seed words

---

## Reproducibility Notes

- Analyses rely on derived frequency matrices archived on Zenodo: https://zenodo.org/records/18093119
- Raw Platform X texts are not redistributed due to platform policies.
- Emoji–seed co-frequency can be computed using a matrix dot product:

  \[
  C = X_{\text{emoji}}^{\top} X_{\text{seed}}
  \]

---

## Citation

If you use this code or the associated dataset, please cite the Zenodo record:

- https://zenodo.org/records/18093119

(Citation details for the paper will be added upon publication.)

---

## License and Usage

This repository is intended for **academic, non-commercial research use**.  
Users are responsible for complying with Platform X data usage and rehydration policies.
