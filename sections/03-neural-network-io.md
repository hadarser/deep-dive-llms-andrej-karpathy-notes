# Step 3 - Neural Network I/O

Go to the data (1-dimensional sequence of integers), take a random window of tokens, and predict the next token.

```text
91, 860, 287, 11579, 3962, 3645
```
$\downarrow$
```text
[91, 860, 287, 11579] -> probability of next token (should be 3962)
```

This is happening simultaneously for all the windows in the data. The neural network is learning to predict the next token based on the previous tokens.