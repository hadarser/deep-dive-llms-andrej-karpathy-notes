# Inference

The process of generating new data from the model.

- Start with some token(s).
- Feed it to the model.
- Get the probability distribution over the vocabulary, and sample a token based on this distribution.
- Append the token to the input and repeat.
- Stop when you reach a predefined length or a special ending token.