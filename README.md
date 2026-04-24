# SAG-Fusion: Statistically Aligned Gated Fusion for Subject-Level Depression Detection

> Paper: *SAG-Fusion: Statistically Aligned Gated Fusion for Subject-Level Depression Detection* [link to be added]

## Overview

SAG-Fusion is a lightweight multimodal fusion framework for subject-level depression detection.
It maps speech and text into a shared Shared Temporal Grid via statistical pooling, then performs
gated fusion and cross-modal attention to capture complementary information across modalities.
Experiments on EATD-Corpus demonstrate competitive performance without relying on large pretrained models.

## File

| File | Description |
|---|---|
| `sag_fusion_main.ipynb` | Full pipeline: data loading, text encoding, audio encoding, model training, val evaluation, and checkpoint saving |

Run all cells in order. Modify `DATA_ROOT` and `LEXICON_ROOT` at the top of **Cell 1** to your local paths before running.

## Dataset: EATD-Corpus

The EATD-Corpus consists of audio and text files from 162 volunteers who received counseling.

**Download:** https://1drv.ms/u/s!AsGVGqImbOwYhHUHcodFC3xmKZKK?e=mCT5oN  

Each volunteer's folder contains:

```
{positive/negative/neutral}.wav        # Raw audio
{positive/negative/neutral}_out.wav    # Preprocessed audio (denoising + de-muting)
{positive/negative/neutral}.txt        # Transcription
new_label.txt                          # Scaled SDS score (raw score × 1.25)
```

## Lexicons

Text encoding relies on the following Chinese sentiment lexicons.
Download them separately and place under a `lexicons/` folder.

- NTUSD (National Taiwan University Sentiment Dictionary): one positive and one negative wordlist
- BosonNLP Sentiment Lexicon
- Degree adverb lexicon
- Negation word list
- HIT Stop Words List


## Data Split

We apply a subject-level three-way split. The model is selected based on positive-class F1 on the validation set.

> Note: Due to the small dataset size, results may vary slightly across runs
> due to random initialization (variation within ±0.05 is expected).


## Reproducibility

Run all cells in `sag_fusion_main.ipynb` in order to fully reproduce the training and evaluation pipeline.
