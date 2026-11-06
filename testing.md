# Part B — Testing phase (3 new cards)

> **Worked simulation:** Test predictions below follow the trained weights from [Part A](training.md). Do not change weights using the test cards.

## Locked weights

- Food = 3
- Service = 2
- Price = 1

## Test results

| Card | Food | Service | Price | Score | Prediction | Customer opinion | Correct? |
| ---: | --- | --- | --- | ---: | --- | --- | --- |
| 11 | Good | Excellent | Cheap | +6 | LIKE | LIKE | Yes |
| 12 | Bad | Bad | Expensive | -6 | DISLIKE | DISLIKE | Yes |
| 13 | Excellent | Great | Moderate | +5 | LIKE | LIKE | Yes |

**Test accuracy: 3/3 = 100%.**

## Compare training and testing

| Set | Correct / Total | Accuracy |
| --- | --- | ---: |
| First 5 training cards | 3/5 | 60% |
| Last 5 training cards | 5/5 | 100% |
| All training cards | 8/10 | 80% |
| Three new test cards | 3/3 | 100% |

The example improved during training and predicted all three held-out cards correctly. However, three test cases are too few to establish reliable performance on every possible restaurant scenario.

## Team comparison — complete after discussing with another team

The assignment asks teams to compare results. **Do not invent another team's scores.** Fill in this section from the class discussion.

| Question | Our simulation | Other team's actual result |
| --- | --- | --- |
| Training accuracy | 80% | _To be recorded_ |
| Testing accuracy | 100% | _To be recorded_ |
| Most influential feature | Food (weight 3) | _To be recorded_ |
| Who improved the most? | We improved from 60% (first five) to 100% (last five) | _Compare after discussion_ |

**Comparison discussion:** The most influential feature in this example was Food because it ended with the largest weight. We should compare both teams' change in accuracy, not just their final score, when deciding who improved most.
