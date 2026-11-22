# Recursive Self Improvement Research Map

[English](README.md) | [简体中文](README_ZH.md)

Recursive self-improvement (RSI) refers to AI systems using their current capabilities to continually improve their model weights, training data, algorithms, prompts, context, tools, memory, agent harnesses, or research processes, so that the next iteration becomes better at solving problems—or better at continuing to improve itself.

## 1. A Recommended Taxonomy

| Level | What is improved | Persistent? | Is the improver improved? | Representative examples | Assessment |
|---|---|---:|---:|---|---|
| L0 Single-inference optimization | The current answer | No | No | Self-Refine, Best-of-N | Not RSI |
| L1 Experience accumulation | Memory, strategies, skill libraries | Yes | Usually no | Reflexion, Dynamic Cheatsheet, ReasoningBank | Self-improvement in a broad sense |
| L2 System / outer-loop optimization | Prompts, context, tools, workflows, harnesses | Yes | Usually fixed | GEPA, ACE, ADAS, autoresearch | The mainstream engineering form of RSI |
| L3 Parameter and training loops | Data, curricula, rewards, weights, training algorithms | Yes | Usually fixed | STaR, Absolute Zero, R-Zero, Self-Rewarding LM | Model-level self-improvement |
| L4 Automated AI R&D | Architectures, training code, experiment plans, research processes | Yes | Partly mutable | ASI-Arch, AIRA, AI Scientist, AlphaEvolve | Bounded automated research loops |
| L5 Recursive improvement | Both the task agent and the improvement mechanism | Yes | Yes | DGM, Hyperagents, AIDE² | Early empirical evidence, still bounded by objectives, evaluation, and compute |
| L6 Strong RSI | Autonomous research-direction setting, rewriting of the underlying system, and continued training of successor systems | Yes | Yes, with sustained open-ended acceleration | Theoretical proposals | **No public evidence yet demonstrates that this has been achieved** |

## 2. The Most Important Institutional Articles and New Papers to Add in 2026

### 2.1 Frontier Labs and Independent Evaluation

- **Anthropic Institute — [When AI builds itself](https://www.anthropic.com/institute/recursive-self-improvement)** (2026): Directly addresses RSI and presents internal data on AI participation in model R&D, coding, and experiment loops. It reports a substantial rise in code output per Anthropic engineer-hour and progress from roughly 3× to about 52× speedups in training-code optimization experiments with fixed objectives. These are internally reported results and are useful as evidence of a frontier trend, but should not be treated as independent replication.
- **OpenAI — [Research acceleration: The view inside OpenAI](https://openai.com/index/research-acceleration-view-inside-openai/)** (2026-09): OpenAI says it has reached an “automated research intern” stage, in which AI can complete clearly specified research tasks that would take a skilled researcher several days, under human direction. The stated target remains supervised research rather than autonomous selection of ultimate goals.
- **METR — [Independent Assessment of AI R&D Acceleration at Anthropic](https://metr.org/blog/2026-11-05-anthropic-ai-rd-acceleration-assessment/)** (2026-11): After receiving access to some internal data, METR estimated that Anthropic’s rate of capability progress was about 1.9 times that of earlier historical periods and judged that AI use may have contributed most of the acceleration. The report also emphasizes confidence intervals and unobserved bottlenecks.
- **METR — [AI R&D-relevant model capabilities are improving rapidly and are getting harder to measure](https://metr.org/blog/2026-11-20-q4-2026-capability-update/)** (2026-11): Finds that public models are very strong at optimization tasks with clear objectives and easily verified outcomes, while open-ended research ability, transfer to real R&D, and measurement validity remain highly uncertain.
- **Stanford HAI — [2026 AI Index: Science](https://hai.stanford.edu/ai-index/2026-ai-index-report/science)**: Reports that the best system scores about 38.8% on PaperArena, an end-to-end scientific research benchmark, well below the 83.5% achieved by PhD experts. This is an important calibration against inflating “can perform local research tasks” into “fully automated scientist.”

### 2.2 Improving the Improver Itself

- **[Darwin Gödel Machine: Open-Ended Evolution of Self-Improving Agents](https://openreview.net/pdf?id=98932dd098fa5b83419746439f3e35a4e3cf54a3.pdf)** (ICLR 2026): An agent edits its own code, evaluates changes on benchmarks, retains effective variants, and maintains a reusable agent archive. It is closer to genuine recursive improvement than a fixed outer-loop search, although its objective, base model, sandbox, and evaluation are still human-defined.
- **[Hyperagents](https://arxiv.org/abs/2603.19461)** (2026 preprint): Places a task agent and the meta-agent responsible for modifying it inside the same editable program, allowing the meta-level improvement mechanism itself to change. The authors report continued improvement across coding, paper review, robot reward design, and mathematical scoring tasks.
- **[Recursive self-improvement of AI research agents](https://arxiv.org/abs/2609.26457)** (AIDE², 2026 preprint): Applies successive selection to the code of an AI research agent. During an eight-day autonomous run, the system accepted seven consecutive improvements that transferred across four held-out task families. The paper also reports a reduction in reward hacking that was not explicitly optimized, though independent replication is still needed.
- **[MetaSkill-Evolve](https://arxiv.org/abs/2607.05297)** (2026 preprint): Separates the evolution of task skills from the evolution of the meta-skill that determines how skills should evolve, updating the two on different timescales.
- **[RSIAgent](https://arxiv.org/abs/2609.15364)** (2026 preprint): Uses training-free multi-agent memory construction to accumulate and reuse transferable experience in new environments.

### 2.3 Automated Discovery of Architectures and Training Algorithms

- **[Neural Architecture Discovery via Autonomous Evolution (ASI-Arch)](https://arxiv.org/abs/2507.18074)** (COLM 2026): Runs a research–experiment–analyze–update loop around linear attention. The authors report 1,773 experiments and 105 high-performing architectures. It demonstrates automated research within a clearly specified search domain and evaluator, not fully open-ended RSI.
- **[Agentic Discovery of Neural Architectures: AIRA-Compose and AIRA-Design](https://arxiv.org/abs/2605.15871)** (2026 preprint): Multiple agents search architectures at two levels—high-level module composition and low-level attention implementation—and test scaling behavior under different model sizes and compute budgets.
- **[From AI Assistant to AI Scientist: Autonomous Discovery of LLM-RL Algorithms with LLM Agents](https://arxiv.org/abs/2603.23951)** (POISE, 2026 preprint): Establishes a propose–implement–evaluate–reflect loop with lineage-based archiving for LLM policy optimization. In experiments starting from GRPO, it evaluates 64 candidate algorithms.
- **[MLEvolve](https://arxiv.org/abs/2606.06473)** (2026 preprint; [official code](https://github.com/InternScience/MLEvolve)): Uses graph search, hierarchical planning, and retrospective memory to discover machine-learning algorithms automatically and reuse experimental experience across branches.
- **[A-Evolve-Training](https://a-evo-lab.github.io/a-evolve-training/)** (2026 technical report/project): After humans construct and audit the initial substrate, an agent performs multiple rounds of post-training on a 30B model. It should be labeled a technical report rather than a peer-reviewed conference paper.
- **[autoresearch](https://github.com/karpathy/autoresearch)** (Karpathy, 2026 open-source project): An agent edits training code, runs experiments within a fixed time budget, and retains changes according to validation metrics. It is a clear L2/L4 engineering loop, but the improvement strategy, metric, and compute boundary are not invented autonomously by the system.

### 2.4 Formally Published 2026 Work on Self-Training, Prompts, Context, and Memory

- **[R-Zero: Self-Evolving Reasoning LLM from Zero Data](https://openreview.net/pdf?id=96apU6YzSO)** (ICLR 2026): A challenger generates tasks near the solver’s capability boundary, and the two are trained alternately. “Zero data” means that the post-training stage uses no human-created problems or labels; it does not mean that the base model was pretrained from scratch.
- **[Self-Evolving Curriculum for LLM Reasoning](https://www.microsoft.com/en-us/research/publication/self-evolving-curriculum-for-llm-reasoning/)** (COLM 2026): Models task-category selection as a non-stationary multi-armed bandit and dynamically adjusts the curriculum using immediate learning gains.
- **[Temporal Self-Rewarding Language Models](https://proceedings.mlr.press/v306/wang26ik.html)** (ICML 2026): Uses models from different points in training to generate chosen and rejected responses, mitigating the collapse of positive/negative margins over repeated self-rewarding rounds.
- **[GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning](https://proceedings.iclr.cc/paper_files/paper/2026/hash/0e9e708b6f48e14fd0ac29e167413f76-Abstract-Conference.html)** (ICLR 2026): Diagnoses problems through natural-language reflection on trajectories, tool calls, and outcomes, then evolves prompts with Pareto search. The authors report fewer rollouts than GRPO and higher performance on several tasks.
- **[Agentic Context Engineering (ACE)](https://openreview.net/pdf?id=eC4ygDs02R)** (ICLR 2026): Treats context as an evolving playbook, using generation, reflection, and curation mechanisms to reduce brevity bias and context collapse.
- **[Dynamic Cheatsheet](https://aclanthology.org/2026.eacl-long.333/)** (EACL 2026): Accumulates strategies, code snippets, and problem-solving experience at test time as persistent external memory without updating model weights.
- **Google Research — [ReasoningBank: Enabling agents to learn from experience](https://www.research.google/blog/reasoningbank-enabling-agents-to-learn-from-experience/)** (ICLR 2026 institutional article; [paper](https://arxiv.org/abs/2509.25140)): Distills transferable reasoning strategies from successful and failed trajectories and combines memory retrieval with test-time scaling.

### 2.5 AI Research: From Research Assistance to Closed-Loop Research

- **[Towards end-to-end automation of AI research](https://www.nature.com/articles/s41586-026-10265-5)** (Nature 2026): The formally peer-reviewed version of The AI Scientist, covering topic selection, experiments, figures, paper writing, and automated reviewing. It also discusses risks involving research quality, attribution, misuse, and the burden placed on peer review.
- **[An AI system to help scientists write expert-level empirical software](https://www.nature.com/articles/s41586-026-10658-6)** (ERA, Nature 2026): Uses LLMs and tree search to optimize quantifiable scientific software and reaches or exceeds strong baselines across multiple domains.
- **[Accelerating scientific discovery with Co-Scientist](https://doi.org/10.1038/s41586-026-10644-y)** (Nature 2026; [DeepMind overview](https://deepmind.google/blog/co-scientist-a-multi-agent-ai-partner-to-accelerate-research/)): Multiple specialized agents generate, reflect on, rank, and evolve scientific hypotheses, while experimental validation and research objectives remain led by human scientists.
- **[A multi-agent system for automating scientific discovery](https://www.nature.com/articles/s41586-026-10652-y)** (Robin, Nature 2026): Integrates literature retrieval, hypothesis generation, experimental suggestions, and data analysis into one biology workflow, making it a semi-autonomous discovery system.
- **[Reimagining research papers as interactive and reliable AI agents](https://www.nature.com/articles/s41586-026-11044-y)** (Paper2Agent, Nature 2026): Packages papers together with their code, data, and methods as interactive agents, reducing the cost of reusing research results.
- **Google DeepMind — [AlphaEvolve: impact across fields](https://deepmind.google/blog/alphaevolve-impact/)** (2026): Reports follow-on applications of AlphaEvolve in genomics, disaster risk, and computing infrastructure. Its core remains evolutionary search combining LLM-generated candidate programs with automated evaluators.

## 3. Foundation Model 

### 3.1 Architecture Search and Model Structure

| Question | Representative work | Method and significance |
|---|---|---|
| Can we search for alternatives to the Transformer architecture? | [The Evolved Transformer](https://proceedings.mlr.press/v97/so19a.html) (ICML 2019); [DARTS](https://openreview.net/forum?id=S1eYHoC5FX) (ICLR 2019) | The former uses evolutionary search with a Transformer warm start; the latter relaxes a discrete architecture space into a continuous one for gradient optimization. Both established foundations for NAS, although their search spaces remain human-defined. |
| Can LLMs directly generate architecture code? | [EvoPrompting](https://proceedings.nips.cc/paper_files/paper/2023/hash/184c1e18d00d7752805324da48ad25be-Abstract-Conference.html) (NeurIPS 2023); [LLMatic](https://doi.org/10.1145/3638529.3654017) (GECCO 2024) | Uses an LLM as a mutation/crossover operator or code generator, followed by evolutionary or quality-diversity selection. |
| Can depth, width, head count, and MLP ratio be tuned automatically? | [AutoFormer](https://arxiv.org/abs/2107.00651) (ICCV 2021); [NAS-BERT](https://arxiv.org/abs/2105.14444) (KDD 2021); [AutoTinyBERT](https://arxiv.org/abs/2107.13686) (ACL 2021) | Uses supernets and weight sharing to search depth, width, and submodule configurations under accuracy and cost constraints. |
| Can architectures be designed dynamically for hardware? | [HAT](https://aclanthology.org/2020.acl-main.686/) (ACL 2020); [Once-for-All](https://openreview.net/forum?id=HylxE1HKwS) (ICLR 2020); [LiteTransformerSearch](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9949e6906be6448230cdba9a4cb2d564-Abstract-Conference.html) (NeurIPS 2022) | Incorporates measured latency, memory, or parameter count into the search and extracts device-specific subnetworks from a supernet. |
| Can we close the propose–implement–train–analyze loop? | [ASI-Arch](https://arxiv.org/abs/2507.18074) (COLM 2026); [AIRA](https://arxiv.org/abs/2605.15871) (2026 preprint) | Extends NAS into agent-driven research loops, while keeping evaluators, task domains, and resource budgets fixed. |

### 3.2 Data Generation, Filtering, and Curricula

| Capability | Representative work | Key mechanism |
|---|---|---|
| Self-generation of reasoning/instruction data | [STaR](https://papers.neurips.cc/paper_files/paper/2022/hash/639a9a172c044fbb64175b5fad42e9a5-Abstract-Conference.html) (NeurIPS 2022); [Self-Instruct](https://aclanthology.org/2023.acl-long.754/) (ACL 2023); [WizardLM](https://proceedings.iclr.cc/paper_files/paper/2024/hash/82eec786fdfbbfa53450c5feb7d1ac92-Abstract-Conference.html) (ICLR 2024); [Magpie](https://proceedings.iclr.cc/paper_files/paper/2025/hash/be06e3802e9411381feece79b4d960c1-Abstract-Conference.html) (ICLR 2025) | Expands training data from a small number of seeds, the model’s own outputs, or an empty user turn. |
| Generation of verifiable hard problems | [Absolute Zero](https://papers.nips.cc/paper_files/paper/2025/hash/9837dc00ff67d176373268ed48042d49-Abstract-Conference.html) (NeurIPS 2025); [R-Zero](https://openreview.net/pdf?id=96apU6YzSO) (ICLR 2026) | Uses code executors or challenger–solver co-evolution to generate tasks near the capability boundary. |
| Filtering incorrect synthetic data | [ReST](https://arxiv.org/abs/2308.08998) (2023 preprint); [Re-ReST](https://aclanthology.org/2024.emnlp-main.861/) (EMNLP 2024) | Generate–filter–improve loops combine rewards, environment feedback, or a reflector to repair low-quality trajectories. |
| Dynamic adjustment of data distributions | [DoReMi](https://proceedings.neurips.cc/paper_files/paper/2023/hash/dcba6be91359358c2355cd920da3fcbd-Abstract-Conference.html) (NeurIPS 2023); [LESS](https://proceedings.mlr.press/v235/xia24c.html) (ICML 2024); [Self-Evolving Curriculum](https://www.microsoft.com/en-us/research/publication/self-evolving-curriculum-for-llm-reasoning/) (COLM 2026) | Uses proxy models, low-rank gradient similarity, or online learning gains to determine data weights and curricula. |

### 3.3 Optimizers, Objectives, and Training Pipelines

The core of this direction is not merely automatic hyperparameter tuning, but allowing agents to propose and validate new update rules, losses, rewards, or algorithm combinations.

- [Self-Taught Optimizer (STOP)](https://openreview.net/pdf?id=46Zgqo4QIU) (COLM 2024): Uses an LLM to write an “improver program,” then recursively asks that program to improve itself.
- [Self-Rewarding Language Models](https://proceedings.mlr.press/v235/yuan24d.html) (ICML 2024): The same model generates responses and produces preference signals as an LLM-as-a-Judge, enabling multiple rounds of DPO.
- [Temporal Self-Rewarding Language Models](https://proceedings.mlr.press/v306/wang26ik.html) (ICML 2026): Uses past and future model checkpoints to preserve an effective preference margin.
- [POISE](https://arxiv.org/abs/2603.23951), [MLEvolve](https://arxiv.org/abs/2606.06473), and [autoresearch](https://github.com/karpathy/autoresearch) (2026): Explore RL algorithm discovery, machine-learning algorithm discovery, and fixed-budget training-strategy search, respectively.

## 4. Evaluation and Reward Layer

### 4.1 Self-Evaluation, Peer Evaluation, and Self-Correction

| Task | Representative work | Boundary of the conclusion |
|---|---|---|
| Evaluate generated answers | [G-Eval](https://aclanthology.org/2023.emnlp-main.153/) (EMNLP 2023); [Self-Refine](https://proceedings.neurips.cc/paper_files/paper/2023/hash/91edff07232fb1b55a505a9e9f6c0ff3-Abstract-Conference.html) (NeurIPS 2023); [Prometheus](https://openreview.net/forum?id=8euJaTveKw) (ICLR 2024) | Model-based review is scalable, but judge bias, positional bias, and same-source bias may be amplified by the loop. |
| Generate rewards/preferences | [Constitutional AI](https://arxiv.org/abs/2212.08073); [RLAIF vs. RLHF](https://proceedings.mlr.press/v235/lee24t.html) (ICML 2024); [Self-Rewarding LM](https://proceedings.mlr.press/v235/yuan24d.html) (ICML 2024) | AI feedback can reduce human-labeling costs, but still relies on human-written principles, rubrics, or initial preferences. |
| Locate reasoning errors | [Math-Shepherd](https://aclanthology.org/2024.acl-long.510/) (ACL 2024); [SCoRe](https://proceedings.iclr.cc/paper_files/paper/2025/hash/871ac99fdc5282d0301934d23945ebaa-Abstract-Conference.html) (ICLR 2025); [ProcessBench](https://aclanthology.org/2025.acl-long.50/) (ACL 2025) | Externally verifiable feedback and on-policy training are usually more reliable than prompt-only “think again” methods. |
| Improve verifiers | [Generative Verifiers](https://proceedings.iclr.cc/paper_files/paper/2025/hash/214308a2d5e3f83ef9ad2739e1cbc46d-Abstract-Conference.html) (ICLR 2025); [Process-based Self-Rewarding](https://arxiv.org/abs/2503.03746) (2025) | Extends answer-level binary classification to generative, process-level verification and can use additional test-time compute. |

### 4.2 Major Failure Modes in Evaluation Loops

- **Reward hacking:** The ICML 2026 [Reward Hacking Benchmark](https://proceedings.mlr.press/v306/thaman26a.html) shows that tool-using agents may exploit shortcuts such as skipping validation, reading side-channel information, or tampering with evaluation functions.
- **Research agents directly attacking evaluation mechanisms:** [Reward Hacking Challenges Oversight of Autonomous Research Agents](https://www.microsoft.com/en-us/research/publication/reward-hacking-challenges-oversight-of-autonomous-research-agents/) (Microsoft Research, 2026) finds many evaluator exploits in settings where hacking is permitted and the threshold is high. It recommends keeping critical metrics outside agent control and recomputing them independently.
- **Noise, task order, and underspecification:** [On the Fragility of Self-Improving Agents](https://arxiv.org/abs/2608.18066) (2026 preprint) finds that gains from self-improvement may be highly sensitive to task order and randomness.
- **Benchmark contamination and poisoned evaluators:** [Reflections on Trusting Trust, Revisited](https://arxiv.org/abs/2609.17817) (2026 preprint) studies the possibility of contaminating self-modifying coding agents through poisoned benchmarks.

## 5. Agent Software

### 5.1 Tools and Skills

- [Toolformer](https://proceedings.neurips.cc/paper_files/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html) (NeurIPS 2023): Learns when and how to call tools through self-supervision.
- [Voyager](https://arxiv.org/abs/2305.16291) (TMLR 2024): Automatically generates, validates, and accumulates a library of code skills in Minecraft.
- [LLM Agents Making Agent Tools](https://aclanthology.org/2025.acl-long.1266/) (ACL 2025): ToolMaker automatically builds callable tools from paper repositories containing code and debugs them through execution feedback.

### 5.2 Harnesses and Agent Design

- [SWE-agent](https://papers.nips.cc/paper/2024/hash/5a7c947568c1b1328ccc5230172e1e7c-Abstract-Conference.html) (NeurIPS 2024): Demonstrates that the agent–computer interface itself significantly affects software-engineering performance.
- [Automated Design of Agentic Systems](https://proceedings.iclr.cc/paper_files/paper/2025/hash/36b7acf6f6010652b3f2a433774a66fe-Abstract-Conference.html) (ADAS, ICLR 2025): A meta-agent invents agent components and compositions through code search.
- [Gödel Agent](https://xunjianyin.github.io/papers/godel-agent.html) (ACL 2025): Allows an agent to inspect and rewrite its own task strategy and improvement logic; the authors also report degradation in some settings and overlapping confidence intervals.
- [Darwin Gödel Machine](https://openreview.net/pdf?id=98932dd098fa5b83419746439f3e35a4e3cf54a3.pdf) (ICLR 2026) and [Hyperagents](https://arxiv.org/abs/2603.19461) (2026 preprint): Move beyond fixed meta-agents toward editable, open-ended agent archives and meta-level programs.

### 5.3 Prompts, Context, and Memory

- [Promptbreeder](https://proceedings.mlr.press/v235/fernando24a.html) (ICML 2024): Co-evolves task prompts and the mutation prompts used to produce new prompts.
- [GEPA](https://proceedings.iclr.cc/paper_files/paper/2026/hash/0e9e708b6f48e14fd0ac29e167413f76-Abstract-Conference.html) (ICLR 2026): Optimizes multiple prompts in a compound AI system through trajectory reflection and Pareto search.
- [ACE](https://openreview.net/pdf?id=eC4ygDs02R) (ICLR 2026): Organizes context as an evolving playbook.
- [Reflexion](https://proceedings.neurips.cc/paper_files/paper/2023/hash/1b44b878bb782e6954cd888628510e90-Abstract-Conference.html) (NeurIPS 2023): Writes feedback from failures into episodic memory.
- [ExpeL](https://ojs.aaai.org/index.php/AAAI/article/view/29936) (AAAI 2024): Extracts general rules across tasks from successful and failed experiences.
- [MemGPT](https://openreview.net/forum?id=0Kk142lP62) (ICLR 2024): Manages limited context using hierarchical memory and explicit swapping.
- [Dynamic Cheatsheet](https://aclanthology.org/2026.eacl-long.333/) (EACL 2026) and [ReasoningBank](https://arxiv.org/abs/2509.25140) (ICLR 2026): Continuously accumulate reusable strategies without changing base-model weights.

## 6. AI Research Layer: What Should the System Complete?

A relatively complete automated research loop includes: literature retrieval → hypothesis generation → experiment design → code implementation → training and evaluation → result analysis → the next research strategy.

| System | Publication status | Scope |
|---|---|---|
| [The AI Scientist](https://www.nature.com/articles/s41586-026-10265-5) | Nature 2026 | End-to-end AI research, paper writing, and automated review; the formal version includes both template-based and open-ended modes. |
| [The AI Scientist-v2](https://arxiv.org/abs/2504.08066) | 2025 preprint; [official repository](https://github.com/SakanaAI/AI-Scientist-v2) | Removes human-written code templates and introduces progressive agentic tree search and an experiment manager. |
| [Agent Laboratory](https://aclanthology.org/2025.findings-emnlp.320/) | Findings of EMNLP 2025 | Literature review, experimentation, and report writing, with optional human feedback at intermediate stages. |
| [MLGym](https://openreview.net/pdf?id=ryTr83DxRq) | COLM 2025 | Measures hypothesis formation, coding, training, and analysis across multiple real machine-learning tasks. |
| [AlphaEvolve](https://arxiv.org/abs/2506.13131) | 2025 technical paper; [official overview](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/) | LLM program generation, automated evaluators, and evolutionary search for algorithms, mathematics, and infrastructure. |
| [ERA](https://www.nature.com/articles/s41586-026-10658-6) | Nature 2026 | Uses tree search to automatically produce high-quality, measurable scientific software. |
| [Co-Scientist](https://doi.org/10.1038/s41586-026-10644-y) | Nature 2026 | Multiple agents generate, debate, and evolve scientific hypotheses. |
| [Robin](https://www.nature.com/articles/s41586-026-10652-y) | Nature 2026 | A closed loop spanning biological literature, hypotheses, experimental suggestions, and data analysis. |

## 7. Conclusions as of 2026

1. **Established:** AI can continually improve prompts, context, tools, code, data curricula, training recipes, and local algorithms in spaces that are automatically scorable, quick to experiment in, and governed by clear objectives.
2. **Preliminarily established:** Agents can modify task-execution code and even the meta-level program responsible for proposing the next modification. DGM, Hyperagents, and AIDE² are important evidence in this direction.
3. **Not yet established:** Public evidence does not show that systems can, without human objectives or fixed evaluators, design and train broadly more capable successor foundation models across domains over long periods with stable, accelerating progress.
4. **The largest bottleneck is not whether a loop can run**, but whether evaluation is valid, improvements transfer, costs are sustainable, and the system is optimizing the real research objective rather than a proxy metric.
5. **Terminology should be used carefully:** A single round of model self-evaluation, multi-agent voting, or automated hyperparameter tuning should not be labeled strong RSI. More precise terms include self-refinement, test-time learning, self-training, agent evolution, automated AI R&D, and bounded recursive improvement.

## 8. Recommended Reading Order

1. Concepts and real-world boundaries: [Anthropic’s RSI report](https://www.anthropic.com/institute/recursive-self-improvement) → [Stanford AI Index 2026: Science](https://hai.stanford.edu/ai-index/2026-ai-index-report/science) → [METR’s independent assessment](https://metr.org/blog/2026-11-05-anthropic-ai-rd-acceleration-assessment/).
2. Outer-loop agent self-improvement: [STOP](https://openreview.net/pdf?id=46Zgqo4QIU) → [ADAS](https://proceedings.iclr.cc/paper_files/paper/2025/hash/36b7acf6f6010652b3f2a433774a66fe-Abstract-Conference.html) → [DGM](https://openreview.net/pdf?id=98932dd098fa5b83419746439f3e35a4e3cf54a3.pdf) → [Hyperagents](https://arxiv.org/abs/2603.19461) → [AIDE²](https://arxiv.org/abs/2609.26457).
3. Closed loops for model weights and training data: [STaR](https://papers.neurips.cc/paper_files/paper/2022/hash/639a9a172c044fbb64175b5fad42e9a5-Abstract-Conference.html) → [Self-Rewarding LM](https://proceedings.mlr.press/v235/yuan24d.html) → [Absolute Zero](https://papers.nips.cc/paper_files/paper/2025/hash/9837dc00ff67d176373268ed48042d49-Abstract-Conference.html) → [R-Zero](https://openreview.net/pdf?id=96apU6YzSO).
4. Automated research loops: [AI Scientist](https://www.nature.com/articles/s41586-026-10265-5) → [AlphaEvolve](https://arxiv.org/abs/2506.13131) → [ASI-Arch](https://arxiv.org/abs/2507.18074) → [AIRA](https://arxiv.org/abs/2605.15871) → [POISE](https://arxiv.org/abs/2603.23951).
5. Failure modes: [Reward Hacking Benchmark](https://proceedings.mlr.press/v306/thaman26a.html) → [Microsoft Research on reward hacking by research agents](https://www.microsoft.com/en-us/research/publication/reward-hacking-challenges-oversight-of-autonomous-research-agents/) → [On the Fragility of Self-Improving Agents](https://arxiv.org/abs/2608.18066).

## Citation and Maintenance Notes

- For formally published work, conference or journal pages are preferred; when no formal version is available, this page links to arXiv or the official project page.
- “2026” may refer to formal publication in 2026 even when the preprint first appeared in 2025. This document preserves both statuses rather than conflating them.
- Internal institutional data, product blogs, and technical reports are used to describe real-world deployment and trends, but cannot substitute for independent peer review or replication.
- Contributions that clarify publication status, reproduce experiments, document counterexamples, or report failures are welcome through issues and pull requests.

This repository is licensed under the [MIT License](LICENSE).


