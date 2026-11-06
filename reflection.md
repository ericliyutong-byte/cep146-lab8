# Lab 8 — Reflection

> These draft responses are based on the [worked training simulation](training.md). Update any details that differ from the group's actual experience.

## 1. How did your predictions improve?

At first, the model gave too much importance to service, so its first two predictions were incorrect. After comparing those predictions with the actual customer opinions, we adjusted the weights to prioritize food quality. In the example, accuracy increased from **60% on the first five cards** to **100% on the last five cards**. This shows how feedback can improve predictions over successive rounds.

## 2. How did weights (tokens) help you learn?

Tokens made the importance of each feature visible. A feature with more tokens contributed more strongly to the final score. When a prediction was wrong, we used the customer opinion to decide which feature needed more or less influence. For example, we increased Food from 1 to 3 and reduced Service from 4 to 2. This helped the decision node recognize that food quality mattered more than service on these cards.

## 3. What would happen with more layers or inputs?

More inputs could include cleanliness, restaurant location, or waiting time. More layers could combine these features into more complicated relationships, such as recognizing when excellent food compensates for poor service. A larger network might detect patterns that a single decision node misses. However, it would usually need more training examples and computation, and it could overfit if trained on too little data.

## 4. How does this reflect how real AI works?

A real neural network takes numerical inputs, combines them using learned weights, and produces an output. During supervised training, it compares predictions with target answers, computes an error, and updates parameters to reduce future error. Our token exercise represents this process in a simplified way: the group checks its guesses, adjusts the importance of inputs, and tests the resulting decision rule on new cards. Real neural networks typically use mathematical optimization such as gradient descent and can contain many interconnected neurons rather than one manually adjusted decision node.

## Conclusion

The worked simulation illustrates how **weights, prediction errors, and feedback** support pattern recognition. Food received the highest final weight because it was the strongest indicator of LIKE versus DISLIKE in these scenarios. The three-card test was successful, but more unseen examples would be needed to know whether the model generalizes reliably.
