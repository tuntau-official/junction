# AI assistant

The assistant turns plain-language questions into SQL against *your* schema. It doesn't guess table names: it has tools to look up your real tables, columns and relations, and it can run a read query to check its answer before showing it to you.

Good for:

- "Show me the top 10 customers by total spend this year."
- "Why does this query return duplicates?"
- "Explain this SQL." (paste or select it)
- "Add a filter for orders over €100" — it edits the canvas and you watch the nodes appear.

The assistant is a **Pro** feature, and you **bring your own model** — Junction doesn't resell AI or route your prompts through Tuntau.

## Configure a model

**Settings → AI**, then fill in three fields:

| Field | Example |
|---|---|
| Endpoint URL | Any OpenAI-compatible chat-completions API |
| API key | Your provider's key (leave empty for most local servers) |
| Model | The model name your endpoint expects |

Presets are included for the common setups; **Test** checks the endpoint before you save.

| Provider | Endpoint |
|---|---|
| OpenAI | `https://api.openai.com/v1` |
| Ollama (local) | `http://localhost:11434/v1` |
| LM Studio (local) | `http://localhost:1234/v1` |
| Azure OpenAI, LiteLLM, OpenRouter, vLLM… | Your deployment's OpenAI-compatible URL |

Tool-calling quality matters more than raw size: pick a model that handles function calling well.

## What it can and can't do

| | |
|---|---|
| ✅ Inspect schema, columns, relations | Freely |
| ✅ Run **read** queries | Freely, to verify its answers |
| ⚠️ Run **writes** (`INSERT`, `UPDATE`, `DELETE`, DDL) | Only after you approve **each one**, and never on a read-only connection |
| ✅ Read your linked codebase | To understand relations — **never writes** to it |
| ✅ Edit the open blueprint | You see every change on the canvas |

## What leaves your machine

Only what goes to the endpoint *you* configured:

- your messages and the conversation so far;
- schema **names and shapes** (tables, columns, types, relations) the assistant looks up;
- result rows **only** from queries it runs to verify an answer.

Point it at a local model (Ollama, LM Studio) and nothing leaves your machine at all.
