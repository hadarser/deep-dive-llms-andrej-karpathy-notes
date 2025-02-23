# Tokenization

We can't just plug text into neural networks. We need to represent it somehow.
**Tokenization** is the process of converting text into numbers.
- **from** a 1-dimensional sequence of text
- **to** a 1-dimensional sequence of integers (1-100k), where each number represents a token, i.e., a few consecutive characters.

GPT-4 uses roughly 100k tokens.

A nice visualization of tokenization can be found [here](https://tiktokenizer.vercel.app/?model=cl100k_base).
- "helloworld" -> [h, elloworld] -> [71, 96392]
- "hello world" -> [hello, world] -> [15339, 1917]

This is still not talking about the embeddings (vectors) that represent these tokens.