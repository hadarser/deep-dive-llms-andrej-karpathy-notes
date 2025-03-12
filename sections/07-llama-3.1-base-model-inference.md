# Llama 3.1 Base Model Inference

## What is a base model?
Basic next-token prediction model.

That is still not very useful.

## Llama 3.1
- Llama 3.1: 405b parameters trained on 15 trillion tokens, released in July 2024.
- Llama 3.1 Instruct: what is it?

## Instruct models
Unlike base models, Instruct models are trained to generate text conditioned on a prompt. In plain English - they are trained to answer questions.

The instruct model is usually (always?) a fine-tuned version of a base model.

## Notes
- A (base) model trained on some data multiple times, can remember the data completely in its weights. Example: Zebra page on English Wikipedia.
- When trying to complete text that contain knowledge of something happened after the model was trained (i.e. future/unknown events), the model will "guess" based on the data it has seen. This is one way to get model hallucinations.