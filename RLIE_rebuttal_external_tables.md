# RLIE Rebuttal – External Tables

## Table 1. GPT-5.4 (no-thinking) commercial-backbone results under the same linear-only setting

| Method | Backbone | Reviews | Dreaddit | Headlines | Citations | LLM Detect | Retweets |
|---|---|---:|---:|---:|---:|---:|---:|
| Zero-shot | GPT-5.4 | 54.8 / 46.1 | 65.9 / 60.5 | 61.0 / 59.5 | 62.8 / 50.7 | 82.3 / 81.9 | 64.4 / 64.5 |
| Few-shot (ICL) | GPT-5.4 | 65.8 / 65.7 | 63.7 / 58.3 | 62.4 / 62.1 | 60.6 / 50.0 | 80.7 / 80.0 | 57.8 / 54.1 |
| Zero-shot Gen | GPT-5.4 | 65.9 / 65.1 | 67.5 / 64.2 | 57.4 / 57.3 | 46.4 / 47.8 | 63.3 / 57.8 | 58.0 / 58.0 |
| IO Refinement | GPT-5.4 | 66.1 / 65.6 | 78.8 / 78.4 | 62.2 / 61.2 | 54.4 / 51.3 | 83.8 / 83.6 | 57.0 / 56.0 |
| HypoGeniC | GPT-5.4 | 69.7 / 69.8 | 80.7 / 80.7 | 60.2 / 60.3 | 51.2 / 50.6 | 85.5 / 85.4 | 62.1 / 62.0 |
| **RLIE (Ours)** | **GPT-5.4** | **75.2 / 75.2** | **83.5 / 83.5** | **67.2 / 67.2** | **64.9 / 63.4** | **91.8 / 91.8** | **66.4 / 66.4** |

## Table 2. Rule-bank-size ablation on Headlines

| # Rules | 2 | 3 | 5 | 10 | 20 | 30 |
|---|---:|---:|---:|---:|---:|---:|
| Test ACC | 0.636 | 0.644 | 0.682 | 0.674 | 0.667 | 0.671 |
| Test F1 | 0.636 | 0.644 | 0.682 | 0.674 | 0.656 | 0.663 |
| Total Tokens (M) | 7.29 | 5.72 | 11.37 | 10.61 | 17.96 | 22.45 |

## Table 3. LR aggregation vs. unweighted majority vote on saved activation datasets

| Task | LR Val ACC | Majority-Vote Val ACC | Delta |
|---|---:|---:|---:|
| headlines | 0.6733 | 0.6667 | -0.0067 |
| retweets | 0.7011 | 0.6944 | -0.0067 |
| llm_detect | 0.9011 | 0.9000 | -0.0011 |
| dreaddit | 0.8156 | 0.7867 | -0.0289 |
| reviews | 0.7300 | 0.5944 | -0.1356 |
| citations | 0.6000 | 0.4778 | -0.1222 |

## Table 4. Round-0 vs. best mean validation accuracy during iterative refinement

| Task | Round-0 Val ACC | Best Mean Val ACC | Per-repeat Best Rounds |
|---|---:|---:|---:|
| headlines | 0.6153 | 0.6660 | 6/4/3 |
| retweets | 0.6044 | 0.7167 | 5/9/4 |
| reviews | 0.6900 | 0.7156 | 5/2/3 |
| dreaddit | 0.8033 | 0.8200 | 4/3/4 |
| llm_detect | 0.8211 | 0.9167 | 5/1/12 |
| citations | 0.5556 | 0.6000 | 1/3/3 |

## Table 5. Finetuned Qwen3-8B classifier vs. RLIE (ACC/F1)

| Task | Finetuned Qwen3-8B | RLIE (ours) |
|---|---:|---:|
| headline | 0.5147 / 0.5148 | 0.6703 / 0.6702 |
| retweet | 0.5140 / 0.5139 | 0.6868 / 0.6861 |
| reviews | 0.9413 / 0.9412 | 0.7087 / 0.7074 |
| dreaddit | 0.5440 / 0.5435 | 0.8233 / 0.8232 |
| llm_detect | 0.9967 / 0.9983 | 0.9066 / 0.9065 |
| citations | 0.5208 / 0.5095 | 0.6458 / 0.6295 |


## Table 6. Best-round selection vs. last-round selection

| Task | Best-vs-last Val ACC Gap | Best-vs-last Val F1 Gap |
|---|---:|---:|
| headlines | 0.0153 | 0.0156 |
| retweets | 0.0144 | 0.0143 |
| reviews | 0.0200 | 0.0204 |
| dreaddit | 0.0089 | 0.0088 |
| llm_detect | 0.0089 | 0.0089 |
| citations | 0.0033 | 0.0087 |


## Table 7. Cross-backbone judge agreement on 6 tasks with a fixed DeepSeek V3.2–learned rule set

- DS = DeepSeek-V3.2-Exp
- Q235 = qwen3-235b-a22b-instruct-2507
- QNext = qwen3-next-80b-a3b-instruct

| Task | Non-abstain: DS vs Q235 | Non-abstain: DS vs QNext | Non-abstain: Q235 vs QNext | Prediction: DS vs Q235 | Prediction: DS vs QNext | Prediction: Q235 vs QNext |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| headlines | 0.8818 | 0.8849 | 0.8891 | 0.8620 | 0.8560 | 0.8700 |
| retweets | 0.9006 | 0.8855 | 0.9300 | 0.8533 | 0.8767 | 0.8500 |
| reviews | 0.8834 | 0.8960 | 0.8712 | 0.9067 | 0.8500 | 0.8700 |
| dreaddit | 0.9336 | 0.9201 | 0.9076 | 0.9102 | 0.8833 | 0.8733 |
| llm_detect | 0.9270 | 0.8776 | 0.8999 | 0.8633 | 0.8433 | 0.8467 |
| citations | 0.8864 | 0.8769 | 0.8759 | 0.9000 | 0.8000 | 0.8667 |

Across all six tasks, the corresponding pairwise **non-abstain agreement** ranges from **0.8712** to **0.9336**, and **prediction agreement** ranges from **0.8000** to **0.9100**.
