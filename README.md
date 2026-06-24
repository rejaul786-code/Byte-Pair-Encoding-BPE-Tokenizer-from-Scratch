# Byte Pair Encoding (BPE) Tokenizer from Scratch in C++

A complete implementation of the Byte Pair Encoding (BPE) tokenization algorithm built from scratch in C++. The project demonstrates how modern language models preprocess text by learning subword vocabularies through iterative merge operations.

## Features

* BPE vocabulary learning from raw text
* Pair-frequency analysis and merge-rule generation
* Subword tokenization
* Token ↔ ID mapping
* Text encoding and decoding
* Unknown word handling through character fallback
* Implemented using STL containers without external NLP libraries

## How It Works

### Training Phase

1. Split words into character-level tokens.
2. Add an end-of-word marker (`</w>`).
3. Count adjacent token-pair frequencies.
4. Merge the most frequent pair.
5. Add the new token to the vocabulary.
6. Repeat for a specified number of merges.

Example:

```text
low
↓
l o w </w>

Merge ('l','o') → 'lo'
Merge ('lo','w') → 'low'

Result:
low </w>
```

## Example

### Training Corpus

```text
low low low low low lower lower newest newest newest
```

### Encoding

Input:

```text
low lower newest
```

Output:

```text
[257, 258, 261, ...]
```

### Decoding

```text
Token IDs
     ↓
Original Text
```

## Data Structures Used

* `unordered_map` for vocabulary storage
* `map` for word-frequency tracking
* `vector` for token sequences and merge rules
* `set` for initial vocabulary construction

## Project Structure

```text
bpe_tokenizer.cpp
│
├── train()        # Learn merge rules and vocabulary
├── encode()       # Convert text into token IDs
├── decode()       # Convert token IDs back to text
└── print_vocab()  # Display learned vocabulary
```

## Key Concepts Demonstrated

* Byte Pair Encoding (BPE)
* Subword Tokenization
* Vocabulary Learning
* Frequency-Based Compression
* Token-ID Mapping
* Text Preprocessing for LLMs
* C++ STL Data Structures

## Future Improvements

* Byte-level BPE
* Vocabulary serialization
* Special tokens (`<PAD>`, `<UNK>`, `<BOS>`, `<EOS>`)
* Parallel training
* Integration with Transformer models

## Author

Built as a learning project to understand the tokenization techniques used in modern Transformer-based language models and LLMs.
