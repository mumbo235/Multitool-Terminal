# AI Assistant Architecture & Configuration Guide

Multitool Terminal features a high-performance, multi-provider AI assistant running directly from your browser. It supports live token streaming, persistent conversational chat sessions, reasoning token calibration, and resilient fallback routing.

---

## Table of Contents

- [Supported AI Providers](#supported-ai-providers)
- [Configuring API Keys](#configuring-api-keys)
- [Pro Tier Priority & Failover Architecture](#pro-tier-priority--failover-architecture)
- [Deprecated Model Policy (&le; 3.6)](#deprecated-model-policy--36)
- [Reasoning Latency Tuning (`ai thinking`)](#reasoning-latency-tuning-ai-thinking)
- [Natural Model Shorthands](#natural-model-shorthands)
- [Interactive Multi-Turn Chat (`ai chat`)](#interactive-multi-turn-chat-ai-chat)
- [Security & Direct Browser-to-API Calls](#security--direct-browser-to-api-calls)

---

## Supported AI Providers

Multitool Terminal connects directly to official AI endpoints via HTTP streaming:

| Provider | Supported Models | Recommended For |
| :--- | :--- | :--- |
| **Google Gemini** | `gemini-2.5-pro`, `gemini-3.8-flash`, `gemini-2.5-flash` | Complex coding, multimodal reasoning, high-throughput streaming. |
| **Anthropic Claude** | `claude-3-7-sonnet`, `claude-3-5-haiku`, `claude-3-opus` | Architectural analysis, nuanced text synthesis, code refactoring. |
| **OpenAI** | `gpt-4o`, `gpt-4o-mini`, `o3-mini`, `gpt-4-turbo` | General reasoning, function calling, logic evaluation. |
| **OpenRouter** | `deepseek/deepseek-r1`, `meta-llama/llama-3.3-70b`, `mistralai/mistral-large` | Open-source foundation models, community routing. |

---

## Configuring API Keys

API keys are configured using either the interactive TUI settings menu or direct CLI configuration:

### Method 1: TUI Configuration Menu
1. Type `settings` at the prompt.
2. Select `[1] AI Providers & API Keys`.
3. Choose your provider (e.g. `[1] Google Gemini`).
4. Paste your API key. Keys are securely masked in the display.
5. Select `[0]` to save and exit.

### Method 2: Command Line Shortcuts
```bash
# Set Google Gemini API key
settings set geminiKey AIzaSy...

# Set Anthropic Claude API key
settings set anthropicKey sk-ant-...

# Set OpenAI API key
settings set openaiKey sk-...
```

---

## Pro Tier Priority & Failover Architecture

For users with Google Gemini Pro subscriptions, Multitool Terminal enforces an intelligent Pro Priority routing engine:

### 1. Default Flagship: `gemini-2.5-pro`
When Google Gemini is selected, the terminal defaults to `gemini-2.5-pro`. This tier leverages maximum reasoning depth, context windows up to 2 million tokens, and multimodal analysis.

### 2. Resilient High-Demand & Quota Fallback
Under peak global usage, upstream API endpoints may return:
- `HTTP 429`: `RESOURCE_EXHAUSTED` (Rate limit / quota exhaustion)
- `HTTP 503`: `UNAVAILABLE` (Upstream capacity surges / server overload)

Rather than failing the request and leaving the user stuck, Multitool Terminal intercepts these specific error codes and automatically fails over to **`gemini-3.8-flash`** (and `gemini-2.5-flash`):
```
[WARN] Gemini 2.5 Pro busy (HTTP 503 / 429). Routed to priority fallback (gemini-3.8-flash).
[PRO] Response generated with Pro priority.
```
- **Configuration Integrity**: The fallback routing is dynamic and temporary. It does **not** demote your saved configuration; future prompts will continue attempting `gemini-2.5-pro` under Pro tier priority.
- **Toggling Pro Priority**: Pro Priority can be toggled via `ai priority on|off` or `settings set proPriority true|false`.

---

## Deprecated Model Policy (&le; 3.6)

Legacy and discontinued Gemini models (including `gemini-3.6-flash`, `gemini-3.5-flash`, `gemini-3.5-flash-lite`, `2.0-flash`, `1.5-pro`, `1.5-flash`, and `1.0`) are permanently deprecated and removed from the active model catalog.

If an incoming prompt or alias targets a legacy model name:
1. The terminal automatically intercepts the request.
2. The model target is dynamically upgraded:
   - Complex/Pro targets upgrade to `gemini-2.5-pro`.
   - Fast/Flash targets upgrade to `gemini-3.8-flash`.
3. An informative notification confirms the upgrade without failing the prompt.

---

## Reasoning Latency Tuning (`ai thinking`)

Gemini 2.5 Pro includes an internal thinking/reasoning chain. By default, extensive thinking token budgets can cause an initial 3 to 10 second delay before the first token streams into the terminal.

You can calibrate this reasoning token budget using the `ai thinking` command:

```bash
# Ultra-fast interactive streaming (512 token reasoning budget)
ai thinking fast

# Default balance of reasoning depth and latency (1024 tokens)
ai thinking balanced

# Deep architectural analysis (4096 tokens)
ai thinking deep

# Disable thinking tokens for instantaneous streaming (0 tokens)
ai thinking off
```

---

## Natural Model Shorthands

Execute one-off queries or switch global model defaults directly from the prompt:

### Direct Single-Line Queries
```bash
pro 2.5 "Write a robust retry wrapper in TypeScript"
flash 3.8 "Format this JSON payload"
opus 5.5 "Compare event-driven architecture vs CQRS"
gpt-4o "Explain SQLite WAL mode locking"
```

### Switching Default Target Models
```bash
ai model pro 2.5
ai model flash 3.8
ai model opus 5.5
ai model o3-mini

# Interactive arrow-key selection
ai model
```

---

## Interactive Multi-Turn Chat (`ai chat`)

To engage in continuous back-and-forth conversation with context preservation:

```
dev@localhost:~$ ai chat
Entering AI interactive chat mode (Model: gemini-2.5-pro).
Type 'exit' or 'quit' to return to terminal prompt.

ai> Let's design a microservices notification system.
ai: [Streaming response...]

ai> How should we handle failed SMS delivery retries?
ai: [Streaming response utilizing previous context...]

ai> exit
Exited interactive chat mode.
```

---

## Security & Direct Browser-to-API Calls

- **Direct Connections**: All network requests originate directly from your web browser (`fetch()` using HTTPS) to the official endpoints (`generativelanguage.googleapis.com`, `api.anthropic.com`, `api.openai.com`).
- **No Proxy Servers**: Multitool Terminal has zero middleman servers, telemetry, or proxies. Your API credentials and chat transcripts never leave your browser sandbox.
- **Local Storage Encryption**: Keys are saved in browser `localStorage` and never transmitted across the network except within the standard `Authorization` / `x-goog-api-key` header to the respective AI provider.
