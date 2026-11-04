# Hi, I'm Lichen 👋

**AI Infra · LLM 推理系统 · 投机解码 · GPU 性能实测**

香港大学人工智能硕士在读。比起标称值，我更关心推理系统的**实测数字**：
一张卡放不放得下、能扛多少并发、投机解码到底快多少、什么时候反而更慢。

*I build and benchmark LLM inference systems, and publish the numbers together with their limits.*

---

## 三个能复现的实验

每个仓库都带原始数据、脚本，以及一节「这些结论**不能**说明什么」。

| 仓库 | 硬件 | 做了什么 | 关键结果 |
|---|---|---|---|
| **[qwen27b-spec-decode-2x5090](https://github.com/lichen9240-creator/qwen27b-spec-decode-2x5090)** | 2×RTX 5090<br>TP=2 | Qwen3.8-27B-FP8 上 5 种投机解码路径 × **385 次真实请求** | DFlash2 C=1 **2.79×**；MTP3 C=8 **1.60×**；SUFFIX 冷启动仅 1.14×；EAGLE-4 两条路径均失败（保留报错原文，不编数据） |
| **[eagle3-qwen3-1.7b-repro](https://github.com/lichen9240-creator/eagle3-qwen3-1.7b-repro)** | 1×RTX 4090 | 从零训 EAGLE-3 draft：ShareGPT/UltraChat → 重生成 → 训练 → 部署 | vLLM + 长输出 **2.135×**（acceptance 2.89）；draft 已发布到 [HuggingFace](https://huggingface.co/Lichen-Creator/Qwen3-1.7B_eagle3) |
| **[llm-sizing-calculator](https://github.com/lichen9240-creator/llm-sizing-calculator)** | 浏览器 | 34 个开源模型的显存 / KV / TTFT / 吞吐测算，含 PD 分离与异构选卡 | 单文件 HTML、零依赖；对 7 个实测点 **MAPE 7.3%** |

> 共同的取舍：宁可写「这条没测出来」，也不拿估计值填空位。

---

## 工具

- **[llm-sizing-calculator](https://github.com/lichen9240-creator/llm-sizing-calculator)** ——
  输入模型 / 卡 / 负载，直接给出显存分解、四类瓶颈占比（显存 / 带宽 / 算力 / 卡间通信）、PD 配比建议，
  每条公式都摊开显示代入值。[在线即用](https://lichen9240-creator.github.io/llm-sizing-calculator/)。
- **[Practical-tools-AIresearch](https://github.com/lichen9240-creator/Practical-tools-AIresearch)** ——
  研究过程中攒的小工具。目前有 `Autodl-AutoConnect`：一条命令盯 AutoDL 空闲卡，
  带预算 / 单价护栏、幂等对账、`--json` 便于 Agent 接管。

## 笔记

**[AI-Infrastructure-Notes](https://github.com/lichen9240-creator/AI-Infrastructure-Notes)** ——
推理基础设施的自学笔记，论文与实测对照着写：

- [投机解码三大将：EAGLE-1 到 4 的变化哲学](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/speculative-decoding-overview.md)
- [DFlash 与 DSpark](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/dflash-and-dspark.md)
  · [EAGLE-4 与 Harness](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/eagle4-harness.md)
- [Prefill 与 Decode](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/01-LLM-Inference-Basics/prefill-and-decode.md)
  · [KV Cache](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/01-LLM-Inference-Basics/kv-cache.md)
  · [PD 分离](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/04-Distributed-Inference/pd-disaggregation.md)

---

## 技术栈

`Python` · `PyTorch` · `vLLM` · `SGLang` · `CUDA` · `Linux` · `Git`

动手过的：张量并行与 PD 分离部署、投机解码（MTP / EAGLE / DFlash / DSpark / SUFFIX）、
压测与指标口径（TTFT / TPOT / ITL / 接受率 / tok/W）、显存与带宽建模、消费级卡（4090 / 5090）调优。

## 交流

对推理性能、选型测算或投机解码有不同意见，欢迎直接在这些仓库里开 Issue —— 尤其是能推翻我结论的数据。
