

## Language_Model_Predict_Next_Word: 

# Project Overview

This project implements a statistical language model that predicts the next word given the previous two words, using a Trigram-based probabilistic approach.
The model is trained on the Reuters corpus from NLTK and estimates conditional probabilities using maximum likelihood estimation (MLE).

The goal of this project is to demonstrate how classic n-gram language models work internally, including data preprocessing, probability estimation, and inference.

# Problem Statement

Natural language prediction is a core task in NLP, commonly used in:

    - Text auto-completion

    - Search query suggestions

    - Assistive typing systems

    - Given a sequence of words, the challenge is to estimate the probability distribution of the next word based on observed language patterns.

    - This project focuses on the following problem:

    - Given two consecutive words (w₁, w₂), predict the most likely next word (w₃).

# Solution Approach

I model this problem using a Trigram Language Model, based on the Markov assumption:

    P(w3​∣w1​,w2​)

Why Trigrams?

    Capture more context than unigrams or bigrams

    Still computationally simple and interpretable

    Good baseline before neural language models

# Dataset

    Source: Reuters Corpus (NLTK)

    Content: News articles segmented into sentences

    Preprocessing:

    Sentence tokenization using NLTK

    Padding applied to handle sentence boundaries

    Trigram extraction from tokenized sentences

# Model Construction
Step 1: Trigram Counting

    For each sentence in the dataset:

    Extract trigrams (w1, w2, w3)

    Count occurrences of each (w1, w2) → w3 combination

    Internally, the model is stored as a nested dictionary:

    model[(w1, w2)][w3] = count


    This structure allows efficient lookup of possible next words for a given word pair.

Step 2: Probability Estimation

    Raw counts are converted into probabilities using Maximum Likelihood Estimation (MLE):

        P(w3​∣w1​,w2​)=∑w​count(w1​,w2​,w)count(w1​,w2​,w3​)​

    This ensures that the probabilities of all possible next words sum to 1 for a given context.

# Example Usage

Once trained, the model can be queried with a word pair to retrieve a probability distribution over possible next words:

    model[('today', 'the')]


This returns all candidate third words along with their estimated probabilities.

# Project Structure
    Language_Model_Predict_Next_Word/
    │
    ├── language_model.py    
    ├── README.md            
    └── requirements.txt      

# Technologies Used

    Python

    NLTK

    Reuters Corpus

    Trigram Language Modeling

    Probabilistic Modeling (MLE)

# Key Takeaways

This project demonstrates:

    How statistical language models work internally

    How probabilities are derived from raw text data

    A clear baseline for understanding more advanced NLP models

    It is intended as an educational and foundational NLP project, not a production-ready language model.

