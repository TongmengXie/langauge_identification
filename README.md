Multilingual Language Identification (N-gram Fingerprints)

This project implements a lightweight language identification (LangID) system using a simple, ungrammed statistical framework based on character n-gram frequency fingerprints.
The approach follows the classic method of Cavnar & Trenkle (1994) but is implemented entirely from scratch, without neural models or pretrained LangID tools.

# Languages Included

Languages were automatically extracted from the Tatoeba multilingual corpus.
The final set includes:

English (en)

Esperanto (eo)

Spanish (es)

French (fr)

Galician (gl)

Marathi (mr) — Devanagari script

Dutch (nl)

Portuguese (pt)

Russian (ru) — Cyrillic script

This mix provides both related and distant languages across different alphabets.

# Dataset Size Per Language

For each language:

200 total sentences collected from Tatoeba

170 sentences used for training

30 sentences used for evaluation

This setup ensures a clear train/test split (no data leakage) and keeps the experiment lightweight.

# Method Summary (Ungrammed Statistical Framework)

The model uses only character statistics — no grammar, morphology, or syntax.
The steps are:

Extract character n-grams (default: 3-grams) from each sentence.

Build a normalized frequency distribution (fingerprint) for each language.

For a test sentence, compute its fingerprint.

Measure similarity to each language using cosine similarity.

Predict the language with the highest similarity score.

Fully transparent and interpretable.

# Evaluation & Visuals

The notebook outputs:

A confusion matrix showing how accurately each language is identified.

A cosine-similarity matrix showing how similar the language fingerprints are.

These reveal natural clusters (e.g., Spanish/Galician, English/Dutch) and strong separation between languages with different writing systems.

- Interpretation of similarity matrix: Spanish, Galician, Portuguese, and French form a loose Romance cluster with noticeably higher mutual similarity than with other languages. English and Dutch form a smaller Germanic cluster, while Esperanto sits in between major groups with moderate similarity to most Latin-script languages. Marathi and Russian stand alone as isolated singletons because their scripts share no n-gram structure with the Latin-based languages.

- Interpretation of confusiom matrix: Galician has more false negatives: the classifier frequently thinks a Galician sentence is Spanish or Portuguese because the shared letter patterns dominate the fingerprint.