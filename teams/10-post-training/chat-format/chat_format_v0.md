# Chat format v0

Team G10. ChatML-style template for Team 3 (G3 Tokenizer) and Team 12 (G12 Quantization and Serving) by Saturday 31 Oct.

## Core rule: special tokens for structure, plain text for values

Instructor ruling, 27 Oct (reply to the special-tokens discussion in the G10 chat):

- **Special tokens** only for structure that the model must never confuse with normal text: the start and end of each role turn, tool call start and end, tool result start and end, and thinking start and end.
- **Plain text** for values inside that structure: tool names, arguments, effort level, options and settings. A tool call is special tokens around plain-text JSON.
- Keep the special-token list short. Sai Teja owns the final list, and TSAI reviews it at the Gate.

Markers in `v0` (each is one atomic special token in the tokenizer, never split into pieces):

- Turn & document markers: `<|endoftext|>` (`000`), `<|im_start|>` (`001`), `<|im_end|>` (`002`)
- Reasoning & tool markers: `<|think|>` (`024`), `<|/think|>` (`025`), `<|tool_call|>` (`026`), `<|/tool_call|>` (`027`), `<|tool_result|>` (`028`), `<|/tool_result|>` (`029`)

Effort is **not** a token. It is a plain-text line, `Reasoning effort: {level}`, at the top of the first system turn. Levels are `1k`, `4k`, `16k` and `64k` (budgets of `1024`, `4096`, `16384` and `65536` tokens covering think + tool trace, excluding the final visible reply).

- Plain-text XML look-alikes and Unicode homoglyphs (`<think>`, `</think>`, `<tool_call>`, `</tool_call>`, `<tool_result>`, `</tool_result>`, `<｜think｜>`, `＜think＞`) are strictly rejected by `render.py`.
- All 9 assigned markers and 247 reserved slots (`0..255`) are listed in `teams/10-post-training/special-tokens/special_tokens_v0.md` for Team 3 (G3) to reserve by Saturday 31 Oct.

## Multi-Tier Context Hierarchy & RBAC Privilege Planes

In frontier agentic coding, context is structured into four deterministic tiers:
1. **Tier 0 (System Directives & RBAC Boundaries - P0):** Core model identity, safety guardrails, and reasoning effort conditioning line (`Reasoning effort: {level}`). Fixed by application host; untrusted user/tool data cannot alter.
2. **Tier 1 (Capabilities & Tool Registry - P0/P1):** Injected tool schemas, `SKILL.md` workflows, and capability descriptions formatted in structured JSON/Markdown.
3. **Tier 2 (Project & Workspace Map - P1):** Active git status, directory tree, and file boundaries (`<|file_sep|>`) defining the environment state.
4. **Tier 3 (Conversation History - P1):** Prior user requests and model interactions.
5. **Tier 4 (Working Memory & Execution - P2/P3):** Internal Chain-of-Thought reasoning traces (`<|think|>...<|/think|>`) and untrusted tool outputs (`<|tool_result|>...<|/tool_result|>`).

### Context Sizing & Effort Budgets
Reasoning effort budgets (`1k` = 1,024, `4k` = 4,096, `16k` = 16,384, `64k` = 65,536 tokens) constrain *only* the think span and tool trace. For a `64k` effort budget, the total serving context window must scale to at least **128k tokens** (aligned with Teams 3, 5, and 12).

## Turn structure

Roles are `system`, `user`, `assistant`, and `tool`.

1. **First turn is always `system`:**
   `<|im_start|>system\nReasoning effort: {level}\n\n{system content}<|im_end|>\n`
   If the transcript has no system message, the turn holds only the effort line. Other `system` and `user` turns are `<|im_start|>{role}\n{content}<|im_end|>\n`.
2. **`assistant` turn:**
   `<|im_start|>assistant\n`, then, in order and omitting empty optional sections:
   - Optional reasoning span wrapped in atomic special tokens: `<|think|>\n{think}\n<|/think|>\n`
   - Zero or more tool calls, each wrapped in atomic special tokens around plain-text JSON: `<|tool_call|>\n{"arguments":{...},"id":"...","name":"..."}\n<|/tool_call|>\n`
   - Optional visible reply text: `{content}`
   Closed by `<|im_end|>\n`.
   *(Tool calls optionally include an `"id"` field to deterministically bind parallel tool invocations).*
3. **`tool` turn:**
   `<|im_start|>tool\n<|tool_result|>\n{content}\n<|/tool_result|><|im_end|>\n` (tool output `content` is required).
4. **End of transcript:**
   `<|endoftext|>`

`render.py` renders messages to a string, `parse()` reconstructs the messages and effort level, and `tokenize_markers()` splits a rendered transcript into atomic special-token IDs (`0..255`) and text spans to verify that no marker is ever left as plain text.

One edge case: a first system message with empty content renders as the effort line only, so `parse()` returns no system message for it.

## Example

Effort `4k`.

```text
<|im_start|>system
Reasoning effort: 4k

You edit code and you report only what a tool returned.<|im_end|>
<|im_start|>user
test_add fails in calc.py. Fix add.<|im_end|>
<|im_start|>assistant
<|think|>
The return adds one too many.
<|/think|>
<|tool_call|>
{"arguments":{"path":"calc.py"},"name":"read_file"}
<|/tool_call|>
I am reading calc.py before editing it.<|im_end|>
<|im_start|>tool
<|tool_result|>
def add(a, b):
    return a + b + 1

<|/tool_result|><|im_end|>
<|im_start|>assistant
<|tool_call|>
{"arguments":{"patch":"return a + b","path":"calc.py"},"name":"apply_patch"}
<|/tool_call|>
Removed the extra increment.<|im_end|>
<|endoftext|>
```

## Tamil application — `ind-ta-sangraha-v`

The existing format and `render.py` apply to Tamil without language-specific control tokens. The examples below are newly authored demonstrations, not extracted Sangraha documents or approved training rows.

- Read and write UTF-8. Preserve content exactly, including combining sequences, pulli, ZWJ/ZWNJ if present, punctuation, mixed-script spans and whitespace. Rendering does not normalize, translate, repair or clean source text.
- Use the same `system`, `user`, `assistant`, `tool` role strings and the same nine markers. Tamil text belongs in content and tool JSON string values. `ta`, `tam`, effort values, tool names and arguments are plain text.
- For the current v0 demo, use one tool call followed by one tool result. The renderer does not preserve call IDs or tool-name metadata, so parallel tool/result correlation needs a later schema decision.

Example input to the shared Python module:

```python
messages = [
    {"role": "system", "content": "தமிழில் பதிலளி."},
    {"role": "user", "content": "தமிழ் உரையை UTF-8 கோப்பில் சேமி."},
    {"role": "assistant", "tool_calls": [
        {"name": "write_text", "arguments": {
            "path": "message.txt", "text": "தமிழ் மொழி"}}
    ]},
    {"role": "tool", "content": "UTF-8 write completed."},
    {"role": "assistant", "content": "தமிழ் உரை சேமிக்கப்பட்டது."},
]
text = render(messages, effort="4k")
assert parse(text) == {"effort": "4k", "messages": messages}
```

Rendered excerpt:

```text
<|im_start|>user
தமிழ் உரையை UTF-8 கோப்பில் சேமி.<|im_end|>
<|im_start|>assistant
<|tool_call|>
{"arguments":{"path":"message.txt","text":"தமிழ் மொழி"},"name":"write_text"}
<|/tool_call|>
<|im_end|>
<|im_start|>tool
<|tool_result|>
UTF-8 write completed.
<|/tool_result|><|im_end|>
```

### Supervision and validation boundaries

For a future SFT integration, mask system/user content and tool observations; supervise assistant replies and assistant-generated tool calls. The SWE demonstration contains no reasoning traces. This is a proposed training policy: `render.py` emits strings, not token-aligned labels or loss masks. A real tokenizer integration must define boundary labels and check the actual tokens.

`tokenize_markers()` checks the declared marker-to-slot mapping with a Python scanner. It does not prove G3's trained tokenizer registers markers atomically. Before the final handoff, G3 must verify each structural surface encodes as one intended ID and ordinary Tamil round-trips correctly. Effort values are metadata; the renderer does not measure or enforce their token budgets.

Current v0 rejects literal control markers inside message content and normalizes away empty optional fields and an empty first system message. Exact round-trip claims apply to the supported canonical message shape illustrated above.

### Executed Tamil SWE task

See `results/tamil_swe_e2e.md` and `swe-task/run_tamil_e2e.py`: a local UTF-8 file-writing bug, an actual failing test, a patch, an actual passing test and a fully round-tripped Tamil tool trajectory. This authored smoke task establishes the local serialization and tool-observation path; it is not an external SWE-bench score or a model-training run.
