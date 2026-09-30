# Privacy & data notes

What happens to your prompts on free tiers — and how to keep sensitive data out of training sets.

## The short version

On most free chat tiers, **your conversations may be used to train models** unless you opt out. The only free chat apps in this list documented as *not* training on inputs are **Duck.ai** and **Venice.ai**. Running **open weights locally** (Ollama, llama.cpp) is the only option where no third party sees your data at all.

## Per-service notes (as of Sept 2026)

| Service | Trains on free-tier data? | Opt-out / notes |
|---|---|---|
| ChatGPT | Yes, by default | Opt-out available in settings |
| Claude (claude.ai) | Reportedly yes, with opt-out | Claude Code not included on Free anyway |
| Gemini app | Gemini Apps activity may be used | Pause Apps activity to stop it |
| Grok | Data-sharing programs reported; terms shifted in 2026 | Check current xAI terms — old data-sharing opt-in was described as irreversible |
| Microsoft Copilot | Data used for ads/personalization | Opt-out exists |
| Meta AI | AI chats processed by Meta; may train models / personalize ads | Normal person-to-person WhatsApp chats remain E2EE |
| DeepSeek chat | Hosted in China; standard collection terms | Assume service-side logging |
| Qwen Chat | Data hosted by Alibaba | — |
| Kimi | Standard collection terms | Free limits unpublished |
| Le Chat (Mistral) | May be used for training unless opted out | Check settings |
| Perplexity | Ad-supported-ish research flow with citations | — |
| ChatGLM / Doubao / ERNIE Bot | Standard collection terms; real-name verification (China) | Assume service-side logging |
| HuggingChat | Some sources say conversations may be used for training | — |
| Poe | Account-linked; point-based | — |
| **Duck.ai** | **No — prompts anonymized, not used for training** | History stored locally (optional encrypted sync) |
| **Venice.ai** | **No training on inputs** | Chats stored in-browser by default |
| LMArena | Prompts are **logged and may enter published datasets** | Research project — do not share sensitive data |

## API free tiers

- **Google AI Studio:** free-tier inputs/outputs may be used to improve Google's products.
- **Cohere:** trial inputs/outputs may be used to improve models.
- **Mistral La Plateforme:** free-tier I/O may be used for training by default (opt-out may exist).
- **Alibaba Cloud Model Studio:** states submitted data is *not* used for model training.
- **OpenRouter :free:** some free models require prompt logging / data-policy relaxation — read the model's data policy before sending anything sensitive.
- **Puter.js:** user-pays — the end user's own Puter account terms apply, not yours.

## Practical rules

1. **Never paste secrets, credentials, customer data, or unfiled IP into a free chat tier** unless you've confirmed the no-training policy (Duck.ai, Venice.ai) or are running locally.
2. **Opt out where offered** — ChatGPT, Claude, Gemini, Le Chat all have settings for this; do it once at signup.
3. **LMArena is a research instrument**, not a private assistant: everything you type may be published.
4. **For code with proprietary logic**, prefer a local model ([gpt-oss](https://huggingface.co/openai/gpt-oss-120b), [Qwen](https://huggingface.co/Qwen), [DeepSeek](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro)) or a paid tier with a zero-retention/data-processing agreement.
5. **Read the current terms yourself** — data policies change (xAI's 2026 shifts are the cautionary tale), and this page is a pointer, not legal advice.
