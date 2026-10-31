# Special tokens v1 (Final Consolidated Allocation)

Shared G10 special-token allocation file (`teams/10-post-training/special-tokens/special_tokens_v1.md`).  
Prepared for **Team 3 (G3 Tokenizer)**, **Team 4 (G4 KE2)**, and **Team 9 (G9 Evaluation)** for the **Saturday 31 Oct** milestone, ahead of G3 tokenizer training commencing on **1 Nov**.

---

## 1. Core Architecture & Frontier Security Policy

- **ChatML Foundation**: Structural turns delimited by atomic tokens `<|im_start|>` and `<|im_end|>`. Document boundaries closed with `<|endoftext|>`.
- **Structural vs. Value Plane Separation (27 Oct Ruling)**:
  - Special tokens are strictly reserved for structural delimiters that the model must never confuse with normal text.
  - Variable values (reasoning effort, tool names, parameters, options) remain plain text inside the structure.
  - Reasoning effort is conditioned via the plain-text system line: `Reasoning effort: {1k|4k|16k|64k}`.
- **256 Reserved Token IDs (`000..255`)**: G3 reserves the entire 256-ID block in the BPE/Unigram vocabulary. Every assigned token below is mapped to exactly one atomic token ID (never split into subwords).
- **Security-First Anti-Smuggling Defenses**:
  - **Unicode Normalization (NFKC)**: Pre-tokenization canonicalization is mandatory to eliminate homoglyph smuggling, zero-width obfuscation (`U+200B..U+200D`), and fullwidth delimiter look-alikes (`<｜...｜>`).
  - **Strict Delimiter Isolation**: Untrusted user and tool text must never resolve to assigned or reserved token IDs.

---

## 2. Consolidated 256-Token Block for Team 3 (G3)

TSAI reserves 256 token IDs (`000..255`).

| Token ID | Name | Special Token Surface (Atomic) | Semantic Role & Privilege Plane |
| :--- | :--- | :--- | :--- |
| `000` | `endoftext` | `<\|endoftext\|>` | End of document / transcript boundary |
| `001` | `im_start` | `<\|im_start\|>` | Start of ChatML turn (`system`, `user`, `assistant`, `tool`) |
| `002` | `im_end` | `<\|im_end\|>` | End of ChatML turn |
| `010` | `fim_prefix` | `<\|fim_prefix\|>` | Fill-In-The-Middle prefix anchor for code infilling |
| `011` | `fim_middle` | `<\|fim_middle\|>` | Fill-In-The-Middle middle target slot for code infilling |
| `012` | `fim_suffix` | `<\|fim_suffix\|>` | Fill-In-The-Middle suffix context anchor |
| `013` | `repo_name` | `<\|repo_name\|>` | Repository / package identifier anchor in multi-file context |
| `014` | `file_sep` | `<\|file_sep\|>` | Multi-file boundary delimiter in workspace repo map |
| `015` | `subagent_call` | `<\|subagent_call\|>` | Sub-agent / delegation invocation boundary |
| `016` | `fim_pad` | `<\|fim_pad\|>` | Fill-In-The-Middle padding token for batched infilling sequences |
| `020` | `subagent_return` | `<\|subagent_return\|>` | Sub-agent / delegation return boundary |
| `024` | `think` | `<\|think\|>` | Start of Chain-of-Thought reasoning trace |
| `025` | `think_end` | `<\|/think\|>` | End of Chain-of-Thought reasoning trace |
| `026` | `tool_call` | `<\|tool_call\|>` | Start of structured JSON tool call payload |
| `027` | `tool_call_end` | `<\|/tool_call\|>` | End of structured JSON tool call payload |
| `028` | `tool_result` | `<\|tool_result\|>` | Start of tool execution output (untrusted environment) |
| `029` | `tool_result_end` | `<\|/tool_result\|>` | End of tool execution output (untrusted environment) |

All remaining IDs in `000..255` (`003..009`, `017..019`, `021..023`, `030..255`) are reserved by TSAI as `<|reserved_NNN|>`. IDs `021` to `023` stay reserved and unused. Do not add `<|eval_fp_*|>`. A fingerprint stays a plain-text canary in Team 9 eval data.

---

## 3. Machine-Readable Table for Tokenizer Training (G3)

```text
000 endoftext <|endoftext|>
001 im_start <|im_start|>
002 im_end <|im_end|>
010 fim_prefix <|fim_prefix|>
011 fim_middle <|fim_middle|>
012 fim_suffix <|fim_suffix|>
013 repo_name <|repo_name|>
014 file_sep <|file_sep|>
015 subagent_call <|subagent_call|>
016 fim_pad <|fim_pad|>
020 subagent_return <|subagent_return|>
024 think <|think|>
025 think_end <|/think|>
026 tool_call <|tool_call|>
027 tool_call_end <|/tool_call|>
028 tool_result <|tool_result|>
029 tool_result_end <|/tool_result|>
```

Unassigned slots `003..009`, `017..023`, and `030..255` are mapped to:
```text
003 reserved_003 <|reserved_003|>
...
255 reserved_255 <|reserved_255|>
```

---

## 4. Dataset Pre-Training Sanity & Ghost Token Action

1. **StarCoder (`code-python` · Sai Teja)**: Strip upstream `B3` ghost tokens (`[INST]`, `[/INST]`, `<think>`, `### Assistant:`) during pre-processing so raw control markers are never learned from pre-training code comments.
2. **HPLT 3.0 (`ind-hi-hplt` · gmrammohan15)**: Verified clean. Devanagari script joiners `U+200D` (ZWJ) and `U+200C` (ZWNJ) retained as natural script characters.
3. **IndicCorpV2 (`ind-hi-indiccorp` · Ranjani)**: Verified clean. No ghost tokens found.
4. **FineWeb-2 Marathi (`ind-mr-fw2` · Amit T)**: Verified clean. Zero ghost tokens. ZWJ/ZWNJ preserved for Marathi orthography (`ऱ्या`, conjuncts).
5. **FineWeb-2 Kannada (`ind-kn-fw2` · Lokesh Arundathi)**: No new token request or allocation change. Preserve vowel sequences, ZWNJ (`U+200C`) and ZWJ (`U+200D`) as text, including the Unicode RA + ZWJ + virama order and its legacy alternative.
6. **StarCoder (`code-python` · f20201351h-maker, assigned 500-document pack)**: No ghost chat markers found (0 of 500 documents). Strip the StarCoder metadata prefix (`<reponame>`, `<filename>`, `<gh_stars>`, 272 documents) in cleaning. PII placeholders (`<NAME>`, `<EMAIL>`, `<PASSWORD>`, `<KEY>`) stay plain text. No new token request.
