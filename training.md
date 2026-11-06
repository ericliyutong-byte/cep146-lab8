# Part A — Training phase (10 cards)

> **Worked simulation:** These predictions illustrate one consistent learning path. They are not a claim that a group actually produced these answers.

## Prediction method

Use the feature-to-number mapping and weighted score described in [the setup](README.md). Predict **LIKE** for scores above zero, and **DISLIKE** for scores at or below zero. Reveal the customer opinion after predicting. Only change weights after an incorrect prediction.

Initial weights: **Food = 1, Service = 4, Price = 1**.

## Training log

The weights used for each card are the weights *before* any adjustment made after that card.

| Card | Food | Service | Price | Weights used (F/S/P) | Score | Prediction | Actual opinion | Correct? | Change after feedback |
| ---: | --- | --- | --- | --- | ---: | --- | --- | --- | --- |
| 1 | Great | Poor | Cheap | 1/4/1 | -2 | DISLIKE | LIKE | No | Food +1 |
| 2 | Bad | Great | Expensive | 2/4/1 | +1 | LIKE | DISLIKE | No | Food +1; Service -2 |
| 3 | Good | Okay | Moderate | 3/2/1 | +3 | LIKE | LIKE | Yes | None |
| 4 | Poor | Poor | Cheap | 3/2/1 | -4 | DISLIKE | DISLIKE | Yes | None |
| 5 | Excellent | Excellent | Expensive | 3/2/1 | +4 | LIKE | LIKE | Yes | None |
| 6 | Okay | Bad | Moderate | 3/2/1 | -2 | DISLIKE | DISLIKE | Yes | None |
| 7 | Great | Okay | Cheap | 3/2/1 | +4 | LIKE | LIKE | Yes | None |
| 8 | Poor | Excellent | Expensive | 3/2/1 | -2 | DISLIKE | DISLIKE | Yes | None |
| 9 | Excellent | Poor | Moderate | 3/2/1 | +1 | LIKE | LIKE | Yes | None |
| 10 | Okay | Okay | Expensive | 3/2/1 | -1 | DISLIKE | DISLIKE | Yes | None |

## Why the weights changed

- **Card 1:** The model disliked the restaurant because poor service had too much influence. The true result was LIKE despite poor service, so we increased **Food from 1 to 2** to give the positive food feature more influence.
- **Card 2:** The model predicted LIKE because great service outweighed bad food and an expensive price. The true result was DISLIKE, so we increased **Food from 2 to 3**, and decreased **Service from 4 to 2** by removing two tokens.
- **Cards 3–10:** Predictions matched the supplied opinions. The example rule therefore made no further adjustments.

## Weight tracker

| Stage | Food | Service | Price | Reason |
| --- | ---: | ---: | ---: | --- |
| Before Card 1 | 1 | 4 | 1 | Starting tokens |
| After Card 1 | 2 | 4 | 1 | Food needed more influence |
| After Card 2 | 3 | 2 | 1 | Emphasize food; reduce misleading service influence |
| After Cards 3–10 | 3 | 2 | 1 | No additional mistakes |

### Final learned weights

**Food = 3 tokens; Service = 2 tokens; Price = 1 token.** Food has the strongest influence for the given restaurant cards.

## Accuracy over time

| Checkpoint | Correct predictions | Accuracy |
| --- | ---: | ---: |
| Cards 1–5 | 3/5 | 60% |
| Cards 6–10 | 5/5 | 100% |
| All 10 cards | 8/10 | 80% |

Cumulative progress: 0/1, 0/2, 1/3, 2/4, 3/5, 4/6, 5/7, 6/8, 7/9, and 8/10 correct.

**Pattern learned:** In these examples, food quality is a stronger indicator of customer opinion than service quality or price. Improving the feature weights fixed the initial misclassifications.
