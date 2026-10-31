# Word2Vec vs. GloVe: Comparative Analysis for Document Classification

## Project Overview

This project explores and compares two popular word embedding techniques, Word2Vec (Skip-gram) and GloVe, for representing textual data and improving document classification.

The objective is to investigate how different word representation techniques capture semantic relationships between words and how these representations influence downstream text classification performance.

The project uses a document classification dataset containing 2,127 documents across five categories: Politics, Sports, Technology, Entertainment, and Business.

## Project Objectives

- Implement and compare Word2Vec Skip-gram and GloVe embeddings.
- Explore semantic relationships and word representations.
- Evaluate the quality of learned word embeddings.
- Visualize high-dimensional word vectors using PCA and t-SNE.
- Compare embedding performance through downstream document classification.
- Analyze the strengths and limitations of each approach.

## Dataset

The dataset contains 2,127 text documents distributed across five categories:

- Politics
- Sports
- Technology
- Entertainment
- Business

Each document is associated with a corresponding category label.

## Methodology

### 1. Text Preprocessing

The text preprocessing pipeline includes:

- Converting text to lowercase.
- Removing punctuation and special characters.
- Removing stopwords.
- Tokenization.
- Text normalization and lemmatization.
- Handling missing values and duplicate documents.

### 2. Word Embedding Techniques

**Word2Vec (Skip-gram)**

Learns word representations by predicting surrounding context words from a target word.

**GloVe (Global Vectors for Word Representation)**

Learns word representations by leveraging global word co-occurrence statistics.

Both techniques are investigated to understand their ability to capture semantic information.

### 3. Embedding Visualization

Dimensionality reduction techniques are used to visualize word embeddings in two-dimensional space:

- PCA (Principal Component Analysis)
- t-SNE (t-Distributed Stochastic Neighbor Embedding)

These visualizations help explore semantic similarities and differences between word representations.

### 4. Model Evaluation

The embedding techniques are evaluated through:

- Semantic Similarity Analysis.
- Topic Coherence.
- Downstream Document Classification.
- Comparative Performance Analysis.

## Technologies & Tools

- Python
- Google Colab
- Pandas & NumPy
- NLTK
- Gensim
- Scikit-learn
- Matplotlib
- Seaborn

## Repository Structure

```text
Word2Vec-GloVe-NLP-Comparison/
│
├── README.md
│
└── Word2Vec_Skip_gram_and_GloVe_using_a_document_classification.ipynb
```

## How to Run

1. Clone or download this repository.
2. Open the Jupyter Notebook using Google Colab or Jupyter Notebook.
3. Install the required dependencies if they are not already available.
4. Run the notebook cells sequentially.
5. Review the preprocessing steps, embedding visualizations, and evaluation results.

## Key Learning Outcomes

This project provides practical experience in Natural Language Processing, word embedding techniques, semantic representation, dimensionality reduction, and machine learning evaluation.

It also demonstrates how different text representation approaches can influence the performance of downstream document classification tasks.

## Author

**Mohammed Elzmrany**

Machine Learning & AI Developer

GitHub: [Add your GitHub Profile URL]

