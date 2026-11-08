<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F3D5C,100:0B1020&height=200&section=header&text=Lichen&fontSize=54&fontColor=ffffff&animation=fadeIn&fontAlignY=34&desc=LLM%20inference%20systems%20%C2%B7%20speculative%20decoding%20%C2%B7%20GPU%20sizing&descSize=16&descAlignY=57" width="100%" alt="Lichen" />

<a href="https://github.com/lichen9240-creator"><img src="https://readme-typing-svg.demolab.com/?font=JetBrains+Mono&size=18&duration=2800&pause=900&color=58A6FF&center=true&vCenter=true&width=780&height=46&lines=Reproducing+EAGLE-3+from+scratch+on+one+4090;Measuring+speculative+decoding+on+2%C3%97+RTX+5090;34+models+%C2%B7+KV+cache+%C2%B7+PD+disaggregation;Keeping+the+runs+that+failed%2C+too" alt="Typing SVG" /></a>

<br/>

<a href="https://huggingface.co/Lichen-Creator/Qwen3-1.7B_eagle3"><img src="https://img.shields.io/badge/HuggingFace-EAGLE--3%20draft-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" alt="HuggingFace" /></a>
<a href="https://lichen9240-creator.github.io/llm-sizing-calculator/"><img src="https://img.shields.io/badge/Live%20demo-Sizing%20calculator-2E7D6F?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Live demo" /></a>
<img src="https://img.shields.io/badge/Based%20in-Shenzhen%20%7C%20Hong%20Kong-0F3D5C?style=for-the-badge" alt="Location" />
<img src="https://img.shields.io/badge/Open%20to-AI%20Infra%20internships-2F6F3E?style=for-the-badge" alt="Open to AI Infra internships" />

<br/><br/>

<i>👋 MSc in AI @ HKU. I reproduce inference systems on consumer GPUs, measure them honestly,<br/>and publish the runs that did <b>not</b> work out.</i>

</div>

## 🧭 What I work on

- ⚡ **Speculative decoding** — EAGLE-3/4, MTP, DFlash2, DSpark, SUFFIX: when it pays, and when it silently loses.
- 🧠 **KV cache & memory** — PagedAttention, prefix caching, and the KV budget hiding behind every speedup number.
- 🧩 **Disaggregated serving** — prefill/decode split, heterogeneous GPUs, and what a KV transfer really costs.
- 📐 **Capacity & sizing** — turning *"4 req/s at P95 16K"* into cards, concurrency limits and a monthly bill.
- 🧪 **Honest benchmarking** — TTFT / TPOT / goodput, cold vs warm cache, and why a median can lie to you.

<br/>

<table>
<tr>
<td width="50%" valign="top">
<h3>🎯 <a href="https://github.com/lichen9240-creator/qwen27b-spec-decode-2x5090">qwen27b-spec-decode-2x5090</a></h3>
<p>Five speculative-decoding paths on Qwen3.8-27B-FP8 · 2× RTX 5090 · TP=2 · 385 real runs</p>
<p>DFlash2 <b>2.79×</b> at C=1 · MTP3 <b>1.60×</b> at C=8 · SUFFIX cold start <b>1.14×</b> · EAGLE-4 failed on both paths, error logs kept</p>
<a href="https://github.com/lichen9240-creator/qwen27b-spec-decode-2x5090/stargazers"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2Flichen9240-creator%2Fqwen27b-spec-decode-2x5090&amp;query=%24.stargazers_count&amp;label=Stars&amp;color=E3B341&amp;style=flat&amp;cacheSeconds=300" alt="stars" /></a>
<img src="https://img.shields.io/badge/vLLM-0.32.0-3B6EA5?style=flat" alt="vLLM" />
</td>
<td width="50%" valign="top">
<h3>🦅 <a href="https://github.com/lichen9240-creator/eagle3-qwen3-1.7b-repro">eagle3-qwen3-1.7b-repro</a></h3>
<p>Training an EAGLE-3 draft from zero on a single RTX 4090 · data → regeneration → training → SGLang vs vLLM</p>
<p><b>2.135×</b> with vLLM and 1024-token outputs, acceptance <b>2.89</b> · draft released on <a href="https://huggingface.co/Lichen-Creator/Qwen3-1.7B_eagle3">HuggingFace</a></p>
<a href="https://github.com/lichen9240-creator/eagle3-qwen3-1.7b-repro/stargazers"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2Flichen9240-creator%2Feagle3-qwen3-1.7b-repro&amp;query=%24.stargazers_count&amp;label=Stars&amp;color=E3B341&amp;style=flat&amp;cacheSeconds=300" alt="stars" /></a>
<img src="https://img.shields.io/badge/SGLang%20%7C%20vLLM-0.5.9%20%7C%200.11.2-3B6EA5?style=flat" alt="engines" />
</td>
</tr>
<tr>
<td width="50%" valign="top">
<h3>📐 <a href="https://github.com/lichen9240-creator/llm-sizing-calculator">llm-sizing-calculator</a></h3>
<p>34 open models · memory / KV / TTFT / TPOT / throughput · monolithic and PD disaggregated</p>
<p>Single-file HTML, zero dependencies · <b>MAPE 7.3%</b> against 7 measured points · <a href="https://lichen9240-creator.github.io/llm-sizing-calculator/">try it in the browser</a></p>
<a href="https://github.com/lichen9240-creator/llm-sizing-calculator/stargazers"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2Flichen9240-creator%2Fllm-sizing-calculator&amp;query=%24.stargazers_count&amp;label=Stars&amp;color=E3B341&amp;style=flat&amp;cacheSeconds=300" alt="stars" /></a>
<img src="https://img.shields.io/badge/license-MIT-2F6F3E?style=flat" alt="MIT" />
</td>
<td width="50%" valign="top">
<h3>🧰 <a href="https://github.com/lichen9240-creator/Practical-tools-AIresearch">Practical-tools-AIresearch</a></h3>
<p>Small tools that remove one annoying step each — starting with a one-command AutoDL GPU grabber</p>
<p>Budget and price guard-rails, idempotent reconciliation, <code>--json</code> output so an agent can take over</p>
<a href="https://github.com/lichen9240-creator/Practical-tools-AIresearch/stargazers"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2Flichen9240-creator%2FPractical-tools-AIresearch&amp;query=%24.stargazers_count&amp;label=Stars&amp;color=E3B341&amp;style=flat&amp;cacheSeconds=300" alt="stars" /></a>
<img src="https://img.shields.io/badge/python-3.10%2B-3B6EA5?style=flat" alt="python" />
</td>
</tr>
</table>

## 🧾 Receipts, not adjectives

Anyone can publish a speedup. Here is what each repo gives you to check it:

- 📦 **Raw runs** — 385 real requests with a `phase` column, 34 fields per run, so every number is traceable.
- 🔁 **Recomputable tables** — `python scripts/reproduce_tables.py --check` rebuilds all reported tables from the CSVs **without a GPU**: 12 checks, 0 failures.
- 🙅 **Failed paths stay in** — EAGLE-4 crashed on both the official and harness paths; the error text is in `logs/`, no estimated numbers in its place.
- 🧯 **Explicit non-claims** — every repo has a *what these numbers do NOT prove* section: sampling variance, weak quality checks, single-machine runs.

## 🔬 How I work

**Read the paper → reproduce it → deploy it → benchmark it → explain the gap → write it down**

I care less about the best-case speedup than about the conditions it needs: request distribution, concurrency, KV pressure, and where the whole thing quietly stops paying off.

## 🛠️ Tech stack

<p>
<img src="https://skillicons.dev/icons?i=py,pytorch,linux,bash,git,docker,vscode" alt="Tech stack" />
</p>

`vLLM` · `SGLang` · `CUDA` · `tensor parallelism` · `PD disaggregation` · `speculative decoding` · `TTFT / TPOT / goodput` · `4090 / 5090 tuning`

## 📈 GitHub in numbers

<table>
<tr>
<td colspan="2"><img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=lichen9240-creator&amp;theme=github_dark" alt="Profile summary" width="100%" /></td>
</tr>
<tr>
<td width="50%"><img src="https://streak-stats.demolab.com/?user=lichen9240-creator&amp;theme=github-dark-blue&amp;hide_border=true" alt="Contribution streak" width="100%" /></td>
<td width="50%"><img src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=lichen9240-creator&amp;theme=github_dark" alt="Most commit language" width="100%" /></td>
</tr>
</table>

<p align="center">
<img src="https://img.shields.io/github/stars/lichen9240-creator?affiliations=OWNER&amp;style=for-the-badge&amp;label=total%20stars&amp;color=E3B341" alt="Total stars" />
<img src="https://img.shields.io/github/followers/lichen9240-creator?style=for-the-badge&amp;color=58A6FF" alt="Followers" />
<img src="https://img.shields.io/github/last-commit/lichen9240-creator/qwen27b-spec-decode-2x5090?style=for-the-badge&amp;label=last%20push" alt="Last commit" />
</p>

## ✍️ Writing

Notes in [AI-Infrastructure-Notes](https://github.com/lichen9240-creator/AI-Infrastructure-Notes), written next to the experiments (*in Chinese*):

- 🪶 [Speculative decoding: the philosophy behind EAGLE-1 → EAGLE-4](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/speculative-decoding-overview.md)
- 🌀 [DFlash and DSpark](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/dflash-and-dspark.md) · [EAGLE-4 and the Harness](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/02-Inference-Optimization/speculative-decoding/eagle4-harness.md)
- 🧱 [Prefill vs Decode](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/01-LLM-Inference-Basics/prefill-and-decode.md) · [KV Cache](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/01-LLM-Inference-Basics/kv-cache.md) · [PD disaggregation](https://github.com/lichen9240-creator/AI-Infrastructure-Notes/blob/main/04-Distributed-Inference/pd-disaggregation.md)

## 🎾 Off the clock

⛷️ **Skiing** — speed, balance, and the honest feedback of a slope.
🏸 **Badminton** — reflexes, rhythm, a little strategy.
🎾 **Tennis** — I play for the long rallies.

## 💬 Say hi

If you have data that breaks one of my conclusions, please open an issue — that is the most useful thing you can send me.

📧 **2439068049@qq.com**

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F3D5C,100:0B1020&height=110&section=footer" width="100%" alt="" />

</div>
