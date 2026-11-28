# Team 10 Written Data Request to Teams 1 (Data A) and 2 (Data B) — Lab 5

Prepared for **Team 1 (Data A)** and **Team 2 (Data B)** per TSAI Lab 5 Design Task 0 (due Sunday 29 Nov 2026; full Lab 5 evidence due Wed 2 Dec, 7:00 AM IST). All paths are under `teams/10-post-training/`.

---

## 1. Contract & Format Requirements (Public Formats and Checks)

Every candidate SFT or RL dataset handed from Teams 1 & 2 to Team 10 must satisfy:
- **Delivery format:** Parquet (`*.parquet`) with a corresponding `pack_table` row (source ID, HF repo/revision commit SHA, row count, token count on frozen `p1536`, licence, generator model + licence, and SHA-256).
- **Tokenizer pin:** Team 3 frozen `p1536` (`tokenizer.json` sha256 `e6b93a93a60520d7b1af2e9242485f443b5596a1e116b8f8798d83bbad25a64b`).
- **Cleaning & F2 checks:**
  - Strip invisible zero-width junk (`U+200B`, `U+FEFF`) and upstream chat ghost markers (`[INST]`, `[/INST]`, `<think>`, `### Assistant:`).
  - **Do NOT apply NFKC** to content; **preserve `ZWJ` (`U+200D`) and `ZWNJ` (`U+200C`)** verbatim for Indic scripts.
  - Pass F2 contamination/integrity checks and Team 9 `decontam_check.py` (fingerprints v2, `set_sha256` `2826a3b883210c653979103c09ce1c79e40fc4f7034b54027f2836482370d22a`) + `canary_scan.py` with **0 flagged** rows.
- **Licence & generator rule (`licences/licence_table.md` — TSAI 28 Nov rule):**
  - **NC, ND and unstated licences are allowed** for all data, post-training data included (TSAI 28 Nov Lab Rules #1).
  - For every source, record the **licence** and **where you found it**; if a model made the data, also record the **generator model** and the **licence terms of that model**.
  - **Benchmark exclusion:** Do not stage benchmark datasets as training data (`rl-math-hendrycks` excluded 21 Nov; HellaSwag excluded 28 Nov due to wikiHow DMCA takedown HTTP 451).

---

## 2. SFT Instruction Data Request (Stage 1 — Base to Chat)

Target schema: chat messages JSON/Parquet (`messages: [{role, content, think?, tool_calls?}]`, optional `tools`, `effort`, `language`, `source_id`) convertible by `teams/10-post-training/sft/convert.py` into ChatML `v0` with assistant-only loss masks (`1` on `assistant` turns, `0` on `system`/`user`/`tool`).

| # | Domain | Target Share | Requested Volume (Rows / Tokens) | Target Team | Candidate Sources (`licences/licence_table.md`) | Quality Filter |
|---|---|---:|---|---|---|---|
| 1 | **Code** | 35% | ~400k–600k rows (~2.5B tok) | Team 1 | `nvidia/OpenCodeReasoning` & `OpenCodeReasoning-2` (`pass_rate == 1.0`, firewalled), `open-r1/codeforces-cots`, `bigcode/commitpackft` | Execution-verified (`pass_rate=1.0`), `<= 32,768` tok, eval-firewall applied against RL & effort suites |
| 2 | **Agentic (SWE / Terminal)** | 25% | ~100k–250k trajectories (~1.5B tok) | Team 1 | `nebius/SWE-rebench-openhands-trajectories`, `nvidia/Nemotron-Cascade-SFT-SWE`, `nvidia/Nemotron-Terminal-Corpus` | Verified pass trajectories, deduped by instance ID, zero SWE-bench Verified/Live/Pro repo overlap |
| 3 | **Tool Calling** | 15% | ~150k–300k dialogues (~0.8B tok) | Team 1 | `Salesforce/xlam-function-calling-60k`, `nvidia/Nemotron-Agentic-v1`, `nvidia/Nemotron-SFT-Agentic-v2` (tool-calling split only) | Valid JSON schema binding, multi-turn + negative ("no tool needed") turns, API-Bank overlap mask applied |
| 4 | **Indic Instructions** | 15% | ~150k–300k dialogues (~0.8B tok) | **Team 2** | `CohereLabs/aya_dataset`, `CohereLabs/aya_collection` (10 permissive subsets from `#399`), plus any native-script cleaned Indic instruction packs across all 10 languages (`hi, mr, ta, te, kn, bn, gu, ml, or, pa`) | Human-written / native-reader checked, zero translationese, `ZWJ`/`ZWNJ` intact, 1% romanised ceiling, Odia/Malayalam/Punjabi gap coverage requested |
| 5 | **Math & General Instruction** | 7–10% | ~200k–400k rows (~0.6B tok) | Team 1 | `open-thoughts/OpenThoughts3-1.2M`, `nvidia/OpenMathReasoning`, `open-r1/OpenR1-Math-220k`, `nvidia/Nemotron-Math-v2`, `nvidia/Nemotron-Science-v1`, `databricks/databricks-dolly-15k`, `sft-oasst2` | Verified math answers where applicable; short-response `1k` effort anchors included |
| 6 | **Long Context (8k–32k)** | Included across 1–5 | >= 50k rows in `8k–32k` band | Teams 1 & 2 | Multi-file repo edits (`SWE-rebench`, `commitpackft`), long CoT (`OpenCodeReasoning-2` `16k–32k`), long Indic documents/Q&A | Verified up to `32,768` tokens (`sft/max_sequence_tokens_proposal.md`), no mid-sentence truncation |

---

## 3. RL Prompt Pools Request (Stage 2 — GRPO with Verifiable Rewards)

Every RL prompt pool must exclude all benchmark items (never train on `MATH`, `HumanEval`, `MBPP`, `SWE-bench Verified`, etc.) and keep expected answers/hidden tests strictly inside verifier files.

| # | RL Pool | Target Volume | Target Team | Checker / Verifier | Requested Inputs & Quality Filter |
|---|---|---:|---|---|---|
| 1 | **Code with hidden tests** | 3,500–20,000 tasks | Team 1 | `rl/verifier.py`, `rl-data/stdio_check.py`, `rl/js/`, `rl/jsts/`, `rl/agentic/`, `swe-envs/` | `deepmind/code_contests` non-Codeforces (`3,251` train / `255` held-out already pinned in `#564`, excluding 66 free-reward IDs & 15 `>65,536`-char output IDs), plus verified Python/JS/TS/Go execution tasks and SWE-rebench tasks |
| 2 | **Math with exact checkable answers** | 10,000–40,000 prompts | Team 1 | `rl/math/math_verifier.py` | Commercial-safe, non-benchmark competition math (`agentica-org/DeepScaleR-Preview-Dataset`, `allenai/RLVR-GSM`, `nvidia/OpenMathReasoning` verifiable subset). **Exclude `rl-math-hendrycks` (TSAI 21 Nov ruling).** |
| 3 | **Indic with checkable answers** | 2,000–10,000 prompts across 10 languages | **Team 2** | `rl/indic/indic_verifier.py`, `rl/indic/generate.py` | Human-written templates + Team 2 native-reader sign-off (`team2_reviewer`). Currently **6 templates (`4 hi, 2 ta`) are signed off (`eligibility: train`, `#781`)**; **missing 8 languages (`te, kn, bn, mr, gu, ml, or, pa`)** and families `F2`/`F4`/`F5`. |

---

## 4. Teams 1 & 2 Reply & Gap Tracking

| Request Area | Partner Team | Status (28 Nov) | Reply / Parquet & `pack_table` Pointer | Identified Gaps |
|---|---|---|---|---|
| SFT Code / Agentic / Tool / Math / Long Context | Team 1 (Data A) | **Replied (`#914`)** | `teams/01-data-a/post_training/data_request_reply_v1.md` & `pack_table_post_training_v1.json` (16 SFT/long-context sources pinned & sampled, >50k `8k–32k` rows confirmed) | `OpenCodeReasoning-2` requires `#565` question rebuild; `Salesforce/xlam-function-calling-60k` gated (needs Hub terms acceptance); `sft-oasst2` not sampled yet; SFT `pack_table` rows generated once Team 10 freezes subset weights |
| SFT Indic (10 languages) | Team 2 (Data B) | **Hindi replied (`#938`); 9 languages pending** | `teams/02-data-b/post_training/hindi_inventory_v1.md` (16 Hindi SFT sources inventoried) | Clean human Hindi SFT is small (`aya_dataset` `1,153` rows); `indic-instruct` subsets (`wikihow`, `anudesh`, `hh-rlhf`, `lm_sys`) need TSAI rulings; `aya_collection` Hindi count pending `#399` recount; **remaining 9 languages (`mr, ta, te, kn, bn, gu, ml, or, pa`) awaiting Team 2 replies** |
| RL Code & Math pools | Team 1 (Data A) | **Replied (`#914`)** | Code pool v1 pinned (`#564`, `3,251` train / `255` held-out). Math pool `rl-math-omr-aops-v1` built (`nvidia/Nemotron-RL-math-OpenMathReasoning` @ `219bf017`, `109,246` AoPS problems, `41,180` exact-number, `7,017,379` prompt tokens, parquet sha256 `56394b30...`, 0 F2/canary hits) | `8,526` (`1,882` exact-number) rows in `rl-math-omr-aops-v1` overlap `Nemotron-SFT-Math-v4` problems (drop from RL if SFT trains on it); `Nemotron-RL-math-stack_overflow` (`110,976` exact-number) & `OpenR1-Math-220k` (`4,809` exact-number) are partial pending generator/licence rulings; `DeepMath-103K` (`2,909` MATH test hits, GPT-4o rewrite), `RLVR-GSM`, `DeepScaleR`, `Nemotron-RL-Math-v2` rejected/not available |
| RL Indic templates & pools | Team 2 (Data B) | **Hindi replied (`#938`, `#932`); 8 languages pending** | `6` templates (`4 hi`, `2 ta`) signed off (`#781`); Hindi `F2` (`hi_f2_words_to_digits`) in PR `#932`; Hindi `HAWP` (`2,336` human arithmetic problems, unstated licence) inventoried in `#938` | Hindi `F4` & `F5` templates missing; `HAWP` needs decimal-rule or integer-subset check + Team 9 `decontam_check.py`; **human templates + native-reader OKs still missing for 8 languages (`te, kn, bn, mr, gu, ml, or, pa`)** |
