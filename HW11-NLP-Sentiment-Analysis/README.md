# HW11 — NLP Sentiment Analysis

## Problem Statement
Perform sentiment and emotion analysis on recipe descriptions from a large
food dataset, classifying each description as positive, negative, or neutral
and identifying the dominant emotional tone using lexicon-based NLP methods.

## Data
- **Source:** Course-provided dataset (Original recipes.csv) — food.com recipe
  corpus
- **Samples:** 5,000 descriptions sampled from 231,637 total recipes
  (random_state=42); rows with missing descriptions excluded
- **Text Field:** recipe description (free-form contributor-written text)
- **Missing Values:** 4,979 missing descriptions in full dataset; excluded
  prior to sampling

## Data Mining Operations
- **Sentiment Algorithm:** VADER (Valence Aware Dictionary and sEntiment
  Reasoner) via NLTK — compound score thresholds: >= 0.05 Positive,
  <= -0.05 Negative, otherwise Neutral
- **Emotion Algorithm:** NRC Emotion Lexicon via nrclex — dominant emotion
  selected by highest word-count accumulation across 8 emotion categories
  (joy, anticipation, trust, fear, anger, disgust, sadness, surprise)
- **Libraries:** pandas, numpy, nltk, nrclex, wordcloud, seaborn, matplotlib
- **Preprocessing:** Lowercasing, removal of punctuation and numbers via
  regex; custom stopword list augmented with domain-specific filler words
  to surface meaningful culinary terms in the word cloud
- **Why VADER:** Designed for short, informal text with punctuation and
  capitalization cues; well-suited for enthusiastic recipe descriptions

## Model Outputs
- Sentiment Distribution: Predominantly Positive (~4,000), Neutral (~750),
  Negative (~250)
- Emotion Distribution: Joy (1,533), Anticipation (1,226), None (952),
  Trust (725), Fear (166), Anger (162), Disgust (103), Sadness (89),
  Surprise (44)
- Sentiment bar chart, emotion bar chart, word cloud

## Limitations
- VADER is a general-purpose sentiment lexicon not trained on culinary text;
  food-specific adjectives such as "rich," "sharp," or "bitter" may be scored
  inconsistently with their culinary meaning
- NRC emotion classification assigns the dominant emotion by raw word count,
  which can be skewed by repeated common words rather than the overall
  emotional tone of the description
- Sampling 5,000 of 231,637 recipes introduces sampling variability; results
  may not be representative of the full corpus distribution

## Results
Recipe descriptions are overwhelmingly positive, consistent with the
self-promotional nature of contributor-written culinary content. Joy and
anticipation dominate the emotion distribution, reflecting the enthusiastic
language commonly used in food writing. The word cloud highlights terms such
as "delicious," "love," "flavor," "favorite," "taste," and "easy" as the
primary sentiment drivers across the corpus.
