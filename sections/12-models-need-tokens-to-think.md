# Models Need Tokens To Think

The models train and inference on 1-dim sequence - left-to-right.
Therefore, the generated tokens NOW are extremely important for the next token.

> [!WARNING]
> The order matters.

For the following prompt:

> Human:
> "Emily buys 3 apples and 2 oranges. Each orange costs $2. The total cost of all the fruit is $13. What is the cost of apples?"

This is a BAD continuation:

> Assistant:
> "The answer is $3. This is because 2 oranges at $2 are $4 total. So the 3 apples cost $9, and therefore each apple is 9/3 = $3."

**Why?** Since when the model gets to output the token "3", it has no previous computation, and pretty much has to guess the answer. Examples like that, if they exist in the training data, will lead to model to be bad in math problems.

This is a GOOD continuation:

> Assistant:
> "The total cost of the oranges is $4. 13 - 4 = 9, the cost of the 3 apples is $9. 9/3 = 3, so each apple costs $3. The answer is $3."

**Why?** The model is building the computation as it goes, based on already computed values that exist in the context. When it gets to the token "3", it has enough information to output the correct answer.

In general, calculation, even if it is broken down into multiple simple steps, are not necessarily trustworthy.

> [!TIP]
> Ask the model (chatGPT) to use tools (code interpreter) to calculate the answer.
