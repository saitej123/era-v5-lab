# Licence table and strategy v0

Shared G10 licence file (`teams/10-post-training/licences/licence_table.md`).

## Team workflow (Core Team · 12 members)

- Keep this **one shared file** (`teams/10-post-training/licences/licence_table.md`).
- Give it **one section for each dataset** (for example `StarCoder`, `Stack Exchange`, `Indic web`).
- Each of the 12 G10 Core Team members adds the licence, source, and decision (`TSAI reserves`) for their own dataset in their own section by pull request to the lead's branch (`g10-week1-post-training`).
- The team lead (Sai Teja) merges the member PRs, removes duplicates in the consolidated licence table, and opens one PR to `theschoolofai/era-v5-lab` `main`.

---

## Consolidated licence table (deduplicated across datasets)

| Set | Source | Language | Licence | Decision |
| --- | --- | --- | --- | --- |
| code-python | [bigcode/starcoderdata](https://huggingface.co/datasets/bigcode/starcoderdata) | Code | other (per-file permissive Stack licences; attribution required) | TSAI reserves |
| chandassu | [BodduSriPavan111/chandassu](https://huggingface.co/datasets/BodduSriPavan111/chandassu) | Telugu | MIT (commercial use allowed) | TSAI reserves |
| ind-mr-fw2 | [HuggingFaceFW/fineweb-2](https://huggingface.co/datasets/HuggingFaceFW/fineweb-2) | Marathi (mr) | ODC-By v1.0 (commercial use permitted with attribution) | TSAI reserves |
| ind-ta-sangraha-v | [ai4bharat/sangraha](https://huggingface.co/datasets/ai4bharat/sangraha) | Tamil (ta) | CC-BY-4.0 (commercial use permitted with attribution) | TSAI reserves |
| ind-hi-hplt | [data.hplt-project.org/three/sorted/hin_Deva](https://data.hplt-project.org/three/sorted/hin_Deva) | Hindi (hi) | CC0-1.0 (packaging) / Web terms | TSAI reserves |
| ind-hi-indiccorp | [ai4bharat/IndicCorpV2](https://huggingface.co/datasets/ai4bharat/IndicCorpV2) | Hindi (hi) | CC-BY-4.0 (commercial use permitted with attribution) | TSAI reserves |
| sft-openhermes-2.5 | [teknium/OpenHermes-2.5](https://huggingface.co/datasets/teknium/OpenHermes-2.5) | English / Multi-domain | Apache-2.0 (commercial use permitted) | TSAI reserves |
| sft-tulu3-filtered | [allenai/tulu-3-sft-mixture](https://huggingface.co/datasets/allenai/tulu-3-sft-mixture) | English / Multi-domain | ODC-By-1.0 / Apache-2.0 (commercial with attribution; NC subsets removed) | TSAI reserves |
| sft-dolly-15k | [databricks/databricks-dolly-15k](https://huggingface.co/datasets/databricks/databricks-dolly-15k) | English | CC-BY-SA-4.0 (commercial use permitted with attribution) | TSAI reserves |
| sft-lmsys-chat-1m | [lmsys/lmsys-chat-1m](https://huggingface.co/datasets/lmsys/lmsys-chat-1m) | Multi-lingual | LMSYS Dataset Agreement (commercial research & post-training permitted) | TSAI reserves |
| sft-bespoke-stratos-17k | [bespokelabs/Bespoke-Stratos-17k](https://huggingface.co/datasets/bespokelabs/Bespoke-Stratos-17k) | English / STEM Reasoning | Apache-2.0 (commercial use permitted) | TSAI reserves |
| sft-openr1-math-220k | [open-r1/OpenR1-Math-220k](https://huggingface.co/datasets/open-r1/OpenR1-Math-220k) | English / Mathematics | Apache-2.0 (commercial use permitted) | TSAI reserves |
| sft-numinamath-cot | [AI-MO/NuminaMath-CoT](https://huggingface.co/datasets/AI-MO/NuminaMath-CoT) | English / Mathematics | Apache-2.0 (commercial use permitted) | TSAI reserves |
| sft-numinamath-tir | [AI-MO/NuminaMath-TIR](https://huggingface.co/datasets/AI-MO/NuminaMath-TIR) | English / Python Math Tools | Apache-2.0 (commercial use permitted) | TSAI reserves |
| sft-openmathinstruct-2 | [nvidia/OpenMathInstruct-2](https://huggingface.co/datasets/nvidia/OpenMathInstruct-2) | English / Mathematics | CC-BY-4.0 (commercial use permitted with attribution) | TSAI reserves |
| sft-ultradata-cot-agent | [openbmb/UltraInteract_sft](https://huggingface.co/datasets/openbmb/UltraInteract_sft) | English / Code & Reasoning | MIT (commercial use permitted) | TSAI reserves |
| sft-glaive-fc-v2 | [glaiveai/glaive-function-calling-v2](https://huggingface.co/datasets/glaiveai/glaive-function-calling-v2) | JSON / Tool Calls | Apache-2.0 (commercial use permitted) | TSAI reserves |
| sft-salesforce-xlam-60k | [Salesforce/xlam-function-calling-60k](https://huggingface.co/datasets/Salesforce/xlam-function-calling-60k) | Multi-tool / API | CC-BY-4.0 (commercial use permitted with attribution) | TSAI reserves |
| sft-magicoder-oss | [ise-uiuc/Magicoder-OSS-Instruct-75K](https://huggingface.co/datasets/ise-uiuc/Magicoder-OSS-Instruct-75K) | Code (Polyglot) | Apache-2.0 (commercial use permitted) | TSAI reserves |
| sft-commitpackft | [bigcode/commitpackft](https://huggingface.co/datasets/bigcode/commitpackft) | 350+ Code Languages | MIT / Permissive per-repo (commercial use permitted) | TSAI reserves |
| sft-swe-gym | [SWE-Gym/SWE-Gym](https://huggingface.co/datasets/SWE-Gym/SWE-Gym) | Code / Python SWE | MIT (commercial use permitted) | TSAI reserves |
| rl-nvidia-helpsteer2 | [nvidia/HelpSteer2](https://huggingface.co/datasets/nvidia/HelpSteer2) | English / Multi-domain | CC-BY-4.0 (commercial use permitted with attribution) | TSAI reserves |
| rl-skywork-reward-80k | [Skywork/Skywork-Reward-Preference-80K-v0.2](https://huggingface.co/datasets/Skywork/Skywork-Reward-Preference-80K-v0.2) | English / Multi-domain | Apache-2.0 (commercial use permitted) | TSAI reserves |
| rl-ultrafeedback-clean | [argilla/ultrafeedback-binarized-preferences-cleaned](https://huggingface.co/datasets/argilla/ultrafeedback-binarized-preferences-cleaned) | English / Multi-domain | MIT (commercial use permitted) | TSAI reserves |
| rl-nectar-rm | [berkeley-nest/Nectar](https://huggingface.co/datasets/berkeley-nest/Nectar) | English / Multi-domain | Apache-2.0 (commercial use permitted) | TSAI reserves |
| rl-intel-orca-dpo | [Intel/orca_dpo_pairs](https://huggingface.co/datasets/Intel/orca_dpo_pairs) | English / Reasoning | Apache-2.0 (commercial use permitted) | TSAI reserves |
| rl-distilabel-math-dpo | [argilla/distilabel-math-dpo](https://huggingface.co/datasets/argilla/distilabel-math-dpo) | English / Mathematics | Apache-2.0 (commercial use permitted) | TSAI reserves |
| rl-code-feedback-dpo | [HuggingFaceH4/Code-Feedback](https://huggingface.co/datasets/m-a-p/CodeFeedback-Filtered-Instruction) | Code (Polyglot) | Apache-2.0 (commercial use permitted) | TSAI reserves |
| rl-wildguardmix | [allenai/wildguardmix](https://huggingface.co/datasets/allenai/wildguardmix) | English / Safety | ODC-By-1.0 (commercial use permitted with attribution) | TSAI reserves |
---

## Dataset sections by G10 Core Team member (12)

### 1. Sai Teja (Lead) — StarCoder (`code-python` · `bigcode/starcoderdata`)

- **Core team:** 10. Post-training and Agentic (Lead) · **Week 2:** 9. Evaluation · **Week 3:** 12. Quantization and Serving
- **Set:** `code-python`
- **Language:** `Code`
- **Source:** [`bigcode/starcoderdata`](https://huggingface.co/datasets/bigcode/starcoderdata)
- **Licence:** `other` — StarCoder training corpus drawn from The Stack; each file retains its upstream licence and attribution notice. Commercial use must follow per-file attribution terms.
- **Decision:** `TSAI reserves`

### 1b. Sai Teja (Lead) — Chandassu (`BodduSriPavan111/chandassu`)

- **Core team:** 10. Post-training and Agentic (Lead) · **Week 2:** 9. Evaluation · **Week 3:** 12. Quantization and Serving
- **Set:** `chandassu`
- **Language:** Telugu (`te`)
- **Source:** [`BodduSriPavan111/chandassu`](https://huggingface.co/datasets/BodduSriPavan111/chandassu) (4,651 padyams; eight metres in vruttamu, jaathi, and vupajaathi)
- **Licence:** `MIT` — commercial use is allowed. The dataset card names the licence as MIT.
- **Decision:** `TSAI reserves`
- **Reading note:** 1,134 Vemana poems store a carriage return as the plain letters `_x000D_`. 23 poems have words replaced by `...`. ZWNJ and ZWJ stay in the text. They are not a licence issue.

### 2. Ajay Kumar — Dataset section *(placeholder for PR to `g10-week1-post-training`)*

- **Set:** *(TBD via PR)*
- **Language:** *(TBD via PR)*
- **Source:** *(TBD via PR)*
- **Licence:** *(TBD via PR)*
- **Decision:** `TSAI reserves`

### 3. Amit T — Indic web (`ind-mr-fw2` · FineWeb-2 Marathi)

- **Set:** `ind-mr-fw2` — FineWeb-2 Marathi split (`data/mr/`)
- **Language:** Marathi (`mr`)
- **Source:** [`HuggingFaceFW/fineweb-2`](https://huggingface.co/datasets/HuggingFaceFW/fineweb-2) (Hugging Face, 2024; Common Crawl curated web pipeline)
- **Licence:** `ODC-By v1.0` (Open Data Commons Attribution License v1.0). Commercial use is explicitly permitted with attribution.
- **Decision:** `TSAI reserves` — commercial-use only rule satisfied. Attribution requirement to be fulfilled in the public model card and training datasheet. Raw data not committed to repository.

### 4. Anirudh Narla — Dataset section *(placeholder for PR to `g10-week1-post-training`)*

- **Set:** *(TBD via PR)*
- **Language:** *(TBD via PR)*
- **Source:** *(TBD via PR)*
- **Licence:** *(TBD via PR)*
- **Decision:** `TSAI reserves`

### 5. Ashish Kamble — Dataset section *(placeholder for PR to `g10-week1-post-training`)*

- **Set:** *(TBD via PR)*
- **Language:** *(TBD via PR)*
- **Source:** *(TBD via PR)*
- **Licence:** *(TBD via PR)*
- **Decision:** `TSAI reserves`

### 6. Hema Varshini Palpandian — Tamil (`ind-ta-sangraha-v`)

- **Set:** `ind-ta-sangraha-v`
- **Language:** Tamil (`ta`; source split `tam`)
- **Source:** [`ai4bharat/sangraha`](https://huggingface.co/datasets/ai4bharat/sangraha), Verified Tamil subset.
- **Licence:** `CC-BY-4.0` — publisher-declared; permits commercial use with attribution, a licence link and notice of changes.
- **Decision:** `TSAI reserves` — source checks and SFT/RL selection pending.
- **Reading note:** 500 Tamil documents. No tested chat/tool markers found. Document URLs and the source release are missing from the sample; verify provenance before training.

### 7. Lokesh Arundathi — Dataset section *(placeholder for PR to `g10-week1-post-training`)*

- **Set:** *(TBD via PR)*
- **Language:** *(TBD via PR)*
- **Source:** *(TBD via PR)*
- **Licence:** *(TBD via PR)*
- **Decision:** `TSAI reserves`

### 8. Rammohan Madhusudan — Indic web (`ind-hi-hplt` · HPLT 3.0 `hin_Deva`)

- **Set:** `ind-hi-hplt`
- **Language:** `Hindi` (`hin_Deva`)
- **Source:** HPLT 3.0 monolingual, sorted release: [`data.hplt-project.org/three/sorted/hin_Deva`](https://data.hplt-project.org/three/sorted/hin_Deva) (web crawl from Internet Archive and Common Crawl; catalogue at [`hplt-project.org/datasets/v3.0`](https://hplt-project.org/datasets/v3.0))
- **Licence:** `CC0-1.0` for the **packaging only**. HPLT's Terms of Use: "We do not own any of the text from which these text data has been extracted" and "We license the actual packaging of these text data under the Creative Commons CC0 license". The underlying web text keeps its original copyright (no per-document licence is given). HPLT 3.0 filters robots.txt opt-outs and removes sources on a takedown request in the next release.
- **Decision:** `TSAI reserves`. Commercial use of the collection is allowed (CC0). For the web text itself, treat it like every other web-crawl source: honour robots.txt opt-outs and takedown requests, keep each document's source URL so it can be removed, and do not redistribute raw text.

### 9. Ranjani Chandrasekaran — Indic web (`ind-hi-indiccorp`)

- **Set:** `ind-hi-indiccorp` — IndicCorpV2 Hindi subset (`data/hi-{1,2,3}.txt`)
- **Language:** Hindi (`hi`)
- **Source:** [`ai4bharat/IndicCorpV2`](https://huggingface.co/datasets/ai4bharat/IndicCorpV2) (HuggingFace, AI4Bharat)
- **Licence:** CC-BY-4.0 — attribution required; commercial use permitted
- **Decision:** `TSAI reserves` (satisfies commercial-use rule via CC-BY-4.0 attribution; attribution to be carried in the model card)


### 10. Ravi Naik — Dataset section *(placeholder for PR to `g10-week1-post-training`)*

- **Set:** *(TBD via PR)*
- **Language:** *(TBD via PR)*
- **Source:** *(TBD via PR)*
- **Licence:** *(TBD via PR)*
- **Decision:** `TSAI reserves`

### 11. Syed Abdul — Dataset section *(placeholder for PR to `g10-week1-post-training`)*

- **Set:** *(TBD via PR)*
- **Language:** *(TBD via PR)*
- **Source:** *(TBD via PR)*
- **Licence:** *(TBD via PR)*
- **Decision:** `TSAI reserves`

### 12. Vikash Ranjan — Stack Exchange / Dataset section *(placeholder for PR to `g10-week1-post-training`)*

- **Set:** *(TBD via PR)*
- **Language:** *(TBD via PR)*
- **Source:** *(TBD via PR)*
- **Licence:** *(TBD via PR)*
- **Decision:** `TSAI reserves`

---

## Frontier Post-Training SFT & RL Inventory (Commercial Production)

### SFT Mixture (Supervised Fine-Tuning)

#### S1. OpenHermes 2.5 (`sft-openhermes-2.5`)
- **Stage:** Post-Training SFT (General Conversational Anchor)
- **Set:** `sft-openhermes-2.5`
- **Language:** English / Multi-domain (900+ domains)
- **Source:** [`teknium/OpenHermes-2.5`](https://huggingface.co/datasets/teknium/OpenHermes-2.5)
- **Licence:** `Apache-2.0` — commercial use allowed.
- **Decision:** `TSAI reserves`
- **Extraction Note:** ~1,001,551 multi-turn dialogues filtered to remove non-commercial upstream components. Benchmark decontaminated against GSM8k and HumanEval.

#### S2. Tulu 3 SFT Mixture Filtered (`sft-tulu3-filtered`)
- **Stage:** Post-Training SFT (Decontaminated Instruction Recipe)
- **Set:** `sft-tulu3-filtered`
- **Language:** English / General
- **Source:** [`allenai/tulu-3-sft-mixture`](https://huggingface.co/datasets/allenai/tulu-3-sft-mixture)
- **Licence:** `ODC-By-1.0` / `Apache-2.0` — commercial use allowed with attribution.
- **Decision:** `TSAI reserves`
- **Extraction Note:** Curated by the Allen Institute for AI (Ai2). Ingests Persona MATH, Persona Code, Persona IF, Evol CodeAlpaca, and WildJailbreak. The 9,500 `No Robots` samples (`CC-BY-NC-4.0`) are quarantined and excluded.

#### S3. Databricks Dolly 15k (`sft-dolly-15k`)
- **Stage:** Post-Training SFT (Human-Authored Ground Truth)
- **Set:** `sft-dolly-15k`
- **Language:** English
- **Source:** [`databricks/databricks-dolly-15k`](https://huggingface.co/datasets/databricks/databricks-dolly-15k)
- **Licence:** `CC-BY-SA-4.0` — commercial use permitted with attribution and share-alike terms.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 15k pure, employee-written human demonstrations (brainstorming, QA, summarization) devoid of synthetic API artifacts.

#### S4. LMSYS-Chat-1M Prompts (`sft-lmsys-chat-1m`)
- **Stage:** Post-Training SFT (Real-World Intent Alignment)
- **Set:** `sft-lmsys-chat-1m`
- **Language:** Multi-lingual (English, Spanish, Chinese, French, etc.)
- **Source:** [`lmsys/lmsys-chat-1m`](https://huggingface.co/datasets/lmsys/lmsys-chat-1m)
- **Licence:** `LMSYS Dataset Agreement` — research & post-training permitted; safe alternative to Terms-violating ShareGPT.
- **Decision:** `TSAI reserves`
- **Extraction Note:** User-turn prompts extracted to anchor natural human user distribution and conversational tone.

#### S5. Bespoke Stratos 17k (`sft-bespoke-stratos-17k`)
- **Stage:** Post-Training SFT (Deep Reasoning & Self-Correction)
- **Set:** `sft-bespoke-stratos-17k`
- **Language:** English / STEM Reasoning
- **Source:** [`bespokelabs/Bespoke-Stratos-17k`](https://huggingface.co/datasets/bespokelabs/Bespoke-Stratos-17k)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 17,000 multi-turn `<|think|>` Chain-of-Thought traces replicating o1/R1-level reasoning, backtracking, and verification.

#### S6. OpenR1-Math 220k (`sft-openr1-math-220k`)
- **Stage:** Post-Training SFT (Formal Mathematical Verification)
- **Set:** `sft-openr1-math-220k`
- **Language:** English / Mathematics
- **Source:** [`open-r1/OpenR1-Math-220k`](https://huggingface.co/datasets/open-r1/OpenR1-Math-220k)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 220,000 verified mathematical solution traces with step-by-step reflection tokens curated by the Hugging Face Open-R1 team.

#### S7. NuminaMath CoT & TIR (`sft-numinamath-cot` / `sft-numinamath-tir`)
- **Stage:** Post-Training SFT (Olympiad Math & Code-Interpreter Reasoning)
- **Set:** `sft-numinamath-cot`, `sft-numinamath-tir`
- **Language:** English / Mathematics & Python TIR
- **Source:** [`AI-MO/NuminaMath-CoT`](https://huggingface.co/datasets/AI-MO/NuminaMath-CoT), [`AI-MO/NuminaMath-TIR`](https://huggingface.co/datasets/AI-MO/NuminaMath-TIR)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 860k CoT solutions plus 64k Tool-Integrated Reasoning (Python code execution inside the `<|think|>` block) pairs from the AIMO 1st Progress Prize winners.

#### S8. OpenMathInstruct-2 (`sft-openmathinstruct-2`)
- **Stage:** Post-Training SFT (Large-Scale Mathematical Instruction)
- **Set:** `sft-openmathinstruct-2`
- **Language:** English / Mathematics
- **Source:** [`nvidia/OpenMathInstruct-2`](https://huggingface.co/datasets/nvidia/OpenMathInstruct-2)
- **Licence:** `CC-BY-4.0` — commercial use permitted with attribution.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 5M high-quality mathematical instruction pairs synthesized by NVIDIA. Filtered down to 500k highest-complexity problems.

#### S9. UltraInteract SFT (`sft-ultradata-cot-agent`)
- **Stage:** Post-Training SFT (Agentic Tree-of-Thought Workflows)
- **Set:** `sft-ultradata-cot-agent`
- **Language:** English / Multi-turn Logic & Code
- **Source:** [`openbmb/UltraInteract_sft`](https://huggingface.co/datasets/openbmb/UltraInteract_sft)
- **Licence:** `MIT` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** Multi-turn interaction trees with tool execution and step-by-step reflection traces.

#### S10. Glaive Function Calling v2 (`sft-glaive-fc-v2`)
- **Stage:** Post-Training SFT (API Schema Compliance & Tool Calling)
- **Set:** `sft-glaive-fc-v2`
- **Language:** JSON / Multi-turn Tools
- **Source:** [`glaiveai/glaive-function-calling-v2`](https://huggingface.co/datasets/glaiveai/glaive-function-calling-v2)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 113,000 dialogues teaching exact JSON schema compliance, function routing, and parsing using the G10 special tokens `<|tool_call|>` and `<|tool_result|>`.

#### S11. Salesforce xLAM 60k (`sft-salesforce-xlam-60k`)
- **Stage:** Post-Training SFT (Advanced Agentic API Orchestration)
- **Set:** `sft-salesforce-xlam-60k`
- **Language:** English / Structured APIs
- **Source:** [`Salesforce/xlam-function-calling-60k`](https://huggingface.co/datasets/Salesforce/xlam-function-calling-60k)
- **Licence:** `CC-BY-4.0` — commercial use permitted with attribution.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 60,000 multi-turn API routing dialogues covering complex parameter parsing and multi-step tool calls.

#### S12. Magicoder OSS-Instruct (`sft-magicoder-oss`)
- **Stage:** Post-Training SFT (Polyglot Coding & Bug Resolution)
- **Set:** `sft-magicoder-oss`
- **Language:** Code (Python, Rust, C++, Java, Go)
- **Source:** [`ise-uiuc/Magicoder-OSS-Instruct-75K`](https://huggingface.co/datasets/ise-uiuc/Magicoder-OSS-Instruct-75K)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 75k programming problems seeded from open-source repositories under MIT/Apache licenses.

#### S13. BigCode CommitPackFT (`sft-commitpackft`)
- **Stage:** Post-Training SFT (Repository Patching & Diff Understanding)
- **Set:** `sft-commitpackft`
- **Language:** 350+ Programming Languages
- **Source:** [`bigcode/commitpackft`](https://huggingface.co/datasets/bigcode/commitpackft)
- **Licence:** `MIT` / Permissive per-repo — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 700k+ natural git commit instructions and corresponding code diffs.

#### S14. SWE-Gym Trajectories (`sft-swe-gym`)
- **Stage:** Post-Training SFT (Autonomous Software Engineering)
- **Set:** `sft-swe-gym`
- **Language:** Python / Bash / Git
- **Source:** [`SWE-Gym/SWE-Gym`](https://huggingface.co/datasets/SWE-Gym/SWE-Gym)
- **Licence:** `MIT` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** End-to-end SWE problem-solving episodes with tool interactions, bash commands, and git diff generation.

---

### Preference Optimization & RL Inventory (DPO / ORPO / RM / GRPO)

#### R1. NVIDIA HelpSteer2 & Preference (`rl-nvidia-helpsteer2`)
- **Stage:** Preference Optimization & Reward Modeling (Multi-Attribute & Pairwise)
- **Set:** `rl-nvidia-helpsteer2`
- **Language:** English / Multi-domain
- **Source:** [`nvidia/HelpSteer2`](https://huggingface.co/datasets/nvidia/HelpSteer2)
- **Licence:** `CC-BY-4.0` — commercial use permitted with attribution.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 10,000 human-annotated samples evaluated on Helpfulness, Correctness, Coherence, Complexity, and Verbosity, with human-authored preference justifications.

#### R2. Skywork Reward Preference 80K (`rl-skywork-reward-80k`)
- **Stage:** Preference Optimization (High-Precision Reward Modeling)
- **Set:** `rl-skywork-reward-80k`
- **Language:** English / Multi-domain
- **Source:** [`Skywork/Skywork-Reward-Preference-80K-v0.2`](https://huggingface.co/datasets/Skywork/Skywork-Reward-Preference-80K-v0.2)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** SOTA curated preference pairs optimized for Bradley-Terry reward scoring.

#### R3. UltraFeedback Binarized Cleaned (`rl-ultrafeedback-clean`)
- **Stage:** Preference Optimization (General DPO Alignment)
- **Set:** `rl-ultrafeedback-clean`
- **Language:** English / Multi-domain
- **Source:** [`argilla/ultrafeedback-binarized-preferences-cleaned`](https://huggingface.co/datasets/argilla/ultrafeedback-binarized-preferences-cleaned)
- **Licence:** `MIT` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** Primary pairwise dataset for DPO/ORPO. Cleaned to prevent evaluation contamination.

#### R4. Berkeley Nectar (`rl-nectar-rm`)
- **Stage:** Preference Optimization (Multi-Way Ranking)
- **Set:** `rl-nectar-rm`
- **Language:** English / Multi-domain
- **Source:** [`berkeley-nest/Nectar`](https://huggingface.co/datasets/berkeley-nest/Nectar)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 183k prompts each with 7 responses ranked from 1 to 7.

#### R5. Intel Orca DPO Pairs (`rl-intel-orca-dpo`)
- **Stage:** Preference Optimization (Reasoning Depth & Anti-Laziness)
- **Set:** `rl-intel-orca-dpo`
- **Language:** English / Analytical
- **Source:** [`Intel/orca_dpo_pairs`](https://huggingface.co/datasets/Intel/orca_dpo_pairs)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** Pairwise preferences favoring step-by-step thinking over shallow completions.

#### R6. Distilabel Math DPO (`rl-distilabel-math-dpo`)
- **Stage:** Preference Optimization (Mathematical Calculation Alignment)
- **Set:** `rl-distilabel-math-dpo`
- **Language:** English / Mathematics
- **Source:** [`argilla/distilabel-math-dpo`](https://huggingface.co/datasets/argilla/distilabel-math-dpo)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** Penalizes intermediate math calculation slips and step hallucinations.

#### R7. Code-Feedback DPO (`rl-code-feedback-dpo`)
- **Stage:** Preference Optimization (Code Veracity & Idiomatic Style)
- **Set:** `rl-code-feedback-dpo`
- **Language:** Code (Polyglot)
- **Source:** [`HuggingFaceH4/Code-Feedback`](https://huggingface.co/datasets/m-a-p/CodeFeedback-Filtered-Instruction)
- **Licence:** `Apache-2.0` — commercial use permitted.
- **Decision:** `TSAI reserves`
- **Extraction Note:** Pairwise code preferences favoring working, tested implementations over buggy or hallucinated APIs.

#### R8. AllenAI WildGuardMix (`rl-wildguardmix`)
- **Stage:** Preference Optimization (Frontier Safety & Refusal Boundaries)
- **Set:** `rl-wildguardmix`
- **Language:** English / Adversarial Safety
- **Source:** [`allenai/wildguardmix`](https://huggingface.co/datasets/allenai/wildguardmix)
- **Licence:** `ODC-By-1.0` — commercial use permitted with attribution.
- **Decision:** `TSAI reserves`
- **Extraction Note:** 86k safety and jailbreak interaction pairs calibrating refusal behavior without false refusals on benign prompts.

---

## Strategy v0

- **Commercial-use data only:** Any dataset or file whose licence is missing or restricts commercial use is excluded.
- **Decision authority:** `TSAI reserves` all dataset release and retention decisions across all members.
- **Repository hygiene:** Raw Parquet, Arrow, or binary training files never enter `era-v5-lab` (enforced by `pr-guard`).
- **Token & effort rules:** 256 reserved special tokens (`0..255`) and four plain-text effort levels (`1k`, `4k`, `16k`, `64k`).
- **Benchmark decontamination protocol:** All training splits (code and text) must be programmatically decontaminated against evaluation benchmarks (SWE-bench, HumanEval, MBPP, LiveCodeBench, BigCodeBench) using 13-gram exact match and embedding-similarity filtering prior to post-training.
- **Provenance & attribution ledger:** Every permissive dataset (ODC-By, CC-BY, Apache-2.0, MIT, Stack per-file notices) has its snapshot timestamp, source repository URL, and licensing terms recorded for automatic aggregation into the release model card.
- **Right-to-be-forgotten & takedown handling:** For curated web crawls (FineWeb-2, HPLT 3.0), maintain source URL manifests to fulfill upstream robots.txt exclusions, DMCA notices, and GDPR Article 17 deletion requests across training checkpoint iterations.
