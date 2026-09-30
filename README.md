# Awesome Free LLMs [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated directory of **LLMs you can use for free** — free API tiers and inference endpoints, free chat apps, and open-weight models you can run locally at zero marginal cost — as of **September 2026**.

"Free" means different things everywhere: per-day rate limits, one-time signup credits, rotating `:free` model pools, credit vouchers that only cover compute, and — the honest definition — open weights you download once and run forever. Every entry says what "free" *actually* means (limits, credits, expiry) and names the gotchas (data used for training, login walls, region limits).

**Verification confidence:** every entry is stamped ✅ **verified 2026-09-29** (free terms read on the vendor's official page) or ⚠️ **unverified** (third-party or ambiguous). **Numbers are never guessed** — if the official page is ambiguous, the entry says so. Machine-readable records live in [`data/free-llms.json`](data/free-llms.json) with a `free_verified` boolean per entry.

## 2026 Highlights

- **Free-tier retirements are the big story:** Cerebras ended its permanent no-card tier (now a card-gated Free Trial with dual-bucket limits, verified), SambaNova's free tier went away for new accounts (~Aug 2026), Together AI and DeepInfra quietly dropped their free trials, and Chutes ended its recurring free tier (March 2026).
- **The generous ones that remain:** Google AI Studio's free plan (Flash models, no card), Groq's recurring free plan, OpenRouter's rotating `:free` pool, Cloudflare Workers AI's 10,000 Neurons/day (verified), and Zhipu's three permanently-$0 GLM Flash models.
- **Open weights keep winning:** Qwen3.8, DeepSeek V4.1 Flash (MIT), GLM-5.3-Flash (MIT), gpt-oss, Gemma 4 (now Apache 2.0), and Xiaomi's MiMo-V2.6 (MIT) are all downloadable and free to run. **License watch:** MiniMax M3 and Kimi K3 moved to *custom* community licenses — not MIT/Apache, whatever third-party lists claim.
- **Chat apps got stricter in 2026:** ChatGPT free reportedly moved to unlimited GPT-5.6 Luna text (Aug 2026, third-party); Poe cut free points 3,000 → 300/day; Perplexity dropped 5 → 3 free Pro searches/day; GitHub Copilot converted premium requests to AI Credits and reportedly paused new free signups.

## Contents

- [Free API tiers & inference endpoints](#free-api-tiers--inference-endpoints)
- [Free chat apps](#free-chat-apps)
- [Open-weight models you can run locally](#open-weight-models-you-can-run-locally)
- [Retired / changed free tiers](#retired--changed-free-tiers)
- [Guides](#guides)
- [Related repositories](#related-repositories)
- [Contributing](#contributing)
- [License](#license)

---

## Free API tiers & inference endpoints

Free LLM API access — rate-limited free plans, starter credits, `:free` model pools, and credit vouchers. Watch the gotchas column; "free" is never the whole story.

- [Google AI Studio (Gemini Developer API)](https://ai.google.dev/) — ⚠️ unverified. Flash/Flash-Lite models free per model on the free plan, no card. Gotchas: free-tier I/O may train Google's products; exact RPM/TPM/RPD sit behind sign-in and vary by project/region; older 2.5 access restricted for new projects (~2026-09-18); Pro models left the general free tier earlier in 2026.
- [Groq](https://groq.com/) — ⚠️ unverified. Recurring free developer plan, per-model limits, no card. Third-party transcription of Groq's official table shows e.g. GPT-OSS 120B/20B at 30 RPM / 1,000 RPD / 8,000 TPM / 200,000 TPD per org — confirm on Groq's rate-limits doc before relying on it.
- [Cerebras](https://inference-docs.cerebras.ai/support/rate-limits) — ✅ verified. Free Trial tier: `gpt-oss-120b` and `qwen-3.8-27b` at **5 RPM / 30K uncached TPM / 90K total TPM / 1M TPH / 1M TPD each** (dual-bucket). The old permanent no-card tier is gone (lost ~2026-08-17); Sept 2026 reports describe a $5 trial credit after adding a verified payment method, expiring in 30 days — third-party, not restated on the fetched page.
- [OpenRouter (:free)](https://openrouter.ai/docs/api_reference/limits) — ⚠️ unverified. `:free` model IDs cost $0 per input/output token. Reported platform limits: 20 RPM / 50 RPD on unfunded accounts, 1,000 RPD after ≥$10 lifetime purchase; daily UTC reset, account-wide; some free models require prompt logging; negative balance can block even free models. Catalog rotates.
- [Fireworks AI](https://docs.fireworks.ai/faq-new/billing-pricing/) — ⚠️ unverified. No permanent free tier; reported $1 starter credit, no card; some sources say a default unpaid cap ~10 RPM; expiry unclear/conflicting.
- [Nebius Token Factory](https://docs.tokenfactory.nebius.com/) — ⚠️ unverified. Reported $1 trial credit, valid 30 days; a bank card is reportedly required to set up billing even to access the trial. (Renamed from Nebius AI Studio — old docs may be stale.)
- [Hugging Face Inference Providers](https://huggingface.co/docs/inference-providers) — ⚠️ unverified. Recurring monthly credits reported as $0.10/month for free users (auto-applied); PRO reportedly $2/month. Account/token required; upstream model availability rotates and may 404/410; $0.10 is only a few turns on heavy models.
- [Pollinations.ai](https://pollinations.ai/) — ⚠️ unverified. Split platform: legacy anonymous endpoint (`text.pollinations.ai/openai`, one reported model GPT-OSS 20B, no key) plus new `gen.pollinations.ai` needing an API key and spending Pollen credits. Registered accounts reportedly get free Pollen refilled hourly (amounts uncertain); legacy "1 request/15s" quotes are stale.
- [Puter.js](https://puter.com/) — ⚠️ unverified. **Not a provider-funded tier** — User-Pays model: the developer embeds Puter.js with no API key and pays $0; the end user authenticates to Puter (sign-in popup) and covers usage. No trustworthy official numeric quota — do not publish the third-party "~200 requests/day" claim.
- [Cloudflare Workers AI](https://developers.cloudflare.com/workers-ai/platform/pricing/) — ✅ verified. **10,000 Neurons/day at no charge** on both Workers Free and Paid plans ("Our free allocation allows anyone to use a total of 10,000 Neurons per day at no charge"); resets daily at 00:00 UTC; excess ops fail with an error. Gotchas: some frontier models require a Workers Paid plan ($5/mo minimum) even before the allowance is exhausted; account + account ID + API token required.
- [Cohere](https://cohere.com/) — ⚠️ unverified. Trial keys reportedly never expire, capped ~1,000 API calls/month (reported per-endpoint RPMs: Chat ~20, Rerank ~10, Tokenize ~100, Embed ~2,000 inputs/min). **Evaluation-only — prohibited for production/commercial use**; trial I/O may train models.
- [Mistral La Plateforme](https://mistral.ai/) — ⚠️ unverified. Free "Experiment" tier reportedly reaches all/most Mistral models, no card; frequently reported ~1B tokens/month, ~1 RPS, ~500K TPM — but some reports conflict with much lower practical RPM. One Sept 2026 source instead claims a "$10/month API credits" model — unresolved conflict; free-tier I/O may be used for training by default.
- [Zhipu / Z.ai GLM (API)](https://docs.z.ai/guides/overview/pricing) — ⚠️ unverified. `glm-4.5-flash` and `glm-4.7-flash` **permanently priced at $0**; `glm-4.6v-flash` may also be free. Third-party reported limit: 1 concurrent request per free model. Starter-grant claims (20M–25M tokens) unverified — omitted.
- [Alibaba Cloud Model Studio (Qwen)](https://www.alibabacloud.com/help/en/model-studio/new-free-quota) — ⚠️ unverified. **1,000,000 free tokens per eligible model**, valid 90 days — International (Singapore) region only. Eligible Sept 2026 models reportedly include Qwen 3.8 Max/Flash/27B, Qwen3 Max, Qwen3 Coder. Gotcha: automatic PAYG billing can kick in after quota unless "Free Quota Only" is enabled per model (reportedly off by default). Alibaba states submitted data is *not* used for training.
- [Novita AI](https://novita.ai/) — ⚠️ unverified. Two distinct things: (a) Sandbox — reported $100 sandbox credits valid 90 days, no card (sessions ≤1h, 5 concurrent, 2 vCPU/4GB RAM); (b) LLM API — only ~$0.50 signup credit reported. The $100 voucher is **compute credit, not LLM API inference credit**; a handful of $0/token open models reportedly stay free after it; sandbox terms reportedly prohibit commercial use without written permission.
- [Parasail](https://parasail.io/) — ⚠️ unverified. "Serverless - Free" tier for prototyping, reportedly 5 RPM (Qwen, DeepSeek, Llama series); third-party registry flags a linked payment method as required. Evidence is thin — verify on Parasail's pricing page.
- [Anthropic (starter credits)](https://platform.claude.com/) — ⚠️ unverified. Small one-time starter credit for new Console accounts — amount deliberately unpublished, no expiry stated; **no permanent API free tier**. Distinct from claude.ai free chat and from the Claude-for-Open-Source program (6 months of Max 20x for qualifying maintainers, launched Feb 2026).
- [DeepSeek (API grant)](https://platform.deepseek.com/) — ⚠️ unverified. Widespread third-party claim: 5M signup tokens, ~30-day expiry, no card — **but absent from DeepSeek's official pricing page**, so treat as unverified. Off-peak pricing is discounted, not free.
- [MiniMax (API trial)](https://www.minimax.io/) — ⚠️ unverified. No permanent free API tier; limited new-account trial credits (amount/expiry not reliable). Do NOT confuse with MiniMax Agent *consumer* credits (reportedly 1,000 signup + 200 daily-login credits).

---

## Free chat apps

No-cost chat surfaces and their message/model limits. Nearly all require a login; nearly all reserve the right to train on free-tier chats — see [privacy notes](docs/privacy-and-data-notes.md).

- [ChatGPT](https://chatgpt.com) — ⚠️ unverified. Free text chat. Aug 2026 third-party reports say free is now unlimited text on GPT-5.6 "Luna" with limited files/images/tools and a Think button for reasoning; an official help article (GPT-5.5 era) previously stated up to 10 GPT-5.5 messages per 5 hours, then auto-switch to the mini version. Login required; consumer chats train models by default (opt-out available); older free models retire on a schedule (GPT-5 retired Feb 13, 2026).
- [Claude](https://claude.ai) — ⚠️ unverified. Free access to the current Sonnet-class model (Sonnet 5 per Sept 2026 reviews), web search, file uploads, Projects, Artifacts, limited agent/coding features. Limits are compute-based on a **rolling 5-hour window** — no fixed published message count (third-party 15–40/window estimates are not official). Login required; free chats reportedly trainable with opt-out; Claude Code not included.
- [Gemini app](https://gemini.google.com) — ⚠️ unverified. Free: standard model reportedly Gemini 3.6 Flash (Sept 2026 reviews), some Pro-model access, image generation, Deep Research (~5 reports/month per one review). Limits compute-based on a 5-hour cycle; no published message count. Google account required; Apps activity may train models unless paused.
- [Grok](https://grok.com) — ⚠️ unverified. Free tier on grok.com/X with the lighter model; ~10 prompts per rolling 2 hours reported; no card. Login required (reports say X account 7+ days old with verified phone); image/video creation gated to SuperGrok; exact free model not reliably established.
- [Microsoft Copilot](https://copilot.microsoft.com) — ⚠️ unverified. Free core text chat; quick chat works **without sign-in**; sign-in unlocks history, longer conversations, image creation, voice. No published numeric text cap (capacity throttling). Copilot Pro retired late 2025; data used for ads/personalization (opt-out exists).
- [Meta AI](https://www.meta.ai) — ⚠️ unverified. Free in WhatsApp, Instagram, Facebook, Messenger and meta.ai; no published message cap (platform rate limits only); Llama-based. Image generation reportedly limited (~25/day per one review); "Meta One" paid add-ons now exist. AI chats processed by Meta and may train models / personalize ads; person-to-person WhatsApp chats remain E2EE.
- [DeepSeek chat](https://chat.deepseek.com) — ⚠️ unverified. Web + app chat fully free, no ads, no in-app purchases (per official-doc mirror); DeepThink reasoning toggle, web search, file uploads; reviews report unlimited queries. Login via email/Google/Apple. Hosted in China — busy-period slowdowns, privacy scrutiny, regional restrictions.
- [Qwen Chat](https://chat.qwen.ai) — ⚠️ unverified. Consumer Qwen Chat free with Qwen3-series models (Qwen3.7-Max reportedly free for all since 2026-05-22); no published request cap. Account via email/phone. Note: Qwen's free *developer* OAuth/coding API route ended 2026-04-15 — consumer chat unaffected.
- [Kimi](https://www.kimi.com) — ⚠️ unverified. Free web/mobile chat with Kimi K2.6/K3 chat and agent modes; free limits unpublished; heavy agent/Deep Research features reportedly paid (~$19/mo Moderato).
- [Le Chat by Mistral](https://chat.mistral.ai) — ⚠️ unverified. Free tier with default Mistral Medium 3.5 (relaunched as "Mistral Vibe" May 2026 per one review), limited messages, web searches, image generation, connectors, voice. Numeric message limit NOT published — third-party guesses (~25/day vs ~200/day) are unreliable; do not cite. Free chats may train models unless opted out.
- [Perplexity](https://www.perplexity.ai) — ⚠️ unverified. Practically unlimited basic/Best searches, **3 Pro Searches/day**, 1 Research query/month, limited file uploads (Sept 2026 plan-guide reviews); automatic model selection — no manual frontier-model picker. Older "5 Pro searches/day" pages are stale.
- [ChatGLM (Z.ai)](https://chat.z.ai) — ⚠️ unverified. Consumer chat free with GLM-5.x-era model access; one third-party guide claims ~50 requests/day (unverified). Account via phone/email. Do not conflate chat quotas with the free API Flash models.
- [Doubao](https://www.doubao.com) — ⚠️ unverified. ByteDance's consumer app: daily chat, copywriting, information lookup remain free; paid Professional tiers launched 2026-06-24 (¥68/200/500 per month). China-focused; Chinese phone-number signup typical.
- [ERNIE Bot (Wenxin Yiyan)](https://yiyan.baidu.com) — ⚠️ unverified. **Fully free since April 1, 2025**, including latest ERNIE models, long-document processing, deep search, AI art, multilingual chat — no paid tier for chat, no explicit cap found. Baidu account + real-name verification; mainland-China availability.
- [GitHub Copilot Free (VS Code)](https://github.com/features/copilot) — ⚠️ unverified. Legacy allowance widely cited: 2,000 code completions + 50 chat/agent requests/month — but premium requests converted to AI Credits on 2026-06-01 and new free signups were reportedly paused ~2026-04-20. Current free availability needs official confirmation.
- [GitHub Spark](https://github.com/features/spark) — ⚠️ unverified. App-building copilot; no stable standalone free tier confirmed. One Sept 2026 report: free pool of ~50 premium requests/month (~4 requests per Spark message). GitHub account required.
- [HuggingChat](https://huggingface.co/chat) — ⚠️ unverified. Free chat over ~120+ models; reviews claim no daily cap, but a mid-2026 technical doc says free accounts get only **$0.10/month inference credit** (~8–10 turns on expensive models) and heavy models drain it fast. HF login required; model availability and queueing are dynamic.
- [Poe](https://poe.com) — ⚠️ unverified. Bot-aggregator free tier: **300 compute points/day since ~2026-03-30** (down from 3,000/day), no rollover; each bot/message costs a different number of points — not a fixed message count.
- [You.com](https://you.com) — ⚠️ unverified. Free core chat/search with usage limits — but current 2026 free model/quota could not be reliably verified (old docs say unlimited basic chat; a 2025 aggregate says 25-query trial). Stale/conflicting data.
- [Duck.ai](https://duck.ai) — ⚠️ unverified. Free, **no account**: multiple models (reported: Claude 4.5 Haiku, Llama 4 Scout, Mistral Small 3 24B, GPT-4o mini, GPT-5 mini, gpt-oss-120b); daily cap not published. Privacy-strong: prompts anonymized, not used for training, history stored locally.
- [Venice.ai](https://venice.ai) — ✅ verified (official blog). Privacy-first free tier, **no login**: **10 text prompts/day + 15 image prompts/day**, base models; Pro $18/mo = unlimited text, 1,000 images/day. No video/API on free; no training on inputs; chats stored in-browser by default.
- [LMArena](https://lmarena.ai) — ⚠️ unverified. **100% free**, no sign-up: anonymous side-by-side model battles, direct chat with featured models, voting, leaderboards; file uploads up to ~10MB per one guide. Research project — prompts are logged and may enter published datasets; don't share sensitive data.

---

## Open-weight models you can run locally

Download once, run forever: open weights mean zero marginal cost (your hardware is the bill). Runners are listed at the end.

- [Llama (Meta)](https://www.llama.com/models/llama-4/) — ⚠️ unverified. Llama 4 Scout (17B active / 109B MoE, 10M ctx) and Maverick (17B active / ~400B MoE, 1M ctx). Custom Llama Community License (verify before redistribution). Scout fits single H100 (Int4); Maverick needs multi-GPU.
- [Qwen (Alibaba)](https://huggingface.co/Qwen) — ✅ verified (Apache 2.0 quoted on HF cards). Qwen3.5/3.6/3.8 from 0.8B to a 2.4T-A95B Max-class MoE. 27B runs on one GPU (~17GB quantized). No open Qwen3.7; Qwen 4 27B open announced for later.
- [DeepSeek](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro) — ✅ verified (MIT quoted on card). V4-Pro (1.6T/49B MoE), V4-Flash, V4.1 Flash (552B/8–16B MoE, 1M ctx, multimodal, Sep 2026). Flash GGUF ≈ 146GB — multi-GPU, not laptop.
- [Kimi (Moonshot AI)](https://huggingface.co/moonshotai/Kimi-K3) — ✅ verified. K2.x (1T/32B MoE) on **Modified MIT** (attribution at 100M MAU/$20M revenue); **K3 (2.8T, 1M ctx, native vision) moved to a custom Kimi K3 License**. K3 weights are 1.56TB (cluster-only); K2.6 quantized runs on high-end Macs (MLX).
- [GLM (Zhipu / Z.ai)](https://huggingface.co/zai-org) — ✅ verified (MIT quoted on card). GLM-5.x line (744B-class MoE, up to 1M ctx) and GLM-5.3-Flash (320B/18B, natively multimodal); GLM-4.7-Flash (30B-A3B) is the smallest. 5.3-Flash EXL3 runs on one 128GB machine (third-party).
- [Gemma (Google)](https://blog.google/innovation-and-ai/technology/developers-tools/gemma-4/) — ✅ verified. Gemma 4 (Apr 2026): E2B (~2.3B) / E4B (~4.5B), 26B-A4B MoE, 31B dense — **first Gemma gen on Apache 2.0** (drops the old restrictive Gemma Terms). E2B runs on Raspberry Pi/phones; E4B on laptops (6.1GB QAT Ollama build).
- [Mistral (open models)](https://huggingface.co/mistralai/Mistral-Small-4-119B-2603) — ✅ verified. Small 4 (119B-A6B MoE), Large 3 (675B), Ministral 3 (3B/8B/14B) on Apache 2.0; Medium 3.5 and Devstral 2 on Modified MIT (revenue cap, third-party). Ministral 3B = mobile/browser; Small 4 Q4 ≈ 68GB (64–128GB Macs).
- [Phi (Microsoft)](https://huggingface.co/microsoft/phi-1) — ✅ verified. MIT: Phi-4 (14B), Phi-4-mini (3.8B, ~2.5GB in Ollama), Phi-4-multimodal (5.6B), Phi-4-reasoning-vision-15B. **No Phi-5 exists** (unreleased as of Sept 2026).
- [gpt-oss (OpenAI)](https://huggingface.co/openai/gpt-oss-120b) — ✅ verified. gpt-oss-120b (117B/5.1B MoE, MXFP4) and gpt-oss-20b (21B/3.6B), 128K ctx, text-only reasoning with adjustable effort. Apache 2.0 + usage policy. 20B fits a 16GB consumer GPU; 120B fits one 80GB H100. `ollama run gpt-oss:20b`.
- [OLMo (Ai2)](https://huggingface.co/allenai/Olmo-3.1-32B-Instruct) — ✅ verified. The "fully open" family: weights + training data (Dolma) + code + 500+ checkpoints, Apache 2.0. 32B = single high-end GPU class. Best choice for auditable, reproducible provenance.
- [Falcon (TII)](https://huggingface.co/tiiuae/Falcon-H1-7B-Base) — ✅ verified (HF org). Falcon-H1 hybrid Mamba2+attention (0.5B–34B, Base+Instruct, 16K–256K ctx), GGUF variants; no vendor-hosted API. Custom Falcon LLM License (verify before commercial use); 0.5B–7B are laptop-friendly.
- [MiMo (Xiaomi)](https://huggingface.co/XiaomiMiMo/MiMo-V2.6-Pro-RL) — ✅ verified. Omnimodal: MiMo-V2.6-Pro-RL (1.02T/42B MoE, 1M ctx, text/image/audio/video) and Flash-RL (309B/15B), **MIT** (no revenue cap). Pro = multi-node; Flash EXL3 2.27bpw runs on one 128GB DGX Spark (third-party). Newest family here (Sept 21–22, 2026).
- [MiniMax (open weights)](https://huggingface.co/MiniMaxAI/MiniMax-M3) — ✅ verified. M3 (~428B/23B MoE, 1M ctx, native multimodal). **LICENSE WARNING: MiniMax Community License (custom — NOT MIT/Apache, widely mislabeled)**; requires "Built with MiniMax M3" attribution + notice/authorization for commercial use. Cluster/multi-node scale.
- [StepFun](https://huggingface.co/stepfun-ai/Step-3.7-Flash) — ✅ verified. Step-3.7-Flash (198B, ~11B active, 256K ctx, multimodal, BF16/FP8/NVFP4/GGUF), Apache 2.0. Runs on a single 128GB unified-memory machine (third-party). Step 5 Preview (600B/27B, Sep 2026) is API-only — weights unconfirmed.
- [NVIDIA Nemotron 3](https://huggingface.co/nvidia/NVIDIA-Nemotron-Nano-9B-v2) — ✅ verified (HF org). Ultra (550B/55B MoE, 1M ctx), Super (120B/12B), Nano 4B/9B (hybrid Mamba) under a custom NVIDIA Open Model License. Nano 4B runs on laptops via Ollama.
- [IBM Granite 4.x](https://huggingface.co/ibm-granite/granite-4.0-350m) — ⚠️ unverified. Enterprise/agent-focused: 1B–32B dense + MoE, Apache 2.0 (third-party — verify the card before commercial use).
- [Liquid AI LFM2.5](https://huggingface.co/LiquidAI) — ✅ verified (HF org). Tiny hybrids (230M/350M/1.2B) with official 4-bit MLX artifacts — edge-first, phones/edge devices.
- [OpenBMB MiniCPM5](https://huggingface.co/openbmb) — ⚠️ unverified. MiniCPM5 1B (May 2026) / 2B (Sep 7 2026), Apache 2.0 (third-party), MLX 4-bit builds — laptop/edge class.
- [inclusionAI (Ant) Ling](https://huggingface.co/inclusionAI) — ⚠️ unverified. Ling-2.6-flash (104B-A7.4B) and Ling-3.0-flash (124B-A5B hybrid KDA+MLA, true 256K), MIT (third-party). 100B+ class — multi-GPU.
- [ByteDance Seed-OSS-36B](https://huggingface.co/ByteDance-Seed/Seed-OSS-36B-Instruct) — ✅ verified. Dense 36B (Aug 2025) with 512K native context, Apache 2.0 (third-party) — single high-end GPU class.

### Runners — how to actually run them

- [Ollama](https://ollama.com/library) — ✅ verified. `ollama run <model>` — pulls, quantizes, and serves behind a local OpenAI-compatible API (MIT). Tags in the wild: `gpt-oss:20b`, `qwen3.5:2b`, `gemma4:e2b-it-qat`, `phi4-mini:3.8b`, `nemotron-3-nano:4b`, `kimi-k2.5`.
- [llama.cpp / GGUF](https://github.com/ggml-org/llama.cpp) — ✅ verified. Bare-metal C++ inference engine + the GGUF quantization standard; built-in `llama-server` (MIT). Best cost-performance on non-NVIDIA hardware (laptops, Apple Silicon, edge); MLX is the Apple-Silicon sibling.
- [LM Studio](https://lmstudio.ai) — ⚠️ unverified. Desktop GUI for discovering, downloading (GGUF/MLX), and chatting with local models — no CLI needed.
- [vLLM](https://github.com/vllm-project/vllm) — ✅ verified. High-throughput serving engine (PagedAttention) with an OpenAI-compatible API — the standard multi-GPU choice for large MoE (Apache 2.0). SGLang is its closest alternative.

---

## Retired / changed free tiers

Free tiers that ended or changed materially, newest first.

- **Cerebras** (Sept 2026) — permanent no-card 1M tokens/day tier → card-gated Free Trial (dual-bucket limits, verified).
- **SambaNova** (~Aug 2026, delisted by trackers 2026-09-23) — free tier gone for new accounts; "Add a payment method and purchase credits to run your first requests". Stale docs still describe the old free tier.
- **Together AI / DeepInfra** (June–Sept 2026) — old signup-credit claims ($1/$5/$25) appear obsolete; minimum credit purchase required.
- **ChatGPT free** (Aug 2026, third-party) — official help page still shows 10 GPT-5.5 messages/5h; reported current behavior is unlimited text on GPT-5.6 "Luna".
- **xAI data-sharing credits** (2026, conflicting) — $25 signup + up to $150/mo after $5 spend with irreversible data-sharing opt-in vs. "program ended, no free tier remains". Verify on xAI's billing page.
- **GitHub Copilot free** (Apr–Jun 2026) — premium requests converted to AI Credits (2026-06-01); new free signups reportedly paused ~2026-04-20.
- **Mistral Experiment tier** (Sept 2026, conflicting) — long-reported ~1B token/month Experiment tier vs. a Sept 2026 source claiming a "$10/month API credits" model. Unresolved; check the official page.
- **Perplexity** (2026) — free dropped 5 → 3 Pro searches/day.
- **Poe** (~Mar 2026) — free points cut 3,000 → 300/day.
- **Chutes** (Mar 2026) — recurring free tier ended.
- **Qwen developer OAuth/coding API** (2026-04-15) — free developer route ended (consumer chat unaffected).
- **OpenAI signup credits** (~mid-2025) — $5/3-month program discontinued; no automatic signup credits since.
- **Google AI Studio** (~2026-09-18) — older 2.5-model access restricted for new projects; Pro models left the general free tier earlier in 2026.
- **Copilot Pro** (late 2025) — retired, replaced by Microsoft 365 Premium / Copilot Plan.
- **ERNIE Bot** (2025-04-01) — went fully free *in the opposite direction*: no paid tier for chat.

---

## Guides

- [Choosing a free LLM](docs/choosing-a-free-llm.md) — which free tier fits coding, agents, chat, bulk processing, or privacy-first use.
- [Limits & gotchas](docs/limits-and-gotchas.md) — how to read rate limits, credit expiry, and the fine print without surprises.
- [Privacy & data notes](docs/privacy-and-data-notes.md) — which free tiers train on your data, and how to opt out.
- [Machine-readable catalog](data/free-llms.json) — every entry with free-tier verification status.

## Related repositories

- [awesome-flagship-llms](https://github.com/dakotac1994/awesome-flagship-llms) — sibling list: flagship frontier LLMs, pricing, and benchmarks.
- [awesome-flash-llms](https://github.com/dakotac1994/awesome-flash-llms) — sibling list: cost-performance Flash-class LLMs and their $/1M-token pricing.
- [awesome-fast-llms](https://github.com/dakotac1994/awesome-fast-llms) — sibling list: inference-speed LLMs, providers, engines, and optimization techniques.
- [awesome-decisions-llms](https://github.com/dakotac1994/awesome-decisions-llms) — sibling list: LLMs and systems for decision-making — decision-tuned models, decision benchmarks & evals, frameworks, and key research papers.

## Contributing

Entries and corrections are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). Every PR is checked by CI: lychee link check over all markdown files, and validation of `data/free-llms.json` (including the `free_verified` boolean and required `source_url` for verified entries).

## License

[MIT](LICENSE) © 2026 dakotac1994
