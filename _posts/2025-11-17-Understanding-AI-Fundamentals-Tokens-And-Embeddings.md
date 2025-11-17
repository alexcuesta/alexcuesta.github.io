---
layout: post
title: "Understanding AI Fundamentals: Tokens and Embeddings Explained"
category: ai
tags:
  - ai
  - machine-learning
  - embeddings
  - tokens
  - openai
  - nlp
---

Last week I have been playing around with the foundational concepts of modern AI: how text is split into tokens and how entire text is represented as a multi-dimensional vector by AI platforms like OpenAI.

# Tokens and Encodings

* Texts are split into tokens.
* The tokens can be split in different ways depending on **encodings**.
* Different models use different encodings. Example: 
    - model `gpt-4o` uses the encoding `o200k_base`
    - model `gpt-4-turbo` uses `cl100k_base`
* There are libraries to extract tokens per encoding: 
    - [tiktoken](https://github.com/openai/tiktoken/blob/main/README.md) for Python
    - [tiktoken-go](https://github.com/pkoukk/tiktoken-go) for Golang
    - [Online Tokenizer](https://platform.openai.com/tokenizer)
* Different encodings may return different numbers of tokens.
* Tokens have a numeric representation.  
E.g.: Hello World -> [24912, 2375] -> 2 tokens
* Models like OpenAI charge per number of input tokens and output tokens.

[More information about tokens on OpenAI](https://cookbook.openai.com/examples/how_to_count_tokens_with_tiktoken)


# Embeddings

* Any text is turned into a vector of a fixed dimension size, regardless of text length.
* The vector dimension depends on the model:
    - OpenAI text-embedding-3-small: 1536 dimensions
    - OpenAI text-embedding-3-large: 3072 dimensions
* Example:

```
Input: "Hello world"
Step 1: Tokenize → ["Hello", " world"] (2 tokens)
Step 2: Process → Model reads both tokens
Step 3: Output → [0.023, -0.891, ..., 0.445] (1536 dims)

Input: "Hello world, this is a very long sentence with many words"
Step 1: Tokenize → 12 tokens
Step 2: Process → Model reads all 12 tokens
Step 3: Output → [0.156, -0.234, ..., 0.789] (1536 dims - SAME SIZE!)
```

* Different text sizes generate the same number of vector dimensions thanks to the Transformer layers and Pooling:

```
1. Text Input: "Hello world"
   ↓
2. Tokenization: ["Hello", " world"] (2 tokens)
   ↓
3. Token Embeddings: Each token → vector
   ["Hello" → [0.1, 0.2, ...],
    " world" → [0.3, 0.4, ...]]
   ↓
4. Model Processing (Transformer layers):
   - Reads ALL token embeddings
   - Uses attention mechanism
   - Understands relationships between tokens
   ↓
5. Pooling/Aggregation:
   - Combines all token information
   - Common methods: mean pooling, CLS token
   ↓
6. Output: Single fixed-size vector [0.023, -0.891, ..., 0.445]
   (1536 dimensions)
```

* The similarity between two vectors is calculated using the cosine of their angle. 
  -  1: identical vectors (angle of 0°)
  -  0: perpendicular vectors (no relation)
  - -1: opposite vectors (angle of 180°)