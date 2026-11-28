# Quantized-rollout mismatch against a PyTorch bf16 reference: Qwen2.5-Coder-1.5B (Team 12 follow-up to #894)

**Scope and limits:** Qwen2.5-Coder-1.5B, Kaggle T4 x2, 8 rollouts per prompt, at most 256 new tokens, eps = 0.2, temperature = 1.0 (Team 10's defaults). Prompts: 50 from the fixed prompt file, selection `balanced` (10 english, 10 indic, 10 code, 10 tool_call, 10 reasoning). The sampler is vLLM (an unquantized model and a W4A16 GPTQ copy made with llm-compressor); the reference scores the same token ids in PyTorch (bfloat16 weights, fp32 logits, cuda, torch 2.11.0+cu126), the setup of `rl-loop/policy.py`. Intervals are 95% percentile intervals that resample prompts (the rollouts of a prompt are not independent). One seed, one model. Mean KL is not available in PyTorch mode (it needs the sampler's full distribution). Rollout tok/s is vLLM batched generation throughput (all prompts and samples at once), not single-stream decode speed; compare it only with the vLLM baseline row.

Reference model: `Qwen/Qwen2.5-Coder-1.5B@df3ce67c0e24480f20468b6ef2894622d69eb73b`. Notebook version `1f0a071bc0f2` (G12 `rollout_vllm.ipynb`). Source PRs: this work https://github.com/theschoolofai/era-v5-lab/pull/965; the baseline note https://github.com/saitej123/era-v5-lab/pull/190.

| Format | Tokens outside [0.8, 1.2] (below / above) | 95% interval | abs log-ratio p50 / p90 / p99 | k3 | k3 95% interval | Top-1 agreement | Rollout tok/s | Speed vs the vLLM baseline (same harness) |
|---|---:|---|---|---:|---|---:|---:|---:|
| `vllm_fp16` | **0.32%** (0.14% / 0.18%) | [0.18%, 0.48%] | 0.00771 / 0.0583 / 0.141 | **0.0008** | [0.0006, 0.0010] | 98.16% [97.83%, 98.49%] | 2682.6 | 1.00x |
| `vllm_W4A16` | **39.68%** (24.48% / 15.19%) | [36.37%, 43.06%] | 0.122 / 0.786 / 2.29 | **0.1186** | [0.1007, 0.1375] | 83.28% [81.14%, 85.37%] | 2808.6 | 1.05x |

## By prompt category (PyTorch reference; prompts per category in the header; intervals resample the prompts of that category)

| Format | code: outside / k3 / top-1 | english: outside / k3 / top-1 | indic: outside / k3 / top-1 | reasoning: outside / k3 / top-1 | tool_call: outside / k3 / top-1 |
|---|---|---|---|---|---|
| `vllm_fp16` | 0.01% / 0.0004 / 98.82% | 0.04% / 0.0006 / 97.94% | 1.05% / 0.0018 / 96.99% | 0.04% / 0.0003 / 99.56% | 0.19% / 0.0007 / 97.25% |
| `vllm_W4A16` | 34.13% / 0.0860 / 88.34% | 39.54% / 0.0683 / 85.96% | 57.44% / 0.2223 / 71.46% | 26.78% / 0.0930 / 90.43% | 37.58% / 0.0971 / 82.34% |

Each category has few prompts (10 at a balanced 50), so these cells are noisier than the pooled table; the intervals are in `torch_reference.json` (`by_category`).

**Reading the table**
- The `vllm_fp16` row has no quantization in it: vLLM's unquantized model (fp16 on a T4) against the PyTorch reference. It is the engine-to-engine floor (0.32% of tokens outside, k3 0.0008); a quantized row's excess over it is the quantization part.
- The speed column divides a format's rollout tok/s by the `vllm_fp16` sampler's tok/s from the same run and session. It is not a speedup against PyTorch bf16 decoding, which was not measured.
- Team 10's stop rule (`k3 <= 0.05`), on the pooled k3 with its interval: under the limit: `vllm_fp16`; interval contains the limit: none; above the limit: `vllm_W4A16`.
