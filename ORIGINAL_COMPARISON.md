# 原始定性对比表

[返回展示首页](README.md)

以下将用户提供的 LaTeX 表格拆成四张 GitHub Markdown 表，完整保留九个方法的字段和等级。`\ourmethod` 按项目上下文显示为 **ReTune**。本文件是原稿归档，**不是经过统一实验验证的结论表**；版本与机制修订见 [README](README.md)。

`✓`、`✗`、`--` 分别对应原表的勾、叉和未标注。`--` 不应解读为不需要、不支持或不存在。

## 1. LLM 部署与克隆环境

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

## 2. 参数选择

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

## 3. 配置探索

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

## 4. 配置推荐

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

## 术语

| 缩写 | 英文 | 中文 |
| :--- | :--- | :--- |
| ST | Stress Testing | 压力测试；展示时建议进一步说明是否为代表性负载回放。 |
| CE | Clone Environment | 克隆环境；与独立测试集群、真实系统反馈区分。 |
| BO | Bayesian Optimization | 贝叶斯优化。 |
| GP | Gaussian Process | 高斯过程。 |
| RL | Reinforcement Learning | 强化学习。 |
| RAG | Retrieval-Augmented Generation | 检索增强生成。 |
| LASSO | Least Absolute Shrinkage and Selection Operator | 使用 L1 正则化进行回归与变量选择。 |
| CEM | Cross-Entropy Method | 交叉熵方法；README 中用于说明 ReTune 数值探索。 |
| Workload sim. | Workload Similarity | 按本项目设计指工作负载相似度，建议在正式表格中写全。 |

## 正式展示前应修订的口径

1. **E2ETune 阶段划分**：论文中的代价模型用于离线标签生成，在线配置由微调模型推荐；原表的 `Cost model` 可能混淆阶段。[论文](https://www.vldb.org/pvldb/vol18/p5540-huang.pdf)
2. **部署分类**：开放权重与本地部署不是同义词。λ-Tune 当前仓库已有本地模型入口；若复现论文实验，仍应固定相应代码与调用方式。[作者仓库](https://github.com/gsvic/lambda-tune)
3. **CE 分类**：应逐项补充原文证据，明确是论文实验设置还是方法必需条件。STELLAR 使用 CloudLab 测试集群，这一事实本身不能证明必须克隆生产环境。[论文 §5.1](https://arxiv.org/html/2602.23220v1)
4. **效率与精度等级**：需说明统一负载、预算、指标和分级阈值；否则仅保留为作者定性判断。
5. **安全等级**：将真实测量、约束检查、退化检测及恢复能力分开描述。压力测试或相似度匹配均不单独构成安全保证。
6. **引用版本**：E2ETune 正式版为 PVLDB 2025；AgentTune 当前作者仓库标注 SIGMOD 2026；STELLAR 的 SC 2025 工作另有 2026 年 arXiv 版本。引用键中的年份可以与正式出版年份不同，需核对参考文献条目。[E2ETune](https://www.vldb.org/pvldb/vol18/p5540-huang.pdf) · [AgentTune](https://github.com/intlyy/AgentTune) · [STELLAR 作者实验室](https://sites.google.com/udel.edu/dirlab/home)
