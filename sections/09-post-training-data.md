# Post-training data (conversations)

After having the base model, we probably want to be able to ask questions and instruct the model.

This is done during post-training, which is cheaper (but still important) compared to pretraining. For chat models, post-training is based on conversation-structured data.

Conversations:

> Human: "What is 2+2?"
>
> Assistant: "2+2 = 4"
>
> Human: "What if it was * instead of +?"
>
> Assistant: "2*2 = 4, same as 2+2!"

> Human: "Why is the sky blue?"
>
> Assistant: "Because of Rayleigh scattering."
>
> Human: "Wow!"
>
> Assistant: "Indeed! Let me know if I can help with anything else :)"

- During this process, the models are also trained on refusal - e.g.
> Human: "How can I hack into a computer?"
>
> Assistant: "I'm sorry I can't help with that."

## Post-training steps

1. **Data collection**: Collect conversation-style data.
2. **Define the tokenization format**: Define the tokenization format for the data, translating the conversation structure to a single tokens stream, such as `gpt-4o`:
> <|im_start|>user<|im_sep|>What is 2+2?<|im_end|>
> <|im_start|>assistant<|im_sep|>2+2 = 4<|im_end|>
> <|im_start|>user<|im_sep|>What if it was *?<|im_end|>
> <|im_start|>assistant<|im_sep|>2*2 = 4, same as 2+2!<| im_end|>
3. During inference, the model will get as input a stream ending in "...<|im_start|>assistant<|im_sep|>", and will generate the next assistant response.


> [!TIP]
> While pre-training can take approx. 3 months, post-training can take a few hours, due to the much smaller dataset size.

## Post-training data sources
There are open-source databases for fine-tuning, such as in [Hugging Face](https://huggingface.co/datasets).

But nowadays, humans are usually not doing the heavy lifting of creating training data by themselves. It is usually a hybrid solution of human effort and synthetic data generation workflow.

> [!TIP]
> In the system prompt, ask the model to be a human labeller. 
> They are educated in their field, and this system prompt can change the probabilities of the model's output to the desired direction.
