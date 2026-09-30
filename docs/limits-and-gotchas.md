# Limits & gotchas

How to read a free tier's fine print — and why the headline ("free!") is never the whole story.

## The five axes of "free"

1. **Rate limits** — requests/minute, tokens/minute, requests/day. Groq's free plan is per-model (e.g. 30 RPM / 1,000 RPD on some models, third-party); Cerebras' trial is dual-bucket (5 RPM *and* 1M tokens/hour, verified). A plan can look generous in RPM and still cap you in TPM.
2. **Credits with expiry** — one-time grants that burn down: Nebius' reported $1/30 days, Anthropic's unpublished starter credit, Novita's $100 sandbox voucher (90 days, compute-only). Expired credits usually mean the API just stops — check whether billing auto-kicks in.
3. **Rotating pools** — OpenRouter's `:free` models change. A model that's $0 today may leave the pool tomorrow; never hardcode a single `:free` model ID in production.
4. **Per-model restrictions** — free tiers often cover only efficiency models (Gemini Flash, not Pro; lighter Grok, not SuperGrok). Frontier models on Cloudflare Workers AI can require a Paid plan even before you exhaust the 10K Neurons/day allowance.
5. **Account/card walls** — no-card tiers (Google AI Studio, Groq, Duck.ai, Venice.ai, LMArena) vs. card-gated trials (Cerebras' new trial). Your broken-phone/VPN situations also matter: some providers gate signups on verified phones or flag unusual connections.

## Expiry and auto-billing traps

- **Alibaba Cloud Model Studio:** automatic PAYG billing can kick in after the 1M-token free quota unless "Free Quota Only" is enabled per model (reportedly off by default).
- **Cerebras:** the old no-card tier silently became a card-gated trial (~Aug 2026) — if you had an old account, your free access may simply be gone.
- **Cohere trial keys:** evaluation-only. "Never expires" does not mean "production-legal" — commercial use is prohibited.

## Data-as-payment

The most common hidden price of free chat: your conversations train models. ChatGPT, Claude, Gemini app, Grok, Meta AI, Le Chat, and HuggingChat all have training-by-default (with opt-outs) or data-sharing programs. [Duck.ai](https://duck.ai) and [Venice.ai](https://venice.ai) are the exceptions — no training on inputs. Full breakdown in [privacy & data notes](privacy-and-data-notes.md).

## Regional and identity gotchas

- **Phone verification:** Grok's free tier reportedly requires an X account 7+ days old with a verified phone; Doubao and ERNIE Bot typically need Chinese phone numbers / real-name verification.
- **Region locks:** ChatGPT and others restrict some countries; Alibaba's Qwen free quota is International (Singapore) region only; DeepSeek chat faces government restrictions in some countries.
- **Waitlists:** free API tiers (Mistral Experiment, xAI's old data-sharing program) have had waitlist or approval mechanics — expect a delay between signup and access.

## How to verify before you build

1. Read the provider's **pricing/limits page yourself** — this list stamps entries ✅ verified only when the free terms were read on an official page; ⚠️ unverified means third-party.
2. Check the **billing dashboard** after signup for the actual quota and expiry — grants often differ from marketing pages.
3. Watch the [**retired / changed**](../README.md#retired--changed-free-tiers) section: 2026 saw Cerebras, SambaNova, Together, DeepInfra, Chutes, Poe, and Perplexity all tighten or end free offers.
4. For local models, read the **license file on the model card** — MiniMax M3 and Kimi K3 are custom-licensed despite what aggregator lists claim.
