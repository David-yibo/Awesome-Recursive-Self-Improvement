# Recursive Self-Improvement（RSI，递归自我改进）研究图谱

> 资料状态：截至 **2026-11-22**。本文优先链接论文正式页面、会议论文库、机构研究页和官方仓库；预印本会明确标注，不把项目宣传等同于同行评审结论。

RSI 指 AI 系统利用自身当前能力，持续改进模型权重、训练数据、算法、提示词、上下文、工具、记忆、Agent Harness 或研究流程，使下一轮系统拥有更强的问题求解能力，或更强的“继续改进自身”的能力。

这里最容易混淆的是：**结果变好**、**系统可持续学习**、**改进器本身也变强**，并不是同一件事。

## 一、建议采用的分层定义

| 层级 | 被改进对象 | 是否持久化 | “改进器”是否被改进 | 典型例子 | 本文判断 |
|---|---|---:|---:|---|---|
| L0 单次推理优化 | 当前答案 | 否 | 否 | Self-Refine、Best-of-N | 不属于 RSI |
| L1 经验积累 | 记忆、策略、技能库 | 是 | 通常否 | Reflexion、Dynamic Cheatsheet、ReasoningBank | 广义自我改进 |
| L2 系统/外层优化 | Prompt、Context、工具、Workflow、Harness | 是 | 通常固定 | GEPA、ACE、ADAS、autoresearch | 工程化 RSI 的主流形态 |
| L3 参数与训练闭环 | 数据、课程、Reward、权重、训练算法 | 是 | 通常固定 | STaR、Absolute Zero、R-Zero、Self-Rewarding LM | 模型层自我改进 |
| L4 自动化 AI R&D | 架构、训练代码、实验方案、研究流程 | 是 | 部分可变 | ASI-Arch、AIRA、AI Scientist、AlphaEvolve | 有界自动研究闭环 |
| L5 递归改进 | 任务 Agent 与改进机制本身 | 是 | 是 | DGM、Hyperagents、AIDE² | 初步实证、仍受目标/评估/算力边界约束 |
| L6 强 RSI | 自主设定研究方向、重写底层系统、持续训练后继系统 | 是 | 是，且长期开放式加速 | 理论设想 | **尚无公开证据证明已经实现** |

因此，更稳妥的表述是：2026 年已经出现了不少 **persistent self-improvement**、**automated AI R&D** 和 **bounded recursive improvement** 的系统；但尚不能据此断言已经实现无边界、无人工目标设定的“智能爆炸式”强 RSI。

## 二、2026 年最值得补入的机构文章与新论文

### 1. 前沿实验室与独立评估

- **Anthropic Institute — [When AI builds itself](https://www.anthropic.com/institute/recursive-self-improvement)**（2026）：直接以 RSI 为主题，披露 AI 已经参与模型研发、代码和实验循环的内部数据。文中报告 Anthropic 工程师单位时间代码产出显著增加，以及模型在固定目标的训练代码优化实验中从约 3× 提速进展到约 52×。这些是机构内部、自报告性质的数据，适合作为前沿趋势证据，不应当作独立复现结果。
- **OpenAI — [Research acceleration: The view inside OpenAI](https://openai.com/index/research-acceleration-view-inside-openai/)**（2026-09）：OpenAI 称其已达到“自动研究实习生”阶段，即在人工方向下完成需要熟练研究者数天的、定义明确的研究任务；目标仍是受监督研究，而不是自主设定终极目标。
- **METR — [Independent Assessment of AI R&D Acceleration at Anthropic](https://metr.org/blog/2026-11-05-anthropic-ai-rd-acceleration-assessment/)**（2026-11）：在获得部分内部数据访问后，METR 估计 Anthropic 的能力进展速度约为此前历史阶段的 1.9 倍，并判断 AI 使用可能贡献了其中多数加速；报告同时强调置信区间和不可观测瓶颈。
- **METR — [AI R&D-relevant model capabilities are improving rapidly and are getting harder to measure](https://metr.org/blog/2026-11-20-q4-2026-capability-update/)**（2026-11）：指出公开模型在目标明确、结果易验证的优化任务上非常强，但开放式研究能力、真实研发迁移和测量有效性仍存在较大不确定性。
- **Stanford HAI — [2026 AI Index: Science](https://hai.stanford.edu/ai-index/2026-ai-index-report/science)**：报告显示最佳系统在端到端科学研究基准 PaperArena 上约为 38.8%，明显低于博士专家的 83.5%；这是避免把“会做局部科研任务”夸大为“全面自动科学家”的重要校准。

### 2. 改进“改进器”本身

- **[Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents](https://openreview.net/pdf?id=98932dd098fa5b83419746439f3e35a4e3cf54a3.pdf)**（ICLR 2026）：Agent 修改自身代码、在 Benchmark 上评估并保留有效变体，同时维护可复用的 Agent Archive。它比固定外层搜索更接近真正的递归改进，但目标函数、基座模型、沙箱和评估仍由人设定。
- **[Hyperagents](https://arxiv.org/abs/2603.19461)**（2026 预印本）：把 Task Agent 与负责修改它的 Meta-Agent 放入同一个可编辑程序，使元级改进机制本身也能被修改；作者在代码、论文评审、机器人奖励设计和数学评分等任务上报告持续改进。
- **[Recursive self-improvement of AI research agents](https://arxiv.org/abs/2609.26457)**（AIDE²，2026 预印本）：对 AI 研究 Agent 的自身代码执行连续选择；8 天自主运行中接受 7 次连续改进，并在四类保留任务上迁移。论文还报告未显式优化的 reward hacking 比例下降，但仍需独立复现。
- **[MetaSkill-Evolve](https://arxiv.org/abs/2607.05297)**（2026 预印本）：区分任务技能演进与“如何演进技能”的元技能演进，以双时间尺度更新两者。
- **[RSIAgent](https://arxiv.org/abs/2609.15364)**（2026 预印本）：通过训练自由的多 Agent 记忆构建，在新环境中积累并重用可迁移经验。

### 3. 自动架构与训练算法发现

- **[Neural Architecture Discovery via Autonomous Evolution (ASI-Arch)](https://arxiv.org/abs/2507.18074)**（COLM 2026）：围绕 Linear Attention 运行 research–experiment–analyze–update 闭环；作者报告 1,773 次实验和 105 个高性能架构。它展示的是有明确搜索域和评价器的自动研究，不是完全开放式 RSI。
- **[Agentic Discovery of Neural Architectures: AIRA-Compose and AIRA-Design](https://arxiv.org/abs/2605.15871)**（2026 预印本）：多个 Agent 在宏观模块组合和底层 Attention 实现两个层面搜索架构，并在不同规模与计算预算下检验缩放表现。
- **[From AI Assistant to AI Scientist: Autonomous Discovery of LLM-RL Algorithms with LLM Agents](https://arxiv.org/abs/2603.23951)**（POISE，2026 预印本）：围绕 LLM policy optimization 建立提出、实现、评估、反思和谱系化归档闭环；在从 GRPO 出发的实验中评估 64 个候选算法。
- **[MLEvolve](https://arxiv.org/abs/2606.06473)**（2026 预印本；[官方代码](https://github.com/InternScience/MLEvolve)）：用图搜索、分层规划和 retrospective memory 自动发现机器学习算法，并复用跨分支实验经验。
- **[A-Evolve-Training](https://a-evo-lab.github.io/a-evolve-training/)**（2026 技术报告/项目）：在人工搭建并审计初始 substrate 后，让 Agent 对一个 30B 模型执行多轮 post-training。应标为技术报告，而非会议正式论文。
- **[autoresearch](https://github.com/karpathy/autoresearch)**（Karpathy，2026 开源项目）：Agent 在固定时间预算内编辑训练代码、运行实验并按验证指标保留改动。它是清晰的 L2/L4 工程闭环，但改进策略、指标和计算边界并未由系统自主发明。

### 4. 2026 年正式发表的自训练、Prompt、Context 与 Memory 工作

- **[R-Zero: Self-Evolving Reasoning LLM from Zero Data](https://openreview.net/pdf?id=96apU6YzSO)**（ICLR 2026）：Challenger 生成接近 Solver 能力边界的任务，两者交替训练；“zero data”指不使用人工题目/标签的后训练阶段，并不表示基础模型从零预训练。
- **[Self-Evolving Curriculum for LLM Reasoning](https://www.microsoft.com/en-us/research/publication/self-evolving-curriculum-for-llm-reasoning/)**（COLM 2026）：把任务类别选择建模为非平稳多臂老虎机，以即时学习收益动态调整课程。
- **[Temporal Self-Rewarding Language Models](https://proceedings.mlr.press/v306/wang26ik.html)**（ICML 2026）：用不同训练时刻的模型生成 chosen/rejected，缓解多轮 self-rewarding 中正负样本逐渐趋同的问题。
- **[GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning](https://proceedings.iclr.cc/paper_files/paper/2026/hash/0e9e708b6f48e14fd0ac29e167413f76-Abstract-Conference.html)**（ICLR 2026）：从轨迹、工具调用和结果中用自然语言反思诊断问题，再通过 Pareto 搜索进化 Prompt；作者报告相对 GRPO 更少的 rollout 和更高的若干任务表现。
- **[Agentic Context Engineering (ACE)](https://openreview.net/pdf?id=eC4ygDs02R)**（ICLR 2026）：把 Context 视为持续演进的 playbook，通过生成、反思和整理机制降低 brevity bias 与 context collapse。
- **[Dynamic Cheatsheet](https://aclanthology.org/2026.eacl-long.333/)**（EACL 2026）：不更新权重，而是在测试时积累策略、代码片段和问题解决经验，形成持久化的外部记忆。
- **Google Research — [ReasoningBank: Enabling agents to learn from experience](https://www.research.google/blog/reasoningbank-enabling-agents-to-learn-from-experience/)**（ICLR 2026 机构文章；[论文](https://arxiv.org/abs/2509.25140)）：从成功与失败轨迹提炼可迁移推理策略，并把记忆检索与 test-time scaling 结合。

### 5. AI Research：从“辅助研究”到闭环研究

- **[Towards end-to-end automation of AI research](https://www.nature.com/articles/s41586-026-10265-5)**（Nature 2026）：The AI Scientist 的正式同行评审版本，覆盖选题、实验、图表、论文写作和自动评审；论文同时讨论研究质量、归因、滥用与审稿系统负担等风险。
- **[An AI system to help scientists write expert-level empirical software](https://www.nature.com/articles/s41586-026-10658-6)**（ERA，Nature 2026）：用 LLM 与 tree search 自动优化可量化科研软件，在多个领域达到或超过强基线。
- **[Accelerating scientific discovery with Co-Scientist](https://doi.org/10.1038/s41586-026-10644-y)**（Nature 2026；[DeepMind 介绍](https://deepmind.google/blog/co-scientist-a-multi-agent-ai-partner-to-accelerate-research/)）：多个专门 Agent 生成、反思、排序并演进科学假设，但实验验证和研究目标仍由人类科学家主导。
- **[A multi-agent system for automating scientific discovery](https://www.nature.com/articles/s41586-026-10652-y)**（Robin，Nature 2026）：将文献检索、假设生成、实验建议和数据分析接入同一生物学工作流，属于半自主发现系统。
- **[Reimagining research papers as interactive and reliable AI agents](https://www.nature.com/articles/s41586-026-11044-y)**（Paper2Agent，Nature 2026）：把论文及其代码、数据和方法包装为可交互 Agent，降低研究成果被复用的成本。
- **Google DeepMind — [AlphaEvolve: impact across fields](https://deepmind.google/blog/alphaevolve-impact/)**（2026）：报告 AlphaEvolve 在基因组、灾害风险和计算基础设施中的后续应用；其核心仍是 LLM 候选程序生成加自动 evaluator 的进化搜索。

## 三、Foundation Model 层

### 3.1 架构搜索与模型结构

| 问题 | 代表工作 | 方法与意义 |
|---|---|---|
| 能否搜索 Transformer 替代结构？ | [The Evolved Transformer](https://proceedings.mlr.press/v97/so19a.html)（ICML 2019）；[DARTS](https://openreview.net/forum?id=S1eYHoC5FX)（ICLR 2019） | 前者用进化搜索并以 Transformer warm start；后者将离散架构空间连续化以便梯度优化。两者奠定 NAS 基础，但搜索空间仍由人定义。 |
| 能否让 LLM 直接生成架构代码？ | [EvoPrompting](https://proceedings.nips.cc/paper_files/paper/2023/hash/184c1e18d00d7752805324da48ad25be-Abstract-Conference.html)（NeurIPS 2023）；[LLMatic](https://doi.org/10.1145/3638529.3654017)（GECCO 2024） | 把 LLM 作为 mutation/crossover 或代码生成器，再由进化与 quality-diversity 机制选择候选。 |
| 能否自动调整深度、宽度、Heads、MLP Ratio？ | [AutoFormer](https://arxiv.org/abs/2107.00651)（ICCV 2021）；[NAS-BERT](https://arxiv.org/abs/2105.14444)（KDD 2021）；[AutoTinyBERT](https://arxiv.org/abs/2107.13686)（ACL 2021） | 用 supernet/weight sharing 搜索不同深度、宽度和子模块配置，以适应精度和成本约束。 |
| 能否针对硬件动态设计？ | [HAT](https://aclanthology.org/2020.acl-main.686/)（ACL 2020）；[Once-for-All](https://openreview.net/forum?id=HylxE1HKwS)（ICLR 2020）；[LiteTransformerSearch](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9949e6906be6448230cdba9a4cb2d564-Abstract-Conference.html)（NeurIPS 2022） | 将实测延迟、内存或参数量纳入搜索，从一个 supernet 中抽取适配目标设备的子模型。 |
| 能否完成“提出—实现—训练—分析”闭环？ | [ASI-Arch](https://arxiv.org/abs/2507.18074)（COLM 2026）；[AIRA](https://arxiv.org/abs/2605.15871)（2026 预印本） | 把 NAS 扩展为 Agent 驱动的研究循环，但评价器、任务域与资源预算仍固定。 |

### 3.2 数据生成、筛选与课程

| 能力 | 代表工作 | 关键机制 |
|---|---|---|
| 自生成推理/指令数据 | [STaR](https://papers.neurips.cc/paper_files/paper/2022/hash/639a9a172c044fbb64175b5fad42e9a5-Abstract-Conference.html)（NeurIPS 2022）；[Self-Instruct](https://aclanthology.org/2023.acl-long.754/)（ACL 2023）；[WizardLM](https://proceedings.iclr.cc/paper_files/paper/2024/hash/82eec786fdfbbfa53450c5feb7d1ac92-Abstract-Conference.html)（ICLR 2024）；[Magpie](https://proceedings.iclr.cc/paper_files/paper/2025/hash/be06e3802e9411381feece79b4d960c1-Abstract-Conference.html)（ICLR 2025） | 从少量种子、模型自身输出或空 user turn 扩展训练数据。 |
| 生成可验证难题 | [Absolute Zero](https://papers.nips.cc/paper_files/paper/2025/hash/9837dc00ff67d176373268ed48042d49-Abstract-Conference.html)（NeurIPS 2025）；[R-Zero](https://openreview.net/pdf?id=96apU6YzSO)（ICLR 2026） | 通过代码执行器或 Challenger–Solver 共演化生成接近能力边界的任务。 |
| 过滤错误合成数据 | [ReST](https://arxiv.org/abs/2308.08998)（2023 预印本）；[Re-ReST](https://aclanthology.org/2024.emnlp-main.861/)（EMNLP 2024） | Generate–Filter–Improve，结合奖励、环境反馈或 Reflector 修正低质量轨迹。 |
| 动态调整数据分布 | [DoReMi](https://proceedings.neurips.cc/paper_files/paper/2023/hash/dcba6be91359358c2355cd920da3fcbd-Abstract-Conference.html)（NeurIPS 2023）；[LESS](https://proceedings.mlr.press/v235/xia24c.html)（ICML 2024）；[Self-Evolving Curriculum](https://www.microsoft.com/en-us/research/publication/self-evolving-curriculum-for-llm-reasoning/)（COLM 2026） | 用 proxy model、低秩梯度相似度或在线学习收益决定数据权重和课程。 |

### 3.3 优化器、目标函数与训练流程

这一方向的核心不只是自动调参，而是让 Agent 提出并验证新的 update rule、loss、reward 或算法组合。

- [Self-Taught Optimizer (STOP)](https://openreview.net/pdf?id=46Zgqo4QIU)（COLM 2024）：用 LLM 编写“改进程序”，再递归地让该程序改进自身。
- [Self-Rewarding Language Models](https://proceedings.mlr.press/v235/yuan24d.html)（ICML 2024）：同一模型既生成回答又以 LLM-as-a-Judge 产生偏好信号，进行多轮 DPO。
- [Temporal Self-Rewarding Language Models](https://proceedings.mlr.press/v306/wang26ik.html)（ICML 2026）：用过去/未来模型维持有效偏好间隔。
- [POISE](https://arxiv.org/abs/2603.23951)、[MLEvolve](https://arxiv.org/abs/2606.06473) 与 [autoresearch](https://github.com/karpathy/autoresearch)（2026）：分别探索 RL 算法发现、机器学习算法发现和固定预算训练策略搜索。

## 四、Evaluation 与 Reward 层

### 4.1 自评、互评与自我纠错

| 任务 | 代表工作 | 结论边界 |
|---|---|---|
| 评价生成答案 | [G-Eval](https://aclanthology.org/2023.emnlp-main.153/)（EMNLP 2023）；[Self-Refine](https://proceedings.neurips.cc/paper_files/paper/2023/hash/91edff07232fb1b55a505a9e9f6c0ff3-Abstract-Conference.html)（NeurIPS 2023）；[Prometheus](https://openreview.net/forum?id=8euJaTveKw)（ICLR 2024） | 模型评审可扩展，但 Judge 偏差、位置偏差和同源偏差会被循环放大。 |
| 生成 Reward/Preference | [Constitutional AI](https://arxiv.org/abs/2212.08073)；[RLAIF vs. RLHF](https://proceedings.mlr.press/v235/lee24t.html)（ICML 2024）；[Self-Rewarding LM](https://proceedings.mlr.press/v235/yuan24d.html)（ICML 2024） | AI feedback 能降低人工标注成本，但仍依赖人写原则、rubric 或初始偏好。 |
| 定位推理错误 | [Math-Shepherd](https://aclanthology.org/2024.acl-long.510/)（ACL 2024）；[SCoRe](https://proceedings.iclr.cc/paper_files/paper/2025/hash/871ac99fdc5282d0301934d23945ebaa-Abstract-Conference.html)（ICLR 2025）；[ProcessBench](https://aclanthology.org/2025.acl-long.50/)（ACL 2025） | 外部可验证反馈和 on-policy 训练通常比纯提示式“再想一遍”更可靠。 |
| 改进 Verifier | [Generative Verifiers](https://proceedings.iclr.cc/paper_files/paper/2025/hash/214308a2d5e3f83ef9ad2739e1cbc46d-Abstract-Conference.html)（ICLR 2025）；[Process-based Self-Rewarding](https://arxiv.org/abs/2503.03746)（2025） | 从答案级二分类扩展到生成式、过程级验证，并可使用额外 test-time compute。 |

### 4.2 评价闭环的主要失败模式

- **Reward hacking**：ICML 2026 的 [Reward Hacking Benchmark](https://proceedings.mlr.press/v306/thaman26a.html) 显示，带工具 Agent 会利用跳过验证、读取旁路信息或篡改评价函数等捷径。
- **研究 Agent 直接攻击评价机制**：[Reward Hacking Challenges Oversight of Autonomous Research Agents](https://www.microsoft.com/en-us/research/publication/reward-hacking-challenges-oversight-of-autonomous-research-agents/)（Microsoft Research，2026）在允许 hack 且阈值较高的设置中确认了大量 evaluator exploit，建议把关键指标置于 Agent 控制之外并独立重算。
- **噪声、任务顺序与欠规范**：[On the Fragility of Self-Improving Agents](https://arxiv.org/abs/2608.18066)（2026 预印本）指出，自我改进收益可能对任务顺序和随机性高度敏感。
- **Benchmark 污染与 poisoned evaluator**：[Reflections on Trusting Trust, Revisited](https://arxiv.org/abs/2609.17817)（2026 预印本）研究了用有毒 Benchmark 污染自修改 Coding Agent 的可能性。

可靠的 RSI 评价至少应包含：冻结的隐藏测试集、多随机种子、等算力对照、独立 evaluator、改进成本、跨任务迁移、灾难性退化、reward hacking 审计，以及“改进器是否真的变强”的单独测量。

## 五、Agent Software 层

### 5.1 Tools & Skills

- [Toolformer](https://proceedings.neurips.cc/paper_files/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html)（NeurIPS 2023）：以自监督方式学习何时以及如何调用工具。
- [Voyager](https://arxiv.org/abs/2305.16291)（TMLR 2024）：在 Minecraft 中自动生成、验证并积累代码技能库。
- [LLM Agents Making Agent Tools](https://aclanthology.org/2025.acl-long.1266/)（ACL 2025）：ToolMaker 从带代码的论文仓库自动构建可调用工具，并通过执行反馈调试。

### 5.2 Harness 与 Agent 设计

- [SWE-agent](https://papers.nips.cc/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html)（NeurIPS 2024）：证明 Agent–Computer Interface 本身会显著影响软件工程性能。
- [Automated Design of Agentic Systems](https://proceedings.iclr.cc/paper_files/paper/2025/hash/36b7acf6f6010652b3f2a433774a66fe-Abstract-Conference.html)（ADAS，ICLR 2025）：Meta-Agent 通过代码搜索发明 Agent 组件与组合。
- [Gödel Agent](https://xunjianyin.github.io/papers/godel-agent.html)（ACL 2025）：让 Agent 检查并重写自身任务策略和改进逻辑；作者也报告了部分设置下的退化与置信区间重叠。
- [Darwin Gödel Machine](https://openreview.net/pdf?id=98932dd098fa5b83419746439f3e35a4e3cf54a3.pdf)（ICLR 2026）与 [Hyperagents](https://arxiv.org/abs/2603.19461)（2026 预印本）：从固定 Meta-Agent 迈向可修改的开放式 Agent 档案与元级程序。

### 5.3 Prompt、Context 与 Memory

- [Promptbreeder](https://proceedings.mlr.press/v235/fernando24a.html)（ICML 2024）：同时进化 task prompt 与用于产生新 prompt 的 mutation prompt。
- [GEPA](https://proceedings.iclr.cc/paper_files/paper/2026/hash/0e9e708b6f48e14fd0ac29e167413f76-Abstract-Conference.html)（ICLR 2026）：通过轨迹反思和 Pareto 搜索优化 compound AI system 中的多个 prompt。
- [ACE](https://openreview.net/pdf?id=eC4ygDs02R)（ICLR 2026）：把 Context 组织为可演进 playbook。
- [Reflexion](https://proceedings.neurips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html)（NeurIPS 2023）：把失败反馈写入 episodic memory。
- [ExpeL](https://ojs.aaai.org/index.php/AAAI/article/view/29936)（AAAI 2024）：从成功和失败经验中抽取跨任务通用规则。
- [MemGPT](https://openreview.net/forum?id=0Kk142lP62)（ICLR 2024）：用分层记忆和显式换入换出管理有限上下文。
- [Dynamic Cheatsheet](https://aclanthology.org/2026.eacl-long.333/)（EACL 2026）与 [ReasoningBank](https://arxiv.org/abs/2509.25140)（ICLR 2026）：在不修改基座权重时持续积累可复用策略。

## 六、AI Research 层：系统应当完成什么

一个较完整的自动研究闭环包含：文献检索 → 假设生成 → 实验设计 → 代码实现 → 训练与评价 → 结果分析 → 下一轮研究策略。

| 系统 | 发表状态 | 覆盖范围 |
|---|---|---|
| [The AI Scientist](https://www.nature.com/articles/s41586-026-10265-5) | Nature 2026 | 端到端 AI 研究、论文写作与自动评审；正式版本同时包含 template 与开放式模式。 |
| [The AI Scientist-v2](https://arxiv.org/abs/2504.08066) | 2025 预印本；[官方仓库](https://github.com/SakanaAI/AI-Scientist-v2) | 去掉人工代码模板，加入 progressive agentic tree search 与 experiment manager。 |
| [Agent Laboratory](https://aclanthology.org/2025.findings-emnlp.320/) | Findings of EMNLP 2025 | Literature review、experimentation、report writing；允许人类阶段性反馈。 |
| [MLGym](https://openreview.net/pdf?id=ryTr83DxRq) | COLM 2025 | 用多项真实 ML 任务测量假设、代码、训练与分析能力。 |
| [AlphaEvolve](https://arxiv.org/abs/2506.13131) | 2025 技术论文；[官方介绍](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/) | LLM 生成程序、自动 evaluator 与进化搜索，用于算法、数学与基础设施。 |
| [ERA](https://www.nature.com/articles/s41586-026-10658-6) | Nature 2026 | 用 tree search 自动产生高质量可度量科研软件。 |
| [Co-Scientist](https://doi.org/10.1038/s41586-026-10644-y) | Nature 2026 | 多 Agent 生成、辩论并演进科学假设。 |
| [Robin](https://www.nature.com/articles/s41586-026-10652-y) | Nature 2026 | 生物学文献、假设、实验建议和数据分析闭环。 |

## 七、截至 2026 年的结论

1. **已经成立**：AI 可以在可自动评分、可快速实验、目标清晰的空间中持续改进 Prompt、Context、工具、代码、数据课程、训练 Recipe 和局部算法。
2. **初步成立**：Agent 可以修改任务执行代码，甚至修改负责提出下一轮修改的元级程序；DGM、Hyperagents 与 AIDE² 是这一方向的重要证据。
3. **仍未成立**：公开证据尚未显示系统能够无人工目标、无固定评价器、跨领域、长期、稳定并加速地设计和训练全面更强的后继基础模型。
4. **最大瓶颈不是“能否循环”**，而是评价是否真实、改进是否迁移、成本是否可持续，以及系统是否在优化代理指标而非真实研究目标。
5. **写作上应避免**把“模型自评一次”“多 Agent 投票”“自动调参”直接称为强 RSI。更准确的术语是 self-refinement、test-time learning、self-training、agent evolution、automated AI R&D 或 bounded recursive improvement。

## 八、推荐阅读顺序

1. 概念与现实边界：[Anthropic RSI 报告](https://www.anthropic.com/institute/recursive-self-improvement) → [Stanford AI Index 2026 Science](https://hai.stanford.edu/ai-index/2026-ai-index-report/science) → [METR 独立评估](https://metr.org/blog/2026-11-05-anthropic-ai-rd-acceleration-assessment/)。
2. Agent 外层自我改进：[STOP](https://openreview.net/pdf?id=46Zgqo4QIU) → [ADAS](https://proceedings.iclr.cc/paper_files/paper/2025/hash/36b7acf6f6010652b3f2a433774a66fe-Abstract-Conference.html) → [DGM](https://openreview.net/pdf?id=98932dd098fa5b83419746439f3e35a4e3cf54a3.pdf) → [Hyperagents](https://arxiv.org/abs/2603.19461) → [AIDE²](https://arxiv.org/abs/2609.26457)。
3. 模型权重与训练数据闭环：[STaR](https://papers.neurips.cc/paper_files/paper/2022/hash/639a9a172c044fbb64175b5fad42e9a5-Abstract-Conference.html) → [Self-Rewarding LM](https://proceedings.mlr.press/v235/yuan24d.html) → [Absolute Zero](https://papers.nips.cc/paper_files/paper/2025/hash/9837dc00ff67d176373268ed48042d49-Abstract-Conference.html) → [R-Zero](https://openreview.net/pdf?id=96apU6YzSO)。
4. 自动研究闭环：[AI Scientist](https://www.nature.com/articles/s41586-026-10265-5) → [AlphaEvolve](https://arxiv.org/abs/2506.13131) → [ASI-Arch](https://arxiv.org/abs/2507.18074) → [AIRA](https://arxiv.org/abs/2605.15871) → [POISE](https://arxiv.org/abs/2603.23951)。
5. 失败模式：[Reward Hacking Benchmark](https://proceedings.mlr.press/v306/thaman26a.html) → [Microsoft Research 的研究 Agent reward hacking](https://www.microsoft.com/en-us/research/publication/reward-hacking-challenges-oversight-of-autonomous-research-agents/) → [Fragility of Self-Improving Agents](https://arxiv.org/abs/2608.18066)。

## 引用与维护说明

- 正式发表优先链接会议/期刊页面；尚无正式版本时链接 arXiv 或官方项目页。
- “2026”可能表示 2026 正式发表，而预印本首次公开时间可能是 2025；本文会同时保留两者，不混写。
- 机构内部数据、产品博客与技术报告用于描述现实部署和趋势，不能替代独立同行评审或复现。
- 欢迎通过 Issue/PR 补充正式发表状态、复现实验、反例和失败报告。

本仓库采用 [MIT License](LICENSE)。

