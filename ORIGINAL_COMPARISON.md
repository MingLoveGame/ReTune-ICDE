# Original Qualitative Comparison

**English** | [简体中文](ORIGINAL_COMPARISON.zh-CN.md)

[Back to the guide](README.md)

The supplied LaTeX table is split into four GitHub Markdown tables below, preserving the fields and ratings for all nine methods. The project macro `\ourmethod` is displayed as **ReTune**. This file archives the original draft; **it is not a set of conclusions validated under a common experimental setup**. See the [README](README.md) for version notes and mechanism corrections.

`✓`, `✗`, and `--` correspond to the checkmark, cross, and unspecified entries in the original table. `--` should not be interpreted as unnecessary, unsupported, or absent.

## 1. LLM deployment and clone environments

| Method | LLM Deployment | CE |
| :--- | :--- | :---: |
| GPTuner | API | ✓ |
| E2ETune | Open-source | ✗ |
| TopTune | -- | ✓ |
| Rabbit | API | ✓ |
| λ-Tune | API | -- |
| AgentTune | API | -- |
| ADSTS | -- | ✓ |
| STELLAR | API | ✓ |
| **ReTune** | **Open-source** | **✗** |

## 2. Parameter selection

| Method | Method used | Efficiency | Accuracy |
| :--- | :--- | :---: | :---: |
| GPTuner | LLM | High | High |
| E2ETune | -- | -- | -- |
| TopTune | -- | -- | -- |
| Rabbit | LLM+RAG | High | High |
| λ-Tune | -- | -- | -- |
| AgentTune | Agent | High | High |
| ADSTS | LASSO+ST | Low | High |
| STELLAR | LLM+RAG | High | High |
| **ReTune** | **dual-LLM** | **High** | **High** |

## 3. Configuration exploration

| Method | Method used | Efficiency | Precision |
| :--- | :--- | :---: | :---: |
| GPTuner | BO | Low | Medium |
| E2ETune | LLM | High | Low |
| TopTune | BO | Low | High |
| Rabbit | LLM | High | Medium |
| λ-Tune | LLM | High | Medium |
| AgentTune | LLM | High | Medium |
| ADSTS | RL | Low | Low |
| STELLAR | Agent | Medium | Medium |
| **ReTune** | **Agent** | **Medium** | **High** |

## 4. Configuration recommendation

| Method | Method used | Efficiency | Safety |
| :--- | :--- | :---: | :---: |
| GPTuner | ST | Low | High |
| E2ETune | Cost model | High | Low |
| TopTune | ST | Low | High |
| Rabbit | GP+ST | Low | High |
| λ-Tune | Multi Eval+ST | Low | High |
| AgentTune | Tree+ST | Low | High |
| ADSTS | ST | Low | High |
| STELLAR | Rule+ST | Low | High |
| **ReTune** | **Workload sim.** | **High** | **High** |

## Glossary

| Abbreviation | Expansion | Meaning in this guide |
| :--- | :--- | :--- |
| ST | Stress Testing | Specify whether this includes representative workload replay when presenting a method. |
| CE | Clone Environment | Distinguish a production clone from a separate test cluster and empirical system feedback. |
| BO | Bayesian Optimization | Optimization using a probabilistic surrogate and an acquisition strategy. |
| GP | Gaussian Process | A probabilistic model used, for example, as a performance surrogate. |
| RL | Reinforcement Learning | Learning a policy from interactions and reward feedback. |
| RAG | Retrieval-Augmented Generation | Generation informed by retrieved information. |
| LASSO | Least Absolute Shrinkage and Selection Operator | Regression and variable selection using L1 regularization. |
| CEM | Cross-Entropy Method | The numerical exploration method discussed for ReTune in the README. |
| Workload sim. | Workload Similarity | Workload similarity in this project's design; spell it out in the final table. |

## Points to revise before formal presentation

1. **E2ETune's phases:** The paper uses the cost model for offline label generation, while a fine-tuned model recommends configurations online. The original `Cost model` entry may conflate these phases. [Paper](https://www.vldb.org/pvldb/vol18/p5540-huang.pdf)
2. **Deployment categories:** Open weights and local deployment are not synonymous. The current λ-Tune repository includes a local-model interface. Pin the relevant code and invocation settings when reproducing the paper. [Author repository](https://github.com/gsvic/lambda-tune)
3. **CE categories:** Add evidence from each paper and distinguish an experimental setting from an algorithmic requirement. STELLAR uses a CloudLab test cluster; this fact alone does not establish that it requires cloning production. [Paper, §5.1](https://arxiv.org/html/2602.23220v1)
4. **Efficiency and accuracy ratings:** Specify common workloads, budgets, metrics, and rating thresholds. Otherwise, retain these labels only as qualitative judgments from the draft.
5. **Safety ratings:** Describe empirical measurement, constraint checking, regression detection, and restoration separately. Neither stress testing nor similarity matching alone guarantees safety.
6. **Citation versions:** E2ETune's published version is PVLDB 2025; AgentTune's current author repository labels the work SIGMOD 2026; the SC 2025 STELLAR work also has a 2026 arXiv version. Years in citation keys may differ from publication years, so verify the bibliography entries. [E2ETune](https://www.vldb.org/pvldb/vol18/p5540-huang.pdf) · [AgentTune](https://github.com/intlyy/AgentTune) · [STELLAR author laboratory](https://sites.google.com/udel.edu/dirlab/home)
