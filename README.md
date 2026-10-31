# Word2Vec Skip-gram vs. GloVe
### A Comparative Study of Word Embeddings for Document Classification

[![Open in Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Muhammadelzmrany/Word2Vec-GloVe-NLP-Comparison-4/blob/main/Word2Vec_Skip_gram_and_GloVe_using_a_document_classification.ipynb)
[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Notebook-Jupyter-orange?logo=jupyter)](https://jupyter.org/)

## Overview

This project compares two word embedding approaches—**Word2Vec (Skip-gram)** and **GloVe**—on a five-class document classification task.

The notebook covers the complete workflow: text cleaning, embedding training and loading, vocabulary coverage, semantic similarity analysis, dimensionality-reduction visualizations, document-vector generation, and classification evaluation.

The goal is not to declare one embedding method universally better, but to understand how the two approaches behave under the same downstream classification setup.

## Key Results

Both models achieved **96.93% test accuracy**. Word2Vec produced a slightly higher Macro-F1 score, while GloVe provided much stronger vocabulary coverage and a higher average within-topic similarity gap.

| Evaluation | Word2Vec Skip-gram | GloVe |
|---|---:|---:|
| Test accuracy | **96.93%** | **96.93%** |
| Macro-F1 | **96.97%** | 96.83% |
| Test vocabulary coverage | 71.69% | **97.86%** |
| Mean within-topic similarity gap* | 0.224 | **0.306** |
| Variance retained by 2 PCA components | 25.19% | **35.17%** |

\* The similarity gap is calculated as average within-topic cosine similarity minus average between-topic cosine similarity. It is used in this project as a comparative topic-coherence indicator, not as a universal or standalone measure of embedding quality.

### Main Observations

- Both embeddings performed equally in test accuracy.
- Word2Vec achieved a marginally higher Macro-F1 score.
- GloVe covered a much larger proportion of the test vocabulary, reducing out-of-vocabulary words.
- GloVe showed a higher average within-topic similarity gap in this experiment.
- The results depend on the dataset, preprocessing, embedding source, and evaluation setup; they should not be generalized to every NLP task.

## Dataset

The dataset contains news documents assigned to five topics:

- Politics
- Sport
- Technology
- Entertainment
- Business

After removing missing entries and duplicate documents, the dataset contained **2,127 documents**. A further **10 duplicate documents** were identified after text normalization, leaving **2,117 documents** for the final experiment.

The data is split into:
- **Training set:** 1,693 documents (80%)
- **Test set:** 424 documents (20%)

The split is stratified to preserve the topic distribution.

> **Dataset note:** The CSV file is not included in this repository. The notebook expects a file named `df_file.csv` with `Text` and `Label` columns.

## Methodology

### 1. Text Preprocessing

The preprocessing pipeline includes:

- Converting text to lowercase.
- Expanding common negations before punctuation removal.
- Keeping English alphabetic tokens.
- Removing English stopwords while preserving `no`, `not`, and `nor`.
- Applying WordNet noun lemmatization.
- Removing empty and duplicate documents after cleaning.

### 2. Word Embeddings

**Word2Vec — Skip-gram**

- Trained on the training documents only.
- Vector size: 100.
- Context window: 5.
- Minimum word count: 2.
- Training epochs: 20.
- Skip-gram mode enabled.

**GloVe — pre-trained**

- Loaded using Gensim's `glove-wiki-gigaword-100` model.
- Vector size: 100.
- Pre-trained on an external corpus rather than the project dataset.

### 3. Embedding Analysis and Visualization

The notebook investigates:

- Vocabulary coverage and out-of-vocabulary words.
- Nearest-neighbor words using cosine similarity.
- Topic-related word relationships.
- PCA visualizations.
- t-SNE visualizations.
- Within-topic and between-topic cosine similarity.

For the PCA and t-SNE plots, the notebook uses a selected set of 25 topic-related words.

### 4. Document Classification

Each document is represented by the **average of its available word vectors** (mean pooling). Words outside the embedding vocabulary are ignored.

A classification pipeline using **StandardScaler and Logistic Regression** is trained separately for each embedding approach.

Evaluation includes:

- Accuracy.
- Macro-F1 score.
- Per-class precision, recall, and F1-score.
- Confusion matrices.

## Technologies

- Python
- Google Colab / Jupyter Notebook
- Pandas and NumPy
- NLTK
- Gensim
- Scikit-learn
- Matplotlib and Seaborn

## Run the Project

1. Open the notebook using the **Open in Google Colab** badge above, or download it and run it in Jupyter.
2. Upload the dataset CSV to the runtime.
3. Make sure the file is available at the path used in the notebook:

   ```python
   DATA_PATH = "/content/df_file.csv"
   ```

   If your file is stored elsewhere, update `DATA_PATH`.
4. Run the notebook cells in order.
5. Allow the notebook to download the required NLTK resources and the pre-trained GloVe model. An internet connection is required for these downloads.

The CSV must contain:
- `Text`: the document text.
- `Label`: the numeric class label, using the mapping defined in the notebook.

## Repository Structure

```text
Word2Vec-GloVe-NLP-Comparison-4/
├── README.md
└── Word2Vec_Skip_gram_and_GloVe_using_a_document_classification.ipynb
```

## Limitations

- The experiment uses one stratified train/test split.
- Word2Vec is trained on this dataset, while GloVe is pre-trained on a larger external corpus. Therefore, the comparison reflects differences in both the embedding method and its training data.
- Mean pooling ignores word order and may weaken the effect of negation.
- Out-of-vocabulary words are ignored when document vectors are created.
- The topic similarity analysis and visualizations use a selected vocabulary.
- t-SNE results can change with parameter settings and should be treated as exploratory.
- PCA explained variance and visual separation do not, by themselves, prove that one embedding is semantically better.

## Conclusion

In this experiment, both approaches achieved the same classification accuracy. Word2Vec had a small advantage in Macro-F1, while GloVe offered broader vocabulary coverage and a stronger average topic-similarity gap.

The findings show why embedding models should be evaluated using multiple perspectives—including downstream performance, vocabulary coverage, and semantic analysis—rather than relying on a single metric.

## Author

**Mohammed Elzmrany**  
Machine Learning & AI Developer

- GitHub: [@Muhammadelzmrany](https://github.com/Muhammadelzmrany)
- Project repository: [Word2Vec-GloVe-NLP-Comparison-4](https://github.com/Muhammadelzmrany/Word2Vec-GloVe-NLP-Comparison-4)
