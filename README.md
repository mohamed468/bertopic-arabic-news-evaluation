# Quantitative Evaluation & Benchmarking for BERTopic Topic Modeling

## Introduction
In this project, I built a topic modeling pipeline on a large Arabic news corpus
(~29K articles) using BERTopic, then added a quantitative evaluation and
benchmarking layer on top of it — moving beyond visual inspection of topics to
measure topic quality systematically using objective metrics and controlled
experimentation.

## What I Learned & Built
By the end of this project, I covered and implemented:

- **Reusable Pipeline Design:** Built a parameterized, reusable BERTopic pipeline
  function to support repeated, controlled experimentation.
- **Quantitative Topic Evaluation:** Implemented topic coherence (c_v), topic
  diversity, and outlier ratio as objective quality signals instead of relying
  on visual inspection alone.
- **Controlled Experimentation (OFAT):** Designed a One-Factor-At-a-Time
  experiment comparing 5 configurations (UMAP/HDBSCAN hyperparameters and
  embedding model choice) to isolate the effect of each factor.
- **Embedding Model Benchmarking:** Found that changing the embedding model had
  a larger effect on coherence than any clustering hyperparameter tested.
- **Critical Result Interpretation:** Manually inspected topics to catch a
  metric-inflation issue caused by Arabic's rich morphology, instead of trusting
  a high coherence score at face value.

## Who Should Explore This
This notebook is aimed at:

- **NLP Practitioners** working with unsupervised topic modeling who want to
  move past "the topics look reasonable" evaluation.
- **Arabic NLP Practitioners** dealing with morphologically rich text and its
  effect on standard NLP metrics.
- **ML Engineers** interested in designing small, defensible experiments
  (OFAT) instead of large, costly grid searches.

## Results

| Configuration | Coherence | Diversity | Topics | Outlier Ratio |
|---|---|---|---|---|
| umap_30 | 0.8778 | 0.9538 | 65 | 22.9% |
| baseline | 0.8649 | 0.9269 | 92 | 33.0% |
| hdbscan_25 | 0.8611 | 0.8713 | 188 | 37.9% |
| umap_10 | 0.8323 | 0.9420 | 85 | 29.6% |
| embedding_distiluse | 0.9321 | 0.9452 | 81 | 34.2% |
<img width="1379" height="990" alt="image" src="https://github.com/user-attachments/assets/cd2d8734-a343-4073-babc-decf5237ae2f" />

No single configuration outperformed all others across every metric — embedding
model choice had the largest effect on coherence, while UMAP tuning had the
largest effect on outlier ratio.

**Author:** Muhammad Abd El-Fattah | [GitHub Profile](https://github.com/mohamed468)
