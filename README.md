# Bias_Analysis_Speech_2_Text
Analysis of bias in speech transcription by speech_recognition for native and non-native speakers
We evaluated our model’s performance on two groups of data (source Mozilla Common Voice Dataset):

Native speakers

Non-native (foreign) speakers

The goal was to assess whether performance is consistent across groups, and to identify potential fairness or bias issues.

📊 Methods

We compared two categories of metrics:

Classification metrics (precision, recall)
→ Do we classify outputs correctly, with few false positives/negatives?

Similarity metrics (Levenshtein distance, ROUGE-2, Jaccard distance, Cosine similarity)
→ How close are model outputs to reference texts, in terms of edits, n-gram overlap, word overlap, and semantic similarity?

We visualized results using kernel density estimation (KDE) plots for each group.

🔎 Findings
1. Precision & Recall

Native speakers: Very high, tightly clustered near 1.0.

Non-native speakers: Still good on average, but more variable, with noticeable tails toward lower values.

Interpretation: The model is more reliable for native data.

2. Similarity Metrics

Levenshtein distance: Natives require fewer edits → closer matches.

ROUGE-2: Natives show sharper peaks near 1.0 → stronger bigram overlap.

Jaccard distance: Natives trend toward smaller distances → better word overlap.

Cosine similarity: Natives are tightly clustered near 1.0 → stronger semantic alignment.

Interpretation: Across string-level and semantic measures, natives are consistently favored.

🧩 Overall Story

The system performs systematically better on native speakers: higher, more consistent accuracy and closer matches to references.

Non-native speakers: Performance is decent but less stable — sometimes close to native-level, sometimes significantly worse.

This indicates a bias and generalization gap: the model is not handling the variability of non-native language as effectively.

✅ Next Steps

Quantify the gap: Use statistical tests (t-tests, KS tests, effect sizes) to measure the significance of differences.

Mitigation strategies:

Data augmentation with non-native samples

Accent or grammar normalization preprocessing

Domain adaptation or fine-tuning

📌 Key takeaway:

The model works reliably for native speakers, but non-native speakers experience reduced reliability and fairness risks.
