# LLM-SOC-Alert-Analysis-Survey

## 📖 仓库简介
本仓库致力于收集、整理和归档“基于大模型与多智能体架构的SOC网络告警关联溯源与研判系统”项目前期的所有调研资料。本项目旨在探索如何利用大模型的自然语言理解与推理能力，结合多智能体分工协作机制，解决传统SOC中海量告警疲劳、关联分析弱、溯源链路断层等痛点。


## 📂 目录结构
* **`01_Industry_Reports/`** (行业报告与现状)
* **`02_Academic_Papers/`** (学术论文与前沿研究)
* **`03_Technical_Solutions/`** (技术方案与开源框架)
* **`04_Knowledge_Base/`** (安全知识与情报源)
* **`05_Alert_Datasets/`** (安全告警数据集)

---

## 01. 行业报告与现状 (Industry Reports)


## 02. 学术论文与前沿研究 (Academic Papers)

### [NDSS 2026] Incident Response Planning Using a Lightweight Large Language Model with Reduced Hallucination

链接：https://www.ndss-symposium.org/ndss-paper/incident-response-planning-using-a-lightweight-large-language-model-with-reduced-hallucination

摘要：及时有效的事件响应是应对日益频繁的网络攻击的关键。然而，为复杂系统确定正确的响应措施是一项重大技术挑战。缓解这一挑战的一种有前景的方法是利用大语言模型中嵌入的安全知识，在事件处理过程中协助安全运营人员。近期研究已经证明了这种方法的潜力，但当前方法主要基于前沿大语言模型的提示工程，成本高昂且容易产生幻觉。我们提出一种新的方法，以减少幻觉的方式使用大语言模型进行事件响应规划，从而解决这些局限性。我们的方法包括三个步骤：微调、信息检索和前瞻性规划。我们证明，我们的方法生成的响应计划产生幻觉的概率是有界的，并且在某些假设下，以增加规划时间为代价，该概率可以任意小。此外，我们表明我们的方法轻量级，可以在普通硬件上运行。我们根据文献中报道的事件日志对我们的方法进行评估。实验结果表明，我们的方法：a）与前沿大语言模型相比，恢复时间最多可缩短22%；b）适用于广泛的事件类型和响应措施。 

### [Arxiv 2025] CORTEX: Collaborative LLM Agents for High-Stakes Alert Triage

链接：https://arxiv.org/abs/2510.00311

摘要：安全运营中心（SOC）每天被数以万计的警报淹没，其中仅有一小部分对应真正的攻击。这种过载引发了警报疲劳，导致威胁被忽视以及分析师倦怠。经典检测管道脆弱且缺乏上下文，而近期基于大语言模型（LLM）的方法通常依赖单一模型来解释日志、检索上下文并端到端地判定警报——这种方法难以应对噪声较大的企业数据，且透明度有限。我们提出了 CORTEX，这是一种用于高风险警报筛选的多智能体 LLM 架构，其中专用智能体基于真实证据进行协作：行为分析智能体检查活动序列，证据收集智能体查询外部系统，推理智能体将发现综合为可审计的决策。为了支持训练和评估，我们发布了一个来自生产环境的细粒度 SOC 调查数据集，捕获了逐步的分析师操作及关联的工具输出。在多样的企业场景中，相较于最先进的单智能体 LLM，CORTEX 大幅减少了误报并提高了调查质量。

### [NDSS 2026 Workshop] Experiences of Using Agentic AI to Fill Tooling Gaps in a Security Operations Center

链接：https://www.ndss-symposium.org/ndss-paper/auto-draft-735

摘要：大语言模型（LLM）正引起安全运营中心（SOC）的关注，但其实际价值与局限性仍有待深入探索。在本研究中，网络安全研究人员以初级 SOC 分析师的身份嵌入某大学 SOC，通过观察日常 workflows，探讨 LLM 如何融入现有的 SOC 实践。我们观察到，分析师经常需要处理大量类似的警报，并手动在异构且分散的工具之间进行切换和关联分析——这些工具包括安全信息与事件管理系统（SIEM）、开源情报（OSINT）服务以及内部安全工具。虽然每个工具都能为工单提供部分所需的分析内容，但它们无法轻易协同工作以解决工单，往往需要人工努力来整合来自不同工具的结果。这种工具间的割裂导致了重复且耗时的 workflow，不仅拖慢了调查速度，还加剧了分析师的倦怠感。基于上述观察，我们设计并实现了一个由 LLM 驱动的 ReAct 智能体，旨在统一这些分散的工具，并自动化常规的筛选任务，如日志检索、信息增强、分析及报告生成。我们在真实的 SOC 工单上对该系统进行了评估，并将该智能体的表现与人工分析师的 workflow 进行了对比。此外，我们还实验了如何通过迭代提示（iterative prompting）和额外的分析师指令来优化智能体的推理能力并提升响应质量。结果表明，我们的智能体能够有效复现多种常规分析师行为，减少人工工作量，并展示了人机协作在简化 operational SOC 环境中警报筛选流程方面的潜力。

## 03. 技术方案与开源框架 (Technical Solutions)

### [Github] Agentic SOC Platform

链接：https://github.com/FunnyWolf/agentic-soc-platform

简介：Agentic SOC Platform 是一个开源的、以 AI 智能体为中心的自动化安全运营平台，旨在将人工智能代理（AI Agents）能力与安全事件管理和响应自动化紧密结合，通过 Webhook 与主流 SIEM 平台集成，采用流式消息队列（如 Redis）处理安全告警，利用内置的 AI 模板对告警进行分析、富化和响应，并提供可本地部署的 SIRP 平台、丰富的模块和插件支持，从而帮助安全团队高效地检测威胁、调查事件并自动执行响应策略，同时保持企业对数据和流程的控制权。

### [Github] DeepSOC

链接：https://github.com/flagify-com/deepsoc

简介：DeepSOC 是一个革命性的安全运营解决方案，它将先进的 AI 技术与传统的安全运营工具完美结合，通过多智能体（Multi-Agent）架构，DeepSOC 能够自动化处理安全事件，显著提升安全运营效率。

### [Github] Agentic SOC Parallel Simulation

链接：https://github.com/SafelineMan/Agentic-SOC-Simulation

简介：Agentic SOC Parallel Simulation 是一个前沿的 Agentic SOC 平行仿真平台，旨在探索 Large Action Model (LAM) 在网络安全领域的极限潜力。通过集成 DeepSeek 强推理引擎、多智能体协同 (Multi-Agent Collaboration) 与 MCP (Model Context Protocol) 标准，我们构建了一个全栈式、全流程、全自动的虚拟 SOC 团队。在这里，AI 不再是简单的脚本执行者，而是具备专家级思维链 (Chain of Thought) 的数字分析师。从紫队生成攻击流量，到蓝队开发检测规则，再到运营团队的分诊、取证与响应，七大智能体在平行空间中自主演练、自我进化。它能够像人类专家一样，从海量数据中抽丝剥茧，构建动态攻击图谱，并果断采取行动，将安全运营的效率与智能化水平提升至新的维度。

## 04. 安全知识图谱与情报源 (Knowledge Base)

### [Github] IR Playbooks

链接：https://github.com/socfortress/Playbooks

简介：IR Playbooks 是一个面向安全运营中心（SOC）分析师的开源仓库，它收集并组织了一系列完整的 事件响应（Incident Response）剧本与工作流程，每个剧本按照 NIST 800‑61 r2 规范划分成六大部分，从事件准备、检测分析，到遏制根除和事后活动，提供详细步骤和模板文档，帮助团队定义资产、检测策略、响应措施、沟通计划等内容，同时也包含各种具体攻击类型的 Playbook 目录及可用于审计的 PDF/Excel 模板，是用于建立、共享和复用标准化 SOC 实践方案的资源库。

### [Github] SOC Resources

链接：https://github.com/0XAl3aref/Soc.Team.Resources

简介：是一个为安全运营中心（SOC）分析师和威胁狩猎实践者整理的资源库，旨在帮助从初学者到高级从业者提升检测和分析能力，通过收集和分类大量实用链接与工具，包括在线威胁监控站点、恶意软件样本库、SIEM/KQL/SPL 查询资源、威胁狩猎规则、日志分析网站、学习课程以及相关安全新闻网站等内容，使 SOC 团队在进行网络威胁识别、检测规则构建和深度狩猎时有便捷的参考与入口。项目按类别组织这些资源，覆盖从信誉查询、沙箱分析、IOC 工具到专业博客与教程等多方面内容，是一个帮助提升 SOC 日常工作效率的综合性资源集合库。

### [Github] DeepSec 语料库

链接：https://github.com/deepsec-top/deepsec

简介：本仓库为 DeepSec 项目托管的开源中文网络安全运营语料库，包含原始语料文件、处理脚本和处理后的输出数据，旨在支持安全运营场景下的大模型训练。


## 05. 安全告警数据集 (Alert Datasets)

### CIC-IDS-2017

链接：https://www.unb.ca/cic/datasets/ids-2017.html

简介：CIC‑IDS‑2017 数据集是由加拿大网络安全研究所（Canadian Institute for Cybersecurity, CIC）与加拿大通信安全机构（CSE）合作构建的网络入侵检测评估数据集，用于网络安全研究，特别是入侵检测系统（IDS）与机器学习模型的训练与评估。该数据集在一个受控网络环境中进行了为期五天（2017 年 7 月 3 日至 7 日）的网络数据捕获，包含真实的正常（良性）流量和多种常见攻击场景（如 FTP 与 SSH 暴力破解、DoS / DDoS、Web 攻击、Heartbleed 漏洞利用、渗透与僵尸网络行为等），并以 PCAP 原始包及通过 CICFlowMeter 提取的流（flow）级特征的 CSV 形式提供，同时对每个样本进行了标注，适合用于流量分析、异常检测、机器学习分类等研究任务。这个数据集因流量多样性和接近真实世界特征而成为入侵检测与网络安全研究的基准数据集。

### AIT Log Data Set V2.0

链接：https://zenodo.org/records/5789064

简介：AIT Log Data Set V2.0 是一套由奥地利技术研究院（Austrian Institute of Technology, AIT）发布的用于入侵检测系统（IDS）评估的合成日志与网络数据集，它通过构建小型企业网络测试环境模拟正常用户行为并注入多步骤攻击，并从所有主机收集系统日志、应用日志、网络流量包捕获（PCAP）、认证与安全事件、DNS、VPN 等多种来源的数据，同时提供对应的攻击标注，用以评估日志分析、异常检测、协同 IDS、告警相关性与 IDS 性能等研究。该“V2.0 版本”相比早期版本包含更复杂的网络拓扑、更丰富的行为模式及多类型日志数据，并支持细粒度标注以便在机器学习/IDS 研究中作为基准数据集使用。

### CSLE‑IDS‑2024

链接：https://zenodo.org/records/10706475

简介：CSLE‑IDS‑2024 数据集 是一套用于入侵检测与响应研究的网络安全日志与事件数据集，由 Kim Hammar 和 Rolf Stadler 等人在 2024 年发布，作为他们关于网络系统容错与入侵响应研究的补充材料之一。该数据集包含从受控实验环境中记录的大量入侵事件痕迹（JSON 格式的攻防日志、SNORT 告警统计等）以及辅助统计文件、系统配置代码与容器镜像等，可用于分析多种攻击行为（例如 SAMBACRY、SHELLSHOCK 漏洞利用等）在真实系统运行中的痕迹，从而支持入侵检测系统（IDS）、响应自动化或安全运营（SOC）相关的评估与模型训练。