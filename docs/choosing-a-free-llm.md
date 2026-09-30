# Choosing a free LLM

Which free option fits your job? Free tiers differ wildly in limits, login requirements, and what you give up in exchange. This guide maps common use cases to the entries in the main list.

## Quick picks (as of Sept 2026)

| Job | Best free option | Why |
|---|---|---|
| General chat, no account | [Duck.ai](https://duck.ai) or [Venice.ai](https://venice.ai) | No login, private by default; Venice = 10 text + 15 images/day (verified) |
| General chat, one login | [ChatGPT](https://chatgpt.com) or [Claude](https://claude.ai) | Most capable free chats; rolling 5-hour compute windows |
| Privacy-first chat | [Duck.ai](https://duck.ai), [Venice.ai](https://venice.ai) | Prompts anonymized, not used for training (see [privacy notes](privacy-and-data-notes.md)) |
| Research with citations | [Perplexity](https://www.perplexity.ai) (3 Pro searches/day) or [LMArena](https://lmarena.ai) (free, no caps) | Built for answers-with-sources; LMArena compares models side by side |
| Coding in an editor | [GitHub Copilot Free](https://github.com/features/copilot) (terms in flux, 2026) or free API tiers feeding an editor agent | Check Copilot's current free status before relying on it |
| API for side projects | [Google AI Studio](https://ai.google.dev/) (Flash models, no card), [Groq](https://groq.com/) (recurring free plan), [OpenRouter :free](https://openrouter.ai/) (rotating $0 models) | Real keys, real code, no card |
| API for batch/offline work | [Cloudflare Workers AI](https://developers.cloudflare.com/workers-ai/platform/pricing/) (10K Neurons/day, verified) or [Zhipu GLM Flash](https://docs.z.ai/guides/overview/pricing) ($0 models) | Predictable daily allowances |
| Agents / tool calling | [Mistral Experiment tier](https://mistral.ai/) (if the 1B-token reports hold) or [OpenRouter :free](https://openrouter.ai/) | Watch for prompt-logging requirements on some free models |
| Fully offline, no data leaves the machine | [Ollama](https://ollama.com/library) + `gpt-oss:20b` / `qwen3.5:2b` / `gemma4:e2b-it-qat` | Zero marginal cost; your hardware is the limit |
| Best local quality on one GPU | [gpt-oss-120b](https://huggingface.co/openai/gpt-oss-120b) (one 80GB H100) or [DeepSeek V4-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro) GGUF (multi-GPU) | Check licenses before redistribution |
| On-device / mobile | [Gemma 4 E2B](https://blog.google/innovation-and-ai/technology/developers-tools/gemma-4/) or [Liquid AI LFM2.5](https://huggingface.co/LiquidAI) | Raspberry Pi / phone class |

## Decision flow

1. **Does any data leave your machine matter?** If yes → run open weights locally ([Ollama](https://ollama.com/library), [llama.cpp](https://github.com/ggml-org/llama.cpp)) or use [Duck.ai](https://duck.ai)/[Venice.ai](https://venice.ai). If no → continue.
2. **Do you need an API key (code) or a chat UI?** API → free tiers section; chat → chat apps section.
3. **How much will you use?** Light/occasional → any free tier. Daily production use → check the actual limits (see [limits & gotchas](limits-and-gotchas.md)); "free" plans that retried this year (Cerebras, SambaNova, Together) remind you to have a fallback provider.
4. **Card or no card?** [Google AI Studio](https://ai.google.dev/), [Groq](https://groq.com/), [Duck.ai](https://duck.ai), [Venice.ai](https://venice.ai), [LMArena](https://lmarena.ai) need no card. Cerebras now requires a verified payment method for its trial.
5. **License check (local models):** most families are Apache 2.0 / MIT — but **MiniMax M3 and Kimi K3 use custom licenses**, and Llama/Falcon/Nemotron carry custom terms. Read the license before shipping a product.

## Traps to avoid

- **Credit vouchers ≠ API credit.** Novita's $100 sandbox voucher covers sandbox compute, not LLM tokens.
- **Free chat ≠ free API.** Claude's free chat gives no API access; ChatGLM's chat quota is separate from Zhipu's $0 API models.
- **"Free" chat often means "you're the training data."** See [privacy & data notes](privacy-and-data-notes.md) before pasting anything sensitive.
- **Limits move.** Several big free tiers tightened or ended in 2026 — build against 2 providers (e.g. OpenRouter `:free` as a fallback) rather than hardcoding one.
