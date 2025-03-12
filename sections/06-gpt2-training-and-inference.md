# GPT-2: Trainging and Inference

> Published by OpenAI on 2019
> Paper: "Language Models are Unsupervised Multitask Learners"
> Transformer model with 1.6 billion parameters
> Max context length: 1024 tokens
> Trained on 100 billion tokens

Some more information:
- Since 2019, a lot have improved:
  - Databases are of higher quality
  - Hardware is more powerful
  - Techniques are more advanced

## Training
- Every "step" is one set of changes to the model's weights
- Loss is just a proxy for the model's performance, not the actual goal
- Training (For Karpathy) took 1 day on 8xH100 GPUs. [Blog post](https://github.com/karpathy/llm.c/discussions/677)