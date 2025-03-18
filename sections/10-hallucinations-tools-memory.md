# Hallucinations, Tool-Use, and Knowledge/Working Memory

## Table of Contents

- [Hallucinations](#hallucinations)
    - ["The Llama 3 Herd of Models"](#the-llama-3-herd-of-models)
        - [Mitigation #1](#mitigation-1)
        - [Mitigation #2](#mitigation-2)
- [Tool-Use](#tool-use)

## Hallucinations

> ### Train Time Examples
> **Human:** "Who is Tom Cruise?"
> **Assistant:** "Tom Cruise is a famous American actor and producer..."
>
> **Human:** "Who is John Barrasso?"
> **Assistant:** "John Barrasso is an American physician and politician..."
>
> **Human:** "Who is Genghis Khan?"
> **Assistant:** "Genghis Khan was the founder of the Mongol Empire."
>
> ...
>
> ### Test Time Examples
> **Human:** "Who is Orson Kovacs?"
> **Assistant:** ???
> </details>

During training, the LLM is trained on real data, so it generates accordingly.
During inference, the model statistically imitates the training data, so it gives the same style of answer, and generates token-by-token.

When asked to generate, the model will first generate the name of the person, as in the training data.

After generating "Orson Kovacs is...", the model hallucinates the rest of the sentence because the generation of the next token is already biased towards SOMETHING, rather than "I don't know".

> [!INFO]
> Recent models are less prone to hallucinations, and might tell ou they don't know. But hallucinations still happen.

### "The Llama 3 Herd of Models"
A paper from Meta, 2024-07-23.

In this paper, the authors describe the procedure to make the model figure out what it knows and doesn't know. They improved the training data accordingly.

### Mitigation #1:

- Take a model to be LLM-as-a-judge.
- Generate some Q&A pairs with the judge, from a factually correct source of information.
- Ask the underlying model to answer the questions.
- If the model answers with an hallucination, we systematically add the question with the following answer: "I don't know.".

If we do this many times, the model will increasingly learn to say "I don't know" when it doesn't know the answer.

### Mitigation #2:

Allow the mode to search!

After the search, the model has enough context to generate a more accurate answer.

This is an example of using a tool (and possibly also a memory call).

## Tool-Use and Knowledge/Working Memory

The model has the option to initiate tools, such as search.

When the inference engine recognize the special tokens generated, e.g. "<SEARCH_START>Who is Orson Kovacs?<SEARCH_END>", it will initiate the search tool with the text written between the special tokens.

The results of the search will be added to the context window.

> [!NOTE]
> The model can also (implicitly) decide that it knows the answers and doesn't need to search.

#### "Vague recollection" vs. "Working memory"
- Knowledge in the parameters == **Vague recollection** (e.g. of something you read 1 month ago).
- Knowledge in the tokens of the context window == **Working memory**.

=> Working memory is more reliable than vague recollection.