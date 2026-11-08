# Hi, I'm Lichen 👋

**AI Infra · LLM 推理系统 · 投机解码 | Training / Architecture / Systems**

香港大学人工智能硕士在读，持续探索大模型从训练、架构到推理部署的完整链路。

我喜欢把论文里的想法变成真实跑起来的系统，再用实验数据验证它究竟有没有用。比起标称性能，我更关心一些实际问题：

- 📦 一张 GPU 到底能装下多大的模型？
- 🚦 推理服务能承受多少并发？瓶颈究竟在计算、显存还是通信？
- 🧠 KV Cache 如何管理和传输，才能让显存利用率更高？
- 🧩 PD Disaggregation 在真实部署中能带来多少收益？
- ⚡ 投机解码什么时候能加速，什么时候反而会更慢？

## 🔬 What I'm Exploring

- **LLM Inference Optimization** — vLLM、SGLang、Continuous Batching、Scheduler、算子与推理性能优化
- **KV Cache & Memory Management** — PagedAttention、Prefix Caching、KV Cache Offloading、Cache Transfer
- **Disaggregated Serving** — Prefill-Decode Disaggregation（PD 分离）、异构 GPU 部署与通信优化
- **Speculative Decoding** — EAGLE-3/4、MTP、DFlash、DSpark，以及 Draft Model 的训练与推理优化
- **LLM Training & Architecture** — Draft Training、Hidden-state Alignment、Multi-layer Feature Fusion、Tree Attention

---

## 🧪 三个能复现的实验

每个仓库都带原始数据、脚本，以及一节「这些结论**不能**说明什么」。

| 仓库 | 硬件 | 做了什么 | 关键结果 |
|---|---|---|---|
| **[qwen27b-spec-decode-2x5090](https://github.com/lichen9240-creator/qwen27b-spec-decode-2x5090)** | 2×RTX 5090<br>TP=2 | Qwen3.8-27B-FP8 上 5 种投机解码路径 × **385 次真实请求** | DFlash2 C=1 **2.79×**；MTP3 C=8 **1.60×**；SUFFIX 冷启动仅 1.14×；EAGLE-4 两条路径均失败（保留报错原文，不编数据） |
| **[eagle3-qwen3-1.7b-repro](https://github.com/lichen9240-creator/eagle3-qwen3-1.7b-repro)** | 1×RTX 4090 | 从零训 EAGLE-3 draft：ShareGPT/UltraChat → 重生成 → 训练 → 部署 | vLLM + 长输出 **2.135×**（acceptance 2.89）；draft 已发布到 [HuggingFace](https://huggingface.co/Lichen-Creator/Qwen3-1.7B_eagle3) |
| **[llm-sizing-calculator](https://github.com/lichen9240-creator/llm-sizing-calculator)** | 浏览器 | 34 个开源模型的显存 / KV / TTFT / 吞吐测算，含 PD 分离与异构选卡 | 单文件 HTML、零依赖；对 7 个实测点 **MAPE 7.3%** |

> 共同的取舍：宁可写「这条没测出来」，也不拿估计值填空位。

---

## 🛠️ How I Learn & Build

我倾向于通过完整的实验链路学习技术：

**Read Papers → Reproduce → Deploy → Benchmark → Analyze → Improve → Experiments → Report**

关注的不只是某个方法的最高加速比，还包括硬件条件、请求分布、并发规模、显存开销和性能边界。

目前也在持续积累 GPU 部署、推理压测、投机解码训练与性能对比方面的实践，希望逐渐从复现已有方案，走向真正理解系统并参与底层优化。

---

## 🧰 工具

- **[llm-sizing-calculator](https://github.com/lichen9240-creator/llm-sizing-calculator)** ——
  输入模型 / 卡 / 负载，直接给出显存分解、四类瓶颈占比（显存 / 带宽 / 算力 / 卡间通信）、PD 配比建议，
  每条公式都摊开显示代入值。[在线即用](https://lichen9240-creator.github.io/llm-sizing-calculator/)。
- **[Practical-tools-AIresearch](https://github.com/lichen9240-creator/Practical-tools-AIresearch)** ——
  研究过程中攒的小工具。目前有 `Autodl-AutoConnect`：一条命令盯 AutoDL 空闲卡，
  带预算 / 单价护栏、幂等对账、`--json` 便于 Agent 接管。

## 📝 笔记

**[AI-Infrastructure-Notes](https://github.com/lichen9240-creator/AI-Infrastructure-Notes)** ——
推理基础设施的自学笔记，论文与实测对照着写：

- [投机解码三大将：EAGLE-1 到 4 的变化哲学](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/speculative-decoding-overview.md)
- [DFlash 与 DSpark](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/dflash-and-dspark.md)
  · [EAGLE-4 与 Harness](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/eagle4-harness.md)
- [Prefill 与 Decode](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/01-LLM-Inference-Basics/prefill-and-decode.md)
  · [KV Cache](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/01-LLM-Inference-Basics/kv-cache.md)
  · [PD 分离](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/04-Distributed-Inference/pd-disaggregation.md)

---

## ⚙️ 技术栈

`Python` · `PyTorch` · `vLLM` · `SGLang` · `CUDA` · `Linux` · `Git`

动手过的：张量并行与 PD 分离部署、投机解码（MTP / EAGLE / DFlash / DSpark / SUFFIX）、
压测与指标口径（TTFT / TPOT / ITL / 接受率 / tok/W）、显存与带宽建模、消费级卡（4090 / 5090）调优。

---

## 🎾 Beyond the Terminal

技术之外，我也喜欢运动和户外：

- ⛷️ Skiing — 喜欢速度、平衡，以及不断挑战自己的感觉。
- 🏸 Badminton — 反应、节奏和一点点策略。
- 🎾 Tennis — 享受每一次多拍相持。

我相信技术探索和运动有些相似：保持好奇，持续练习，在一次次反馈中变得更好。

---

## 💬 交流

对推理性能、选型测算或投机解码有不同意见，欢迎直接在这些仓库里开 Issue —— 尤其是能推翻我结论的数据。

*I build, benchmark, and optimize LLM inference systems. I enjoy digging into the details behind performance numbers — from GPU memory and KV Cache to speculative decoding and distributed serving.*

**Always curious. Always building.**
