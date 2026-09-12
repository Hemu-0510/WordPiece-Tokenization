# WordPiece Tokenization From Scratch

## Overview

This project implements the WordPiece subword tokenization algorithm from scratch using Python in JupyterLab.

WordPiece is a subword tokenization algorithm used by BERT-family models. It differs from BPE because it selects the pair with the highest WordPiece score instead of simply selecting the most frequent pair.

## Objectives

* Understand the basic concept of WordPiece tokenization.
* Create an initial character-level vocabulary.
* Calculate token frequencies and pair frequencies.
* Calculate WordPiece scores.
* Find the highest-scoring pair.
* Merge tokens based on the highest score.
* Tokenize a new word using the learned vocabulary.
* Convert tokens into token IDs.
* Handle unknown words using `[UNK]`.

## Technologies Used

* Python
* JupyterLab
* Collections library
* Counter

## Dataset

A small sample dataset is used for demonstrating WordPiece tokenization.

```text
hug  -> 2
hugs -> 1
pug  -> 1
```

The numbers represent the frequency of each word.

## Initial Tokenization

The words are initially divided into individual characters.

```text
hug  -> h ##u ##g
hugs -> h ##u ##g ##s
pug  -> p ##u ##g
```

The `##` symbol indicates that the token occurs inside a word.

## WordPiece Score

WordPiece calculates a score for each adjacent token pair.

The score is calculated using:

```text
Score = Pair Frequency / (First Token Frequency × Second Token Frequency)
```

The pair with the highest score is selected for merging.

## Token Merging

After calculating the scores, the highest-scoring pair is selected.

For example:

```text
##g + ##s
```

is merged into:

```text
##gs
```

The process can be repeated until the desired vocabulary size is reached.

## Tokenization

After training, the learned vocabulary is used to tokenize a new word.

For example:

```text
hugs
```

is tokenized as:

```text
["hug", "##s"]
```

WordPiece searches for the longest subword available in the vocabulary.

## Token to ID Conversion

Each vocabulary token is assigned a numerical ID.

Example:

```text
hug  -> 7
##s  -> 5
```

Therefore:

```text
hugs
    ↓
["hug", "##s"]
    ↓
[7, 5]
```

## Unknown Token Handling

If WordPiece cannot completely tokenize a word using the available vocabulary, it returns `[UNK]`.

Example:

```text
bum
    ↓
["[UNK]"]
```

## Project Workflow

```text
Training Words
      ↓
Initial Character Splitting
      ↓
Token Frequency Calculation
      ↓
Pair Frequency Calculation
      ↓
WordPiece Score Calculation
      ↓
Find Highest-Scoring Pair
      ↓
Merge Pair
      ↓
Update Vocabulary
      ↓
Tokenize New Word
      ↓
Convert Tokens to IDs
      ↓
Handle [UNK]
```


## Output Screenshot

<img width="697" height="874" alt="image" src="https://github.com/user-attachments/assets/380b55d3-b89f-4dbc-994e-2c313f4db037" />

```

## Conclusion

This project demonstrates the complete basic workflow of WordPiece tokenization from scratch. It shows how tokens are created, frequencies are calculated, WordPiece scores are used to select token pairs, and new words are tokenized into subwords and converted into token IDs.
