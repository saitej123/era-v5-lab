# Licence table and strategy v0

Shared G10 licence file (`teams/10-post-training/licences/licence_table.md`).

## Team workflow (Core Team · 12 members)

- Keep this **one shared file** (`teams/10-post-training/licences/licence_table.md`).
- Give it **one section for each dataset** (for example `StarCoder`, `Stack Exchange`, `Indic web`).
- Each of the 12 G10 Core Team members adds the licence, source, and decision (`TSAI reserves`) for their own dataset in their own section by pull request to the lead's branch (`g10-week1-post-training`).
- The team lead (Sai Teja) merges the member PRs, removes duplicates in the consolidated licence table, and opens one PR to `theschoolofai/era-v5-lab` `main`.

---

## Consolidated licence table (deduplicated across datasets)

Three stages. Sets marked `excluded` stay in the table with the reason and are not used in any training mix (TSAI ruling, G10 chat, 30 Oct).

### Stage 0: Foundation data (pre-training and continual pre-training)

| Set | Source | Language | Licence | Decision |
| --- | --- | --- | --- | --- |
| code-python | bigcode/starcoderdata | Code | other (per-file permissive Stack licences; attribution required) | TSAI reserves |
| chandassu | BodduSriPavan111/chandassu | Telugu | MIT (commercial use allowed) | TSAI reserves |
| ind-mr-fw2 | [HuggingFaceFW/fineweb-2](https://huggingface.co/datasets/HuggingFaceFW/fineweb-2) | Marathi (mr) | ODC-By v1.0 (commercial use permitted with attribution) | TSAI reserves |
| ind-ta-sangraha-v | [ai4bharat/sangraha](https://huggingface.co/datasets/ai4bharat/sangraha) | Tamil (ta) | CC-BY-4.0 (commercial use permitted with attribution) | TSAI reserves |
| ind-hi-hplt | [data.hplt-project.org/three/sorted/hin_Deva](https://data.hplt-project.org/three/sorted/hin_Deva) | Hindi (hi) | CC0-1.0 (packaging) / Web terms | TSAI reserves |
| ind-hi-indiccorp | [ai4bharat/IndicCorpV2](https://huggingface.co/datasets/ai4bharat/IndicCorpV2) | Hindi (hi) | CC-BY-4.0 (commercial use permitted with attribution) | TSAI reserves |
| code-go | bigcode/starcoderdata | Code (Go) | other (per-file permissive Stack licences; attribution required) | TSAI reserves |

### Stage 1: Supervised fine-tuning (SFT) instruction mixture

| Set | Source | Language | Generator model | Licence | Decision |
| --- | --- | --- | --- | --- | --- |
| sft-code-commitpackft | [bigcode/commitpackft](https://huggingface.co/datasets/bigcode/commitpackft) | Code (350+ languages) | none (real GitHub commits) | mit (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-code-self-oss-instruct | [bigcode/self-oss-instruct-sc2-exec-filter-50k](https://huggingface.co/datasets/bigcode/self-oss-instruct-sc2-exec-filter-50k) | Code (Python) | The base model itself generates instructions, responses and tests in the SelfCodeAlign method (arXiv 2410.24198); StarCoder2-Instruct used StarCoder2-15B (from memory, the card is empty; verify) | odc-by (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-code-magicoder-oss | [ise-uiuc/Magicoder-OSS-Instruct-75K](https://huggingface.co/datasets/ise-uiuc/Magicoder-OSS-Instruct-75K) | Code (polyglot) | GPT-3.5 (OpenAI, closed) | mit (Hub tag; commercial use permitted per tag) | excluded |
| sft-code-codefeedback | [m-a-p/CodeFeedback-Filtered-Instruction](https://huggingface.co/datasets/m-a-p/CodeFeedback-Filtered-Instruction) | Code (polyglot) | Mixed upstream sets (Magicoder, Evol-Instruct code); Qwen-72B-Chat used only as a filter | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-rl-code-rstar-coder | [microsoft/rStar-Coder](https://huggingface.co/datasets/microsoft/rStar-Coder) | Code (competitive) | GPT-4o (OpenAI, closed) for problem synthesis and test-input generators; QwQ-32B (open weights) for the long-reasoning solutions (paper, arXiv 2505.21297) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | excluded |
| sft-code-swe-rebench-openhands | [nebius/SWE-rebench-openhands-trajectories](https://huggingface.co/datasets/nebius/SWE-rebench-openhands-trajectories) | Code (agent trajectories) | Qwen3-Coder-480B-A35B-Instruct (open weights) via OpenHands | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-code-nemotron-cp-v2 | [nvidia/Nemotron-SFT-Competitive-Programming-v2](https://huggingface.co/datasets/nvidia/Nemotron-SFT-Competitive-Programming-v2) | Code (competitive, SQL) | Competitive subset: model not named on the card (NeMo-Skills pipeline; DeepSeek-R1-0528 is cited). Exercism subset: synthetic, model not named. Text-to-SQL: NVIDIA Data Designer, LLM not named | cc-by-4.0, odc-by, mit (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-code-nemotron-swe-v3 | [nvidia/Nemotron-SFT-SWE-v3](https://huggingface.co/datasets/nvidia/Nemotron-SFT-SWE-v3) | Code (agent trajectories) | Not on the card (it names only the OpenHands, SWE-agent and mini-SWE-agent harnesses). NVIDIA's Nemotron 3 Ultra paper names MiniMax-M2.5 and Qwen3-Coder-480B-A35B-Instruct (open weights) for its SWE trajectories; not tied to this set by the card, verify | cc-by-4.0, apache-2.0, mit, bsd-3-clause, bsd-2-clause (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-code-nemotron-terminal | [nvidia/Nemotron-Terminal-Corpus](https://huggingface.co/datasets/nvidia/Nemotron-Terminal-Corpus) | Code (terminal agent) | DeepSeek-V3.2 (open weights) for both the synthetic tasks and the trajectories (paper, arXiv 2602.21193) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-code-opencodereasoning | [nvidia/OpenCodeReasoning](https://huggingface.co/datasets/nvidia/OpenCodeReasoning) | Code (competitive) | DeepSeek-R1 (open weights) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-code-opencodereasoning-2 | [nvidia/OpenCodeReasoning-2](https://huggingface.co/datasets/nvidia/OpenCodeReasoning-2) | Code (competitive) | DeepSeek-R1 for solutions, QwQ for critiques (both open weights) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-code-codeforces-cots | [open-r1/codeforces-cots](https://huggingface.co/datasets/open-r1/codeforces-cots) | Code (competitive) | DeepSeek-R1 (open weights) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-indic-aya-collection | [CohereLabs/aya_collection](https://huggingface.co/datasets/CohereLabs/aya_collection) | Multilingual incl. Indic | Templated and translated from existing datasets; no single generator | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-indic-aya-dataset | [CohereLabs/aya_dataset](https://huggingface.co/datasets/CohereLabs/aya_dataset) | Multilingual incl. Indic | None (human-written) | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-indic-indic-align | [ai4bharat/indic-align](https://huggingface.co/datasets/ai4bharat/indic-align) | 14 Indic languages | Llama-2-70B-Chat for many parts (Llama), plus translated human prompts; Mistral-7B in some parts | cc-by-4.0 (Hub tag; commercial use permitted per tag) | excluded |
| sft-indic-samvaad-hi | [sarvamai/samvaad-hi-v1](https://huggingface.co/datasets/sarvamai/samvaad-hi-v1) | Hindi, English, Hinglish | Not stated on the card or in Sarvam's announcement; unknown | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-indic-code-oss-codes-coding | [oss-codes/Coding-Conversational-Dataset-Indic](https://huggingface.co/datasets/oss-codes/Coding-Conversational-Dataset-Indic) | Indic (Hindi, Tamil, ...) + code | Not stated; the card is empty | mit (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-indic-code-oss-codes-cs | [oss-codes/Computer-Science-Conversational-Dataset-Indic](https://huggingface.co/datasets/oss-codes/Computer-Science-Conversational-Dataset-Indic) | Indic + computer science | Not stated; the card is empty | mit (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-indic-math-orca-math-hi | [BhabhaAI/orca-math-word-problems-200k-hindi-filtered](https://huggingface.co/datasets/BhabhaAI/orca-math-word-problems-200k-hindi-filtered) | Hindi (math) | GPT-4 (OpenAI, closed) via Orca-Math, then translated | mit (Hub tag; commercial use permitted per tag) | excluded |
| sft-indic-math-aryabhatta-orca-hi | [GenVRadmin/Aryabhatta-Orca-Maths-Hindi](https://huggingface.co/datasets/GenVRadmin/Aryabhatta-Orca-Maths-Hindi) | Hindi (math) | GPT-4 (OpenAI, closed) via Orca-Math, then translated | mit (Hub tag; commercial use permitted per tag) | excluded |
| sft-math-nemotron-proofs | [nvidia/Nemotron-Math-Proofs-v1](https://huggingface.co/datasets/nvidia/Nemotron-Math-Proofs-v1) | English / Mathematics | gpt-oss-120b (statement formalisation) and Goedel-Prover-V2-32B (proofs) | cc-by-sa-4.0 (Hub tag; share-alike, team decision needed) | allowed (CC-BY-SA, attribution needed) |
| sft-math-nemotron-math-v2 | [nvidia/Nemotron-Math-v2](https://huggingface.co/datasets/nvidia/Nemotron-Math-v2) | English / Mathematics | gpt-oss-120b (all solution traces) | cc-by-4.0, cc-by-sa-4.0 (Hub tag; share-alike, team decision needed) | allowed (CC-BY-SA, attribution needed) |
| sft-math-openmathinstruct-2 | [nvidia/OpenMathInstruct-2](https://huggingface.co/datasets/nvidia/OpenMathInstruct-2) | English / Mathematics | Llama-3.1-405B-Instruct (Llama) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | excluded |
| sft-rl-math-openmathreasoning | [nvidia/OpenMathReasoning](https://huggingface.co/datasets/nvidia/OpenMathReasoning) | English / Mathematics | DeepSeek-R1 and QwQ-32B (open weights) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-math-openr1-math | [open-r1/OpenR1-Math-220k](https://huggingface.co/datasets/open-r1/OpenR1-Math-220k) | English / Mathematics | DeepSeek-R1 (open weights) | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-math-numinamath-1.5 | [project-numina/NuminaMath-1.5](https://huggingface.co/datasets/project-numina/NuminaMath-1.5) | English / Mathematics | Mixed; solutions from the source datasets, no single generator stated | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-math-numinamath-cot | [project-numina/NuminaMath-CoT](https://huggingface.co/datasets/project-numina/NuminaMath-CoT) | English / Mathematics | GPT-4 (OpenAI, closed) rewrote solutions into chain-of-thought; GPT-4o was used for the tool-integrated set (secondary sources, not on the card; verify) | apache-2.0 (Hub tag; commercial use permitted per tag) | excluded |
| sft-stem-code-nemotron-post-v1 | [nvidia/Nemotron-Post-Training-Dataset-v1](https://huggingface.co/datasets/nvidia/Nemotron-Post-Training-Dataset-v1) | English / Math, STEM, Code | DeepSeek-R1-0528 and Qwen3-235B-A22B (open weights); Llama-3.3-Nemotron-Super is the model it was built to train | cc-by-4.0 (Hub tag; commercial use permitted per tag) | excluded |
| sft-stem-code-nemotron-post-v2 | [nvidia/Nemotron-Post-Training-Dataset-v2](https://huggingface.co/datasets/nvidia/Nemotron-Post-Training-Dataset-v2) | Multilingual / Math, STEM, Code | DeepSeek-R1-0528, Qwen3-235B-A22B, Qwen3-30B-A3B (open weights), Qwen2.5-14B-Instruct and Qwen2.5-32B-Instruct-AWQ; the card does not map models to subsets (read from the Hub page, not the gated files) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | excluded |
| sft-stem-code-openthoughts3 | [open-thoughts/OpenThoughts3-1.2M](https://huggingface.co/datasets/open-thoughts/OpenThoughts3-1.2M) | English / Math, Code, Science | QwQ-32B (open weights) | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| sft-science-nemotron-science | [nvidia/Nemotron-Science-v1](https://huggingface.co/datasets/nvidia/Nemotron-Science-v1) | English / Science | gpt-oss-120b (open weights) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |

### Stage 2: Preference optimization and RLVR

| Set | Source | Language | Generator model | Licence | Decision |
| --- | --- | --- | --- | --- | --- |
| rl-code-r2e-gym | [R2E-Gym/R2E-Gym-Subset](https://huggingface.co/datasets/R2E-Gym/R2E-Gym-Subset) | Code (Python SWE) | Not named in the paper's main text (tests and issues are LLM-generated by back-translation from commits, arXiv 2504.07164); check its appendix | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| rl-code-swe-gym | [SWE-Gym/SWE-Gym](https://huggingface.co/datasets/SWE-Gym/SWE-Gym) | Code (Python SWE) | None (real GitHub issues and tests) | mit (Hub tag; commercial use permitted per tag) | TSAI reserves |
| rl-code-acecode-87k | [TIGER-Lab/AceCode-87K](https://huggingface.co/datasets/TIGER-Lab/AceCode-87K) | Code (Python) | GPT-4o-mini (OpenAI, closed) rewrote the questions | mit (Hub tag; commercial use permitted per tag) | excluded |
| rl-code-deepcoder | [agentica-org/DeepCoder-Preview-Dataset](https://huggingface.co/datasets/agentica-org/DeepCoder-Preview-Dataset) | Code (competitive) | None (problems and tests collected from existing sets) | mit (Hub tag; commercial use permitted per tag) | TSAI reserves |
| rl-code-swe-rebench-v2 | [nebius/SWE-rebench-V2](https://huggingface.co/datasets/nebius/SWE-rebench-V2) | Code (20 languages incl. Go) | Qwen3-Coder-480B-A35B-Instruct (installation agent, log parsing); quality labels from an ensemble of gpt-oss-120b, GLM-4.7 and DeepSeek-V3.2 (paper, arXiv 2602.23866) | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| rl-code-codeforces | [open-r1/codeforces](https://huggingface.co/datasets/open-r1/codeforces) | Code (competitive) | None (Codeforces problems); the card mentions DeepSeek-R1 only for generated test inputs | cc-by-4.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| rl-math-dapo-17k | [BytedTsinghua-SIA/DAPO-Math-17k](https://huggingface.co/datasets/BytedTsinghua-SIA/DAPO-Math-17k) | English / Mathematics | Problems scraped from the web and competition sites; an unnamed LLM rewrote questions so the answer is an integer (paper, arXiv 2503.14476) | apache-2.0 (Hub tag; commercial use permitted per tag) | TSAI reserves |
| rl-math-big-math | [SynthLabsAI/Big-Math-RL-Verified](https://huggingface.co/datasets/SynthLabsAI/Big-Math-RL-Verified) | English / Mathematics | Llama-3.1-405B (Llama) reformulated multiple-choice questions; Llama-3.1-70B filtered; Llama-3.1-8B/405B set the solve rates; gpt-4o-mini classified domains (paper, arXiv 2502.17387). Problems come from existing sets | apache-2.0 (Hub tag; commercial use permitted per tag) | excluded |
| rl-math-deepmath-103k | [zwhe99/DeepMath-103K](https://huggingface.co/datasets/zwhe99/DeepMath-103K) | English / Mathematics | DeepSeek-R1 (open weights) | mit (Hub tag; commercial use permitted per tag) | TSAI reserves |
---

## Dataset sections by G10 Core Team member (12)

### 1. Sai Teja (Lead) — StarCoder (`code-python` · `bigcode/starcoderdata`)

- **Core team:** 10. Post-training and Agentic (Lead) · **Week 2:** 9. Evaluation · **Week 3:** 12. Quantization and Serving
- **Set:** `code-python`
- **Language:** `Code`
- **Source:** `bigcode/starcoderdata`
- **Licence:** `other` — StarCoder training corpus drawn from The Stack; each file retains its upstream licence and attribution notice. Commercial use must follow per-file attribution terms.
- **Decision:** `TSAI reserves`

### 1b. Sai Teja (Lead) — Chandassu (`BodduSriPavan111/chandassu`)

- **Core team:** 10. Post-training and Agentic (Lead) · **Week 2:** 9. Evaluation · **Week 3:** 12. Quantization and Serving
- **Set:** `chandassu`
- **Language:** Telugu (`te`)
- **Source:** `BodduSriPavan111/chandassu` (4,651 padyams; eight metres in vruttamu, jaathi, and vupajaathi)
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
- **Source:** `HuggingFaceFW/fineweb-2` (Hugging Face, 2024; Common Crawl curated web pipeline)
- **Licence:** `ODC-By v1.0` (Open Data Commons Attribution License v1.0). Commercial use is explicitly permitted with attribution.
- **Decision:** `TSAI reserves` — commercial-use only rule satisfied. Attribution requirement to be fulfilled in the public model card and training datasheet. Raw data not committed to repository.

### 4. f20201351h-maker — StarCoder (`code-python` · `bigcode/starcoderdata`, assigned 500-document pack)

- **Core team:** 10. Post-training and Agentic · **Week 2:** 11. Release · **Week 3:** 6. Performance and Kernels
- **Set:** `code-python` (500-document pack; already in the Stage 0 table, so no new row)
- **Language:** `Code` (Python)
- **Source:** `bigcode/starcoderdata` on Hugging Face (gated; users accept its Terms of Use)
- **Generator model:** none (no LLM-generated text). The files are source code from public GitHub repositories; 12 of them are tool-generated code such as Django migrations.
- **Licence:** `other`, as on the dataset card. Users must abide by the terms of each file's original licence, including attribution.
- **What the pack shows (licence headers at the top of the 500 files):** Apache-2.0 45, MIT 16, BSD 6, GPL 6, LGPL 2, among the licence families that repeat in the pack. One-off headers were not classified, so other licences may still be present.
  **At least 8 files carry a GPL/LGPL header:**
  - GPL: `890651e4733e8944` (GPLv3+), `bcb288906f19d84d` (GPLv3+), `da1e1a24ce2d8184` (GPLv3), `1ba7834883790ea6` (GPLv2 with the Universal FOSS Exception), `b722cf3b05cb227a` (GPLv2), `e2c3db81526c288d` (GPLv2+).
  - LGPL: `6fbbb7afb4c34553` (LGPLv3+), `0f044ee517526307` (tri-licence MPL 1.1 / GPL 2.0 / LGPL 2.1).
- **Decision:** `TSAI reserves`.
  - Proposal: keep the permissive-licensed files (Apache-2.0, MIT, BSD). Keep each file's path and licence in a per-file manifest for attribution, because the `E4` cleaning medicine removes repeated licence headers from the text.
  - Flag the GPL/LGPL files for TSAI and drop them by default: the TSAI data rule lets in permissive licences and CC-BY-SA with attribution, and GPL/LGPL is neither. The licence follows the file, not the corpus (same finding as `code-go`, section 10).

### 5. Ashish Kamble — Dataset section *(placeholder for PR to `g10-week1-post-training`)*

- **Set:** *(TBD via PR)*
- **Language:** *(TBD via PR)*
- **Source:** *(TBD via PR)*
- **Licence:** *(TBD via PR)*
- **Decision:** `TSAI reserves`

### 6. Hema Varshini Palpandian — Tamil (`ind-ta-sangraha-v`)

- **Set:** `ind-ta-sangraha-v`
- **Language:** Tamil (`ta`; source split `tam`)
- **Source:** `ai4bharat/sangraha`, Verified Tamil subset.
- **Licence:** `CC-BY-4.0` — publisher-declared; permits commercial use with attribution, a licence link and notice of changes.
- **Decision:** `TSAI reserves` — source checks and SFT/RL selection pending.
- **Reading note:** 500 Tamil documents. No tested chat/tool markers found. Document URLs and the source release are missing from the sample; verify provenance before training.

### 7. Lokesh Arundathi — Kannada (`ind-kn-fw2`)

- **Set:** `ind-kn-fw2`
- **Language:** Kannada (`kn`)
- **Source:** `HuggingFaceFW/fineweb-2` (Hugging Face, 2024; Common Crawl curated web pipeline)
- **Licence:** `ODC-By v1.0` (Open Data Commons Attribution License v1.0). Commercial use is explicitly permitted with attribution.
- **Decision:** `TSAI reserves` — commercial-use only rule satisfied. Attribution requirement to be fulfilled in the public model card and training datasheet.

### 8. gmrammohan15 — Indic web (`ind-hi-hplt` · HPLT 3.0 `hin_Deva`)

- **Set:** `ind-hi-hplt`
- **Language:** `Hindi` (`hin_Deva`)
- **Source:** HPLT 3.0 monolingual, sorted release: `data.hplt-project.org/three/sorted/hin_Deva` (web crawl from Internet Archive and Common Crawl; catalogue at `hplt-project.org/datasets/v3.0`)
- **Licence:** `CC0-1.0` for the **packaging only**. HPLT's Terms of Use: "We do not own any of the text from which these text data has been extracted" and "We license the actual packaging of these text data under the Creative Commons CC0 license". The underlying web text keeps its original copyright (no per-document licence is given). HPLT 3.0 filters robots.txt opt-outs and removes sources on a takedown request in the next release.
- **Decision:** `TSAI reserves`. Commercial use of the collection is allowed (CC0). For the web text itself, treat it like every other web-crawl source: honour robots.txt opt-outs and takedown requests, keep each document's source URL so it can be removed, and do not redistribute raw text.

### 9. Ranjani Chandrasekaran — Indic web (`ind-hi-indiccorp`)

- **Set:** `ind-hi-indiccorp` — IndicCorpV2 Hindi subset (`data/hi-{1,2,3}.txt`)
- **Language:** Hindi (`hi`)
- **Source:** `ai4bharat/IndicCorpV2` (HuggingFace, AI4Bharat)
- **Licence:** CC-BY-4.0 — attribution required; commercial use permitted
- **Decision:** `TSAI reserves` (satisfies commercial-use rule via CC-BY-4.0 attribution; attribution to be carried in the model card)


### 10. Ravi Naik — Go (`code-go` · `bigcode/starcoderdata`)

- **Set:** `code-go`
- **Language:** Code (Go)
- **Source:** `bigcode/starcoderdata`, Go subset (500-document pack)
- **Licence:** `other` — Hub tag `license:other`, gated (auto-approval). StarCoder training corpus drawn from The Stack; each file keeps its upstream licence and attribution notice. Commercial use must follow per-file terms.
- **Decision:** `TSAI reserves`
- **Reading note:** 500 documents read. 53 start with a long licence header. One GPL file (`20331b3adb6eeb61`), one AGPL file (`83d8307ca8489972`) and one "free for personal use" file (`ab877ddc979bdd7d`) turned up, so licences must be filtered per file, not per corpus. Raw documents are not committed.

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

## Stage 1: SFT instruction mixture, candidate sets

Chat-formatted dialogues, reasoning traces and tool or agent trajectories for coding, Indic languages, math and science. Each entry has the standard fields, `TSAI reserves` as the decision (`excluded` where TSAI ruled a set out), and one line of opinion. Licence values are the Hugging Face tags read on 29 Oct 2026; a tag is not legal clearance. Per-dataset notes, 20-row samples and a benchmark-overlap check are in [team10-datasets](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets).

Eleven sets in the two stage sections are `excluded` (six named by TSAI, and five more where a closed OpenAI or Llama model made part of the data: `sft-code-magicoder-oss`, `sft-indic-indic-align`, `sft-math-numinamath-cot`, `sft-rl-code-rstar-coder`, `rl-math-big-math`), and two CC-BY-SA sets (`sft-math-nemotron-proofs`, `sft-math-nemotron-math-v2`) are `allowed (CC-BY-SA, attribution needed)` after TSAI's update that CC-BY-SA data is allowed with attribution. `rl-code-deepcoder` and `sft-science-nemotron-science` go to G9 (Evaluation) for a decontamination test before any use.

### `sft-code-commitpackft` — commitpackft

- **Stage:** SFT
- **Set:** `sft-code-commitpackft`
- **Language:** Code (350+ languages)
- **Source:** [`bigcode/commitpackft`](https://huggingface.co/datasets/bigcode/commitpackft)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** none (real GitHub commits)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Commit data with repo licences filtered upstream; low benchmark risk but untested.
- **Details and 20-row sample:** [bigcode__commitpackft](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/bigcode__commitpackft)

### `sft-code-self-oss-instruct` — self-oss-instruct-sc2-exec-filter-50k

- **Stage:** SFT
- **Set:** `sft-code-self-oss-instruct`
- **Language:** Code (Python)
- **Source:** [`bigcode/self-oss-instruct-sc2-exec-filter-50k`](https://huggingface.co/datasets/bigcode/self-oss-instruct-sc2-exec-filter-50k)
- **Licence:** `odc-by` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** The base model itself generates instructions, responses and tests in the SelfCodeAlign method (arXiv 2410.24198); StarCoder2-Instruct used StarCoder2-15B (from memory, the card is empty; verify)
- **Decision:** `TSAI reserves`
- **Our opinion:** use. Self-generated and execution-filtered. ODC-By needs attribution.
- **Details and 20-row sample:** [bigcode__self-oss-instruct-sc2-exec-filter-50k](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/bigcode__self-oss-instruct-sc2-exec-filter-50k)

### `sft-code-magicoder-oss` — Magicoder-OSS-Instruct-75K

- **Stage:** SFT
- **Set:** `sft-code-magicoder-oss`
- **Language:** Code (polyglot)
- **Source:** [`ise-uiuc/Magicoder-OSS-Instruct-75K`](https://huggingface.co/datasets/ise-uiuc/Magicoder-OSS-Instruct-75K)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** GPT-3.5 (OpenAI, closed)
- **Decision:** `excluded` — TSAI rule in the G10 chat (30 Oct): data made by closed OpenAI, Anthropic, Google or Llama models stays excluded. Applied by us to this set. Reason: Instructions were generated with GPT-3.5 (OpenAI, closed).
- **Our opinion:** excluded under that rule. Ask TSAI if a partial use (for example only the human-written parts) is acceptable.
- **Details and 20-row sample:** [ise-uiuc__Magicoder-OSS-Instruct-75K](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/ise-uiuc__Magicoder-OSS-Instruct-75K)

### `sft-code-codefeedback` — CodeFeedback-Filtered-Instruction

- **Stage:** SFT
- **Set:** `sft-code-codefeedback`
- **Language:** Code (polyglot)
- **Source:** [`m-a-p/CodeFeedback-Filtered-Instruction`](https://huggingface.co/datasets/m-a-p/CodeFeedback-Filtered-Instruction)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Mixed upstream sets (Magicoder, Evol-Instruct code); Qwen-72B-Chat used only as a filter
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Built from several instruction sets, one of them Evol-Instruct code. Check HumanEval/MBPP overlap.
- **Details and 20-row sample:** [m-a-p__CodeFeedback-Filtered-Instruction](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/m-a-p__CodeFeedback-Filtered-Instruction)

### `sft-rl-code-rstar-coder` — rStar-Coder

- **Stage:** SFT + RL
- **Set:** `sft-rl-code-rstar-coder`
- **Language:** Code (competitive)
- **Source:** [`microsoft/rStar-Coder`](https://huggingface.co/datasets/microsoft/rStar-Coder)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** GPT-4o (OpenAI, closed) for problem synthesis and test-input generators; QwQ-32B (open weights) for the long-reasoning solutions (paper, arXiv 2505.21297)
- **Decision:** `excluded` — TSAI rule in the G10 chat (30 Oct): data made by closed OpenAI, Anthropic, Google or Llama models stays excluded. Applied by us to this set. Reason: GPT-4o (OpenAI, closed) synthesized the problems and wrote the test-input generators.
- **Our opinion:** excluded under that rule. Ask TSAI if partial use is acceptable.
- **Details and 20-row sample:** [microsoft__rStar-Coder](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/microsoft__rStar-Coder)

### `sft-code-swe-rebench-openhands` — SWE-rebench-openhands-trajectories

- **Stage:** SFT
- **Set:** `sft-code-swe-rebench-openhands`
- **Language:** Code (agent trajectories)
- **Source:** [`nebius/SWE-rebench-openhands-trajectories`](https://huggingface.co/datasets/nebius/SWE-rebench-openhands-trajectories)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Qwen3-Coder-480B-A35B-Instruct (open weights) via OpenHands
- **Decision:** `TSAI reserves`
- **Our opinion:** use. OpenHands trajectories. Apply the same task-ID overlap check.
- **Details and 20-row sample:** [nebius__SWE-rebench-openhands-trajectories](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nebius__SWE-rebench-openhands-trajectories)

### `sft-code-nemotron-cp-v2` — Nemotron-SFT-Competitive-Programming-v2

- **Stage:** SFT
- **Set:** `sft-code-nemotron-cp-v2`
- **Language:** Code (competitive, SQL)
- **Source:** [`nvidia/Nemotron-SFT-Competitive-Programming-v2`](https://huggingface.co/datasets/nvidia/Nemotron-SFT-Competitive-Programming-v2)
- **Licence:** `cc-by-4.0, odc-by, mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Competitive subset: model not named on the card (NeMo-Skills pipeline; DeepSeek-R1-0528 is cited). Exercism subset: synthetic, model not named. Text-to-SQL: NVIDIA Data Designer, LLM not named
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Per-subset licences (CC-BY-4.0, ODC-By, MIT). The Exercism subset is decontaminated against Aider.
- **Details and 20-row sample:** [nvidia__Nemotron-SFT-Competitive-Programming-v2](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__Nemotron-SFT-Competitive-Programming-v2)

### `sft-code-nemotron-swe-v3` — Nemotron-SFT-SWE-v3

- **Stage:** SFT
- **Set:** `sft-code-nemotron-swe-v3`
- **Language:** Code (agent trajectories)
- **Source:** [`nvidia/Nemotron-SFT-SWE-v3`](https://huggingface.co/datasets/nvidia/Nemotron-SFT-SWE-v3)
- **Licence:** `cc-by-4.0, apache-2.0, mit, bsd-3-clause, bsd-2-clause` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Not on the card (it names only the OpenHands, SWE-agent and mini-SWE-agent harnesses). NVIDIA's Nemotron 3 Ultra paper names MiniMax-M2.5 and Qwen3-Coder-480B-A35B-Instruct (open weights) for its SWE trajectories; not tied to this set by the card, verify
- **Decision:** `TSAI reserves`
- **Our opinion:** use. Mixed permissive licences. Check overlap with the SWE-bench variants we report.
- **Details and 20-row sample:** [nvidia__Nemotron-SFT-SWE-v3](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__Nemotron-SFT-SWE-v3)

### `sft-code-nemotron-terminal` — Nemotron-Terminal-Corpus

- **Stage:** SFT
- **Set:** `sft-code-nemotron-terminal`
- **Language:** Code (terminal agent)
- **Source:** [`nvidia/Nemotron-Terminal-Corpus`](https://huggingface.co/datasets/nvidia/Nemotron-Terminal-Corpus)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** DeepSeek-V3.2 (open weights) for both the synthetic tasks and the trajectories (paper, arXiv 2602.21193)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. The teacher model is not stated on the card. Check Terminal-Bench overlap.
- **Details and 20-row sample:** [nvidia__Nemotron-Terminal-Corpus](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__Nemotron-Terminal-Corpus)

### `sft-code-opencodereasoning` — OpenCodeReasoning

- **Stage:** SFT
- **Set:** `sft-code-opencodereasoning`
- **Language:** Code (competitive)
- **Source:** [`nvidia/OpenCodeReasoning`](https://huggingface.co/datasets/nvidia/OpenCodeReasoning)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** DeepSeek-R1 (open weights)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. DeepSeek-R1-family traces, so check the teacher's terms. The card excludes the CodeContests and open-r1/codeforces test splits.
- **Details and 20-row sample:** [nvidia__OpenCodeReasoning](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__OpenCodeReasoning)

### `sft-code-opencodereasoning-2` — OpenCodeReasoning-2

- **Stage:** SFT
- **Set:** `sft-code-opencodereasoning-2`
- **Language:** Code (competitive)
- **Source:** [`nvidia/OpenCodeReasoning-2`](https://huggingface.co/datasets/nvidia/OpenCodeReasoning-2)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** DeepSeek-R1 for solutions, QwQ for critiques (both open weights)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Same teacher-terms check as OpenCodeReasoning.
- **Details and 20-row sample:** [nvidia__OpenCodeReasoning-2](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__OpenCodeReasoning-2)

### `sft-code-codeforces-cots` — codeforces-cots

- **Stage:** SFT
- **Set:** `sft-code-codeforces-cots`
- **Language:** Code (competitive)
- **Source:** [`open-r1/codeforces-cots`](https://huggingface.co/datasets/open-r1/codeforces-cots)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** DeepSeek-R1 (open weights)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. R1 traces on Codeforces problems. Use the `_decontaminated` configs.
- **Details and 20-row sample:** [open-r1__codeforces-cots](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/open-r1__codeforces-cots)

### `sft-indic-aya-collection` — aya_collection

- **Stage:** SFT
- **Set:** `sft-indic-aya-collection`
- **Language:** Multilingual incl. Indic
- **Source:** [`CohereLabs/aya_collection`](https://huggingface.co/datasets/CohereLabs/aya_collection)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Templated and translated from existing datasets; no single generator
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Templated tasks; the card does not state the source sets or model terms, and sub-dataset licences are unchecked.
- **Details and 20-row sample:** [CohereLabs__aya_collection](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/CohereLabs__aya_collection)

### `sft-indic-aya-dataset` — aya_dataset

- **Stage:** SFT
- **Set:** `sft-indic-aya-dataset`
- **Language:** Multilingual incl. Indic
- **Source:** [`CohereLabs/aya_dataset`](https://huggingface.co/datasets/CohereLabs/aya_dataset)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** None (human-written)
- **Decision:** `TSAI reserves`
- **Our opinion:** use. Human-written prompt/completion pairs under Apache-2.0 per the card. The cleanest Indic set found.
- **Details and 20-row sample:** [CohereLabs__aya_dataset](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/CohereLabs__aya_dataset)

### `sft-indic-indic-align` — indic-align

- **Stage:** SFT
- **Set:** `sft-indic-indic-align`
- **Language:** 14 Indic languages
- **Source:** [`ai4bharat/indic-align`](https://huggingface.co/datasets/ai4bharat/indic-align)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Llama-2-70B-Chat for many parts (Llama), plus translated human prompts; Mistral-7B in some parts
- **Decision:** `excluded` — TSAI rule in the G10 chat (30 Oct): data made by closed OpenAI, Anthropic, Google or Llama models stays excluded. Applied by us to this set. Reason: Many responses are Llama-2-70B-Chat outputs (Llama).
- **Our opinion:** excluded under that rule. Ask TSAI if a partial use (for example only the human-written parts) is acceptable.
- **Details and 20-row sample:** [ai4bharat__indic-align](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/ai4bharat__indic-align)

### `sft-indic-samvaad-hi` — samvaad-hi-v1

- **Stage:** SFT
- **Set:** `sft-indic-samvaad-hi`
- **Language:** Hindi, English, Hinglish
- **Source:** [`sarvamai/samvaad-hi-v1`](https://huggingface.co/datasets/sarvamai/samvaad-hi-v1)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Not stated on the card or in Sarvam's announcement; unknown
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. The card does not say which model wrote the replies.
- **Details and 20-row sample:** [sarvamai__samvaad-hi-v1](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/sarvamai__samvaad-hi-v1)

### `sft-indic-code-oss-codes-coding` — Coding-Conversational-Dataset-Indic

- **Stage:** SFT
- **Set:** `sft-indic-code-oss-codes-coding`
- **Language:** Indic (Hindi, Tamil, ...) + code
- **Source:** [`oss-codes/Coding-Conversational-Dataset-Indic`](https://huggingface.co/datasets/oss-codes/Coding-Conversational-Dataset-Indic)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Not stated; the card is empty
- **Decision:** `TSAI reserves`
- **Our opinion:** check. Small; origin and generator not verified.
- **Details and 20-row sample:** [oss-codes__Coding-Conversational-Dataset-Indic](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/oss-codes__Coding-Conversational-Dataset-Indic)

### `sft-indic-code-oss-codes-cs` — Computer-Science-Conversational-Dataset-Indic

- **Stage:** SFT
- **Set:** `sft-indic-code-oss-codes-cs`
- **Language:** Indic + computer science
- **Source:** [`oss-codes/Computer-Science-Conversational-Dataset-Indic`](https://huggingface.co/datasets/oss-codes/Computer-Science-Conversational-Dataset-Indic)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Not stated; the card is empty
- **Decision:** `TSAI reserves`
- **Our opinion:** check. Small; origin and generator not verified.
- **Details and 20-row sample:** [oss-codes__Computer-Science-Conversational-Dataset-Indic](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/oss-codes__Computer-Science-Conversational-Dataset-Indic)

### `sft-indic-math-orca-math-hi` — orca-math-word-problems-200k-hindi-filtered

- **Stage:** SFT
- **Set:** `sft-indic-math-orca-math-hi`
- **Language:** Hindi (math)
- **Source:** [`BhabhaAI/orca-math-word-problems-200k-hindi-filtered`](https://huggingface.co/datasets/BhabhaAI/orca-math-word-problems-200k-hindi-filtered)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** GPT-4 (OpenAI, closed) via Orca-Math, then translated
- **Decision:** `excluded` — TSAI ruling in the G10 chat (30 Oct): quarantined sets stay out of the lab and out of every training mix. Reason: Hindi translation of Orca-Math, which was generated with GPT-4, so OpenAI terms apply.
- **Our opinion:** excluded, as ruled by TSAI. Hindi translation of Orca-Math, which is GPT-4 generated, so OpenAI terms apply.
- **Details and 20-row sample:** [BhabhaAI__orca-math-word-problems-200k-hindi-filtered](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/BhabhaAI__orca-math-word-problems-200k-hindi-filtered)

### `sft-indic-math-aryabhatta-orca-hi` — Aryabhatta-Orca-Maths-Hindi

- **Stage:** SFT
- **Set:** `sft-indic-math-aryabhatta-orca-hi`
- **Language:** Hindi (math)
- **Source:** [`GenVRadmin/Aryabhatta-Orca-Maths-Hindi`](https://huggingface.co/datasets/GenVRadmin/Aryabhatta-Orca-Maths-Hindi)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** GPT-4 (OpenAI, closed) via Orca-Math, then translated
- **Decision:** `excluded` — TSAI ruling in the G10 chat (30 Oct): quarantined sets stay out of the lab and out of every training mix. Reason: Hindi translation of Orca-Math, which was generated with GPT-4, so OpenAI terms apply.
- **Our opinion:** excluded, as ruled by TSAI. Hindi translation of Orca-Math, which is GPT-4 generated, so OpenAI terms apply.
- **Details and 20-row sample:** [GenVRadmin__Aryabhatta-Orca-Maths-Hindi](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/GenVRadmin__Aryabhatta-Orca-Maths-Hindi)

### `sft-math-nemotron-proofs` — Nemotron-Math-Proofs-v1

- **Stage:** SFT
- **Set:** `sft-math-nemotron-proofs`
- **Language:** English / Mathematics
- **Source:** [`nvidia/Nemotron-Math-Proofs-v1`](https://huggingface.co/datasets/nvidia/Nemotron-Math-Proofs-v1)
- **Licence:** `cc-by-sa-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** gpt-oss-120b (statement formalisation) and Goedel-Prover-V2-32B (proofs)
- **Decision:** `allowed (CC-BY-SA, attribution needed)` — TSAI ruling (G10 chat, 30 Oct): CC-BY-SA data is allowed with attribution when a permissive model made it, and data made by gpt-oss models is allowed because the weights are open under Apache-2.0; data made by closed OpenAI, Anthropic, Google or Llama models stays excluded. Statements were formalized by gpt-oss-120b (open-weight, Apache-2.0) and proofs attempted by Goedel-Prover-V2-32B; no OpenAI API or Llama outputs.
- **Our opinion:** use. CC-BY-SA-4.0: carry attribution and keep the share-alike terms.
- **Details and 20-row sample:** [nvidia__Nemotron-Math-Proofs-v1](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__Nemotron-Math-Proofs-v1)

### `sft-math-nemotron-math-v2` — Nemotron-Math-v2

- **Stage:** SFT
- **Set:** `sft-math-nemotron-math-v2`
- **Language:** English / Mathematics
- **Source:** [`nvidia/Nemotron-Math-v2`](https://huggingface.co/datasets/nvidia/Nemotron-Math-v2)
- **Licence:** `cc-by-4.0, cc-by-sa-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** gpt-oss-120b (all solution traces)
- **Decision:** `allowed (CC-BY-SA, attribution needed)` — TSAI ruling (G10 chat, 30 Oct): CC-BY-SA data is allowed with attribution when a permissive model made it, and data made by gpt-oss models is allowed because the weights are open under Apache-2.0; data made by closed OpenAI, Anthropic, Google or Llama models stays excluded. All solution traces came from gpt-oss-120b (open-weight, Apache-2.0); the AoPS part is CC-BY-4.0 and the StackExchange and MathGenSelect parts are CC-BY-SA-4.0.
- **Our opinion:** use, with attribution. The card says it is decontaminated.
- **Details and 20-row sample:** [nvidia__Nemotron-Math-v2](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__Nemotron-Math-v2)

### `sft-math-openmathinstruct-2` — OpenMathInstruct-2

- **Stage:** SFT
- **Set:** `sft-math-openmathinstruct-2`
- **Language:** English / Mathematics
- **Source:** [`nvidia/OpenMathInstruct-2`](https://huggingface.co/datasets/nvidia/OpenMathInstruct-2)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Llama-3.1-405B-Instruct (Llama)
- **Decision:** `excluded` — TSAI ruling in the G10 chat (30 Oct): quarantined sets stay out of the lab and out of every training mix. Reason: Solutions were generated with Llama-3.1-405B, and the Llama licence limits using its outputs to train other models.
- **Our opinion:** excluded, as ruled by TSAI. Generated with Llama-3.1-405B, so Llama licence terms apply. Built from GSM8K and MATH train problems.
- **Details and 20-row sample:** [nvidia__OpenMathInstruct-2](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__OpenMathInstruct-2)

### `sft-rl-math-openmathreasoning` — OpenMathReasoning

- **Stage:** SFT + RL prompts
- **Set:** `sft-rl-math-openmathreasoning`
- **Language:** English / Mathematics
- **Source:** [`nvidia/OpenMathReasoning`](https://huggingface.co/datasets/nvidia/OpenMathReasoning)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** DeepSeek-R1 and QwQ-32B (open weights)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Traces from DeepSeek-R1 and QwQ, so check teacher terms. The card says benchmark decontamination was applied.
- **Details and 20-row sample:** [nvidia__OpenMathReasoning](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__OpenMathReasoning)

### `sft-math-openr1-math` — OpenR1-Math-220k

- **Stage:** SFT
- **Set:** `sft-math-openr1-math`
- **Language:** English / Mathematics
- **Source:** [`open-r1/OpenR1-Math-220k`](https://huggingface.co/datasets/open-r1/OpenR1-Math-220k)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** DeepSeek-R1 (open weights)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. R1 traces on NuminaMath 1.5 problems, so it inherits the NuminaMath overlap.
- **Details and 20-row sample:** [open-r1__OpenR1-Math-220k](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/open-r1__OpenR1-Math-220k)

### `sft-math-numinamath-1.5` — NuminaMath-1.5

- **Stage:** SFT
- **Set:** `sft-math-numinamath-1.5`
- **Language:** English / Mathematics
- **Source:** [`project-numina/NuminaMath-1.5`](https://huggingface.co/datasets/project-numina/NuminaMath-1.5)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Mixed; solutions from the source datasets, no single generator stated
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Sources include amc_aime and olympiads with no decontamination stated; web-scraped problem text may not be covered by the dataset licence.
- **Details and 20-row sample:** [project-numina__NuminaMath-1.5](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/project-numina__NuminaMath-1.5)

### `sft-math-numinamath-cot` — NuminaMath-CoT

- **Stage:** SFT
- **Set:** `sft-math-numinamath-cot`
- **Language:** English / Mathematics
- **Source:** [`project-numina/NuminaMath-CoT`](https://huggingface.co/datasets/project-numina/NuminaMath-CoT)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** GPT-4 (OpenAI, closed) rewrote solutions into chain-of-thought; GPT-4o was used for the tool-integrated set (secondary sources, not on the card; verify)
- **Decision:** `excluded` — TSAI rule in the G10 chat (30 Oct): data made by closed OpenAI, Anthropic, Google or Llama models stays excluded. Applied by us to this set. Reason: Solutions were rewritten with GPT-4 / GPT-4o (OpenAI, closed).
- **Our opinion:** excluded under that rule. Ask TSAI if a partial use (for example only the human-written parts) is acceptable.
- **Details and 20-row sample:** [project-numina__NuminaMath-CoT](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/project-numina__NuminaMath-CoT)

### `sft-stem-code-nemotron-post-v1` — Nemotron-Post-Training-Dataset-v1

- **Stage:** SFT
- **Set:** `sft-stem-code-nemotron-post-v1`
- **Language:** English / Math, STEM, Code
- **Source:** [`nvidia/Nemotron-Post-Training-Dataset-v1`](https://huggingface.co/datasets/nvidia/Nemotron-Post-Training-Dataset-v1)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** DeepSeek-R1-0528 and Qwen3-235B-A22B (open weights); Llama-3.3-Nemotron-Super is the model it was built to train
- **Decision:** `excluded` — TSAI ruling in the G10 chat (30 Oct): quarantined sets stay out of the lab and out of every training mix. Reason: Responses come from Qwen and DeepSeek teacher models; gated, and prompt provenance is not cleared.
- **Our opinion:** excluded, as ruled by TSAI. Responses come from Qwen and DeepSeek models, so check their terms. Some prompts must be fetched separately from their original sources under their own terms.
- **Details and 20-row sample:** [nvidia__Nemotron-Post-Training-Dataset-v1](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__Nemotron-Post-Training-Dataset-v1)

### `sft-stem-code-nemotron-post-v2` — Nemotron-Post-Training-Dataset-v2

- **Stage:** SFT
- **Set:** `sft-stem-code-nemotron-post-v2`
- **Language:** Multilingual / Math, STEM, Code
- **Source:** [`nvidia/Nemotron-Post-Training-Dataset-v2`](https://huggingface.co/datasets/nvidia/Nemotron-Post-Training-Dataset-v2)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026; gated dataset. A tag is not legal clearance.
- **Generator model:** DeepSeek-R1-0528, Qwen3-235B-A22B, Qwen3-30B-A3B (open weights), Qwen2.5-14B-Instruct and Qwen2.5-32B-Instruct-AWQ; the card does not map models to subsets (read from the Hub page, not the gated files)
- **Decision:** `excluded` — TSAI ruling in the G10 chat (30 Oct): quarantined sets stay out of the lab and out of every training mix. Reason: Responses come from Qwen and DeepSeek teacher models; gated, and prompt provenance is not cleared.
- **Our opinion:** excluded, as ruled by TSAI. Gated so the card was not read. Earlier notes say models trained on it may fall under Qwen and DeepSeek licences.
- **Details and 20-row sample:** [nvidia__Nemotron-Post-Training-Dataset-v2](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__Nemotron-Post-Training-Dataset-v2)

### `sft-stem-code-openthoughts3` — OpenThoughts3-1.2M

- **Stage:** SFT
- **Set:** `sft-stem-code-openthoughts3`
- **Language:** English / Math, Code, Science
- **Source:** [`open-thoughts/OpenThoughts3-1.2M`](https://huggingface.co/datasets/open-thoughts/OpenThoughts3-1.2M)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** QwQ-32B (open weights)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Mixed question sources; no decontamination stated on the card.
- **Details and 20-row sample:** [open-thoughts__OpenThoughts3-1.2M](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/open-thoughts__OpenThoughts3-1.2M)

### `sft-science-nemotron-science` — Nemotron-Science-v1

- **Stage:** SFT
- **Set:** `sft-science-nemotron-science`
- **Language:** English / Science
- **Source:** [`nvidia/Nemotron-Science-v1`](https://huggingface.co/datasets/nvidia/Nemotron-Science-v1)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** gpt-oss-120b (open weights)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. Generated with GPT-OSS-120B (open-weight). Questions mimic GPQA style, so run a near-duplicate check against GPQA. Per TSAI, the source name goes to G9 (Evaluation) for a decontamination test; no use before that.
- **Details and 20-row sample:** [nvidia__Nemotron-Science-v1](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nvidia__Nemotron-Science-v1)


## Stage 2: Preference optimization and RLVR, candidate sets

Verifiable-answer and test-based sets for RL (math, code, SWE tasks). Each entry has the standard fields, `TSAI reserves` as the decision (`excluded` where TSAI ruled a set out), and one line of opinion. Licence values are the Hugging Face tags read on 29 Oct 2026; a tag is not legal clearance. Per-dataset notes, 20-row samples and a benchmark-overlap check are in [team10-datasets](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets).

### `rl-code-r2e-gym` — R2E-Gym-Subset

- **Stage:** RL
- **Set:** `rl-code-r2e-gym`
- **Language:** Code (Python SWE)
- **Source:** [`R2E-Gym/R2E-Gym-Subset`](https://huggingface.co/datasets/R2E-Gym/R2E-Gym-Subset)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Not named in the paper's main text (tests and issues are LLM-generated by back-translation from commits, arXiv 2504.07164); check its appendix
- **Decision:** `TSAI reserves`
- **Our opinion:** use. Permissive tag, SWE tasks with tests. Compare the repos with SWE-bench repos.
- **Details and 20-row sample:** [R2E-Gym__R2E-Gym-Subset](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/R2E-Gym__R2E-Gym-Subset)

### `rl-code-swe-gym` — SWE-Gym

- **Stage:** RL
- **Set:** `rl-code-swe-gym`
- **Language:** Code (Python SWE)
- **Source:** [`SWE-Gym/SWE-Gym`](https://huggingface.co/datasets/SWE-Gym/SWE-Gym)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** None (real GitHub issues and tests)
- **Decision:** `TSAI reserves`
- **Our opinion:** use. The Python repos keep their own licences. Compare the 11 repos with SWE-bench.
- **Details and 20-row sample:** [SWE-Gym__SWE-Gym](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/SWE-Gym__SWE-Gym)

### `rl-code-acecode-87k` — AceCode-87K

- **Stage:** RL
- **Set:** `rl-code-acecode-87k`
- **Language:** Code (Python)
- **Source:** [`TIGER-Lab/AceCode-87K`](https://huggingface.co/datasets/TIGER-Lab/AceCode-87K)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** GPT-4o-mini (OpenAI, closed) rewrote the questions
- **Decision:** `excluded` — TSAI ruling in the G10 chat (30 Oct): quarantined sets stay out of the lab and out of every training mix. Reason: Questions were rewritten by GPT-4o-mini, so OpenAI terms apply.
- **Our opinion:** excluded, as ruled by TSAI. Tests per problem. Questions were rewritten by GPT-4o-mini, so OpenAI terms apply to that text. Check HumanEval/MBPP overlap.
- **Details and 20-row sample:** [TIGER-Lab__AceCode-87K](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/TIGER-Lab__AceCode-87K)

### `rl-code-deepcoder` — DeepCoder-Preview-Dataset

- **Stage:** RL
- **Set:** `rl-code-deepcoder`
- **Language:** Code (competitive)
- **Source:** [`agentica-org/DeepCoder-Preview-Dataset`](https://huggingface.co/datasets/agentica-org/DeepCoder-Preview-Dataset)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** None (problems and tests collected from existing sets)
- **Decision:** `TSAI reserves`
- **Our opinion:** use, `train` only. The training set holds 600 LiveCodeBench problems from before 1 Aug 2024 and the `test` data is LiveCodeBench plus CodeElo. Per TSAI, the source name goes to G9 (Evaluation) for a decontamination test; no use before that.
- **Details and 20-row sample:** [agentica-org__DeepCoder-Preview-Dataset](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/agentica-org__DeepCoder-Preview-Dataset)

### `rl-code-swe-rebench-v2` — SWE-rebench-V2

- **Stage:** RL
- **Set:** `rl-code-swe-rebench-v2`
- **Language:** Code (20 languages incl. Go)
- **Source:** [`nebius/SWE-rebench-V2`](https://huggingface.co/datasets/nebius/SWE-rebench-V2)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Qwen3-Coder-480B-A35B-Instruct (installation agent, log parsing); quality labels from an ensemble of gpt-oss-120b, GLM-4.7 and DeepSeek-V3.2 (paper, arXiv 2602.23866)
- **Decision:** `TSAI reserves`
- **Our opinion:** use. The card warns that only the original SWE-bench repos were excluded. Remove task IDs that overlap with our eval set.
- **Details and 20-row sample:** [nebius__SWE-rebench-V2](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/nebius__SWE-rebench-V2)

### `rl-code-codeforces` — codeforces

- **Stage:** RL
- **Set:** `rl-code-codeforces`
- **Language:** Code (competitive)
- **Source:** [`open-r1/codeforces`](https://huggingface.co/datasets/open-r1/codeforces)
- **Licence:** `cc-by-4.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** None (Codeforces problems); the card mentions DeepSeek-R1 only for generated test inputs
- **Decision:** `TSAI reserves`
- **Our opinion:** use, check. The Codeforces problem text may not be covered by the dataset licence (header CC-BY-4.0, body ODC-By 4.0). Use `train` only.
- **Details and 20-row sample:** [open-r1__codeforces](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/open-r1__codeforces)

### `rl-math-dapo-17k` — DAPO-Math-17k

- **Stage:** RL
- **Set:** `rl-math-dapo-17k`
- **Language:** English / Mathematics
- **Source:** [`BytedTsinghua-SIA/DAPO-Math-17k`](https://huggingface.co/datasets/BytedTsinghua-SIA/DAPO-Math-17k)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** Problems scraped from the web and competition sites; an unnamed LLM rewrote questions so the answer is an integer (paper, arXiv 2503.14476)
- **Decision:** `TSAI reserves`
- **Our opinion:** use. Verifiable answers. Check AIME and MATH-500 overlap.
- **Details and 20-row sample:** [BytedTsinghua-SIA__DAPO-Math-17k](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/BytedTsinghua-SIA__DAPO-Math-17k)

### `rl-math-big-math` — Big-Math-RL-Verified

- **Stage:** RL
- **Set:** `rl-math-big-math`
- **Language:** English / Mathematics
- **Source:** [`SynthLabsAI/Big-Math-RL-Verified`](https://huggingface.co/datasets/SynthLabsAI/Big-Math-RL-Verified)
- **Licence:** `apache-2.0` — Hugging Face tag read on 29 Oct 2026; gated dataset. A tag is not legal clearance.
- **Generator model:** Llama-3.1-405B (Llama) reformulated multiple-choice questions; Llama-3.1-70B filtered; Llama-3.1-8B/405B set the solve rates; gpt-4o-mini classified domains (paper, arXiv 2502.17387). Problems come from existing sets
- **Decision:** `excluded` — TSAI rule in the G10 chat (30 Oct): data made by closed OpenAI, Anthropic, Google or Llama models stays excluded. Applied by us to this set. Reason: Llama-3.1-405B (Llama) reformulated the multiple-choice questions.
- **Our opinion:** excluded under that rule. Ask TSAI if partial use is acceptable.
- **Details and 20-row sample:** [SynthLabsAI__Big-Math-RL-Verified](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/SynthLabsAI__Big-Math-RL-Verified)

### `rl-math-deepmath-103k` — DeepMath-103K

- **Stage:** RL (and SFT)
- **Set:** `rl-math-deepmath-103k`
- **Language:** English / Mathematics
- **Source:** [`zwhe99/DeepMath-103K`](https://huggingface.co/datasets/zwhe99/DeepMath-103K)
- **Licence:** `mit` — Hugging Face tag read on 29 Oct 2026. A tag is not legal clearance.
- **Generator model:** DeepSeek-R1 (open weights)
- **Decision:** `TSAI reserves`
- **Our opinion:** use. The card says it was decontaminated against common benchmarks.
- **Details and 20-row sample:** [zwhe99__DeepMath-103K](https://github.com/RaviNaik/ERA/tree/main/v5/capstone/team10-datasets/zwhe99__DeepMath-103K)


## Strategy v0

- **Commercial-use data only:** Any dataset or file whose licence is missing or restricts commercial use is excluded.
- **Decision authority:** `TSAI reserves` all dataset release and retention decisions across all members.
- **Repository hygiene:** Raw Parquet, Arrow, or binary training files never enter `era-v5-lab` (enforced by `pr-guard`).
- **Token & effort rules:** 256 reserved special tokens (`0..255`) and four plain-text effort levels (`1k`, `4k`, `16k`, `64k`).
- **Benchmark decontamination protocol:** All training splits (code and text) must be programmatically decontaminated against evaluation benchmarks (SWE-bench, HumanEval, MBPP, LiveCodeBench, BigCodeBench) using 13-gram exact match and embedding-similarity filtering prior to post-training.
- **Provenance & attribution ledger:** Every permissive dataset (ODC-By, CC-BY, Apache-2.0, MIT, Stack per-file notices) has its snapshot timestamp, source repository URL, and licensing terms recorded for automatic aggregation into the release model card.
- **Right-to-be-forgotten & takedown handling:** For curated web crawls (FineWeb-2, HPLT 3.0), maintain source URL manifests to fulfill upstream robots.txt exclusions, DMCA notices, and GDPR Article 17 deletion requests across training checkpoint iterations.
- **Excluded sets:** A set that TSAI rules out is marked `excluded` in the table with the reason, stays listed, and is never used in a training mix. CC-BY-SA data made by a permissive model is `allowed (CC-BY-SA, attribution needed)`; attribution goes in the model card. Sets that need a decontamination test go to G9 (Evaluation) first.
