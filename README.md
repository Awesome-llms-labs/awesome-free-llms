# Awesome Free LLMs [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated directory of **LLMs you can use for free** — free API tiers and inference endpoints, free chat apps, and open-weight models you can run locally at zero marginal cost — as of **September 2026**.

"Free" means different things everywhere: per-day rate limits, one-time signup credits, rotating `:free` model pools, credit vouchers that only cover compute, and — the honest definition — open weights you download once and run forever. Every entry says what "free" *actually* means (limits, credits, expiry) and names the gotchas (data used for training, login walls, region limits).

**Verification confidence:** every entry is stamped ✅ **verified** (free terms read on the vendor's official page) or ⚠️ **unverified** (third-party or ambiguous). **Numbers are never guessed** — if the official page is ambiguous, the entry says so. Machine-readable records live in [`data/free-llms.json`](data/free-llms.json) with a `free_verified` boolean per entry. **54 of 71 entries verified** (22 on 2026-09-29, 32 on 2026-09-30).

## 2026 Highlights

- **Free-tier retirements are the big story:** Cerebras ended its permanent no-card tier (now a card-gated Free Trial with dual-bucket limits, verified), SambaNova's free tier went away for new accounts (~Aug 2026), Together AI and DeepInfra quietly dropped their free trials, and Chutes ended its recurring free tier (March 2026). **All four retirements now verified on the official pages (2026-09-30).**
- **The generous ones that remain:** Google AI Studio's free plan (Flash models, no card), Groq's recurring free plan, OpenRouter's rotating `:free` pool, Cloudflare Workers AI's 10,000 Neurons/day (verified), and Zhipu's three permanently-$0 GLM Flash models.
- **Open weights keep winning:** Qwen3.8, DeepSeek V4.1 Flash (MIT), GLM-5.3-Flash (MIT), gpt-oss, Gemma 4 (now Apache 2.0), and Xiaomi's MiMo-V2.6 (MIT) are all downloadable and free to run. **License watch:** MiniMax M3 and Kimi K3 moved to *custom* community licenses — not MIT/Apache, whatever third-party lists claim.
- **Chat apps, now verified where possible:** ChatGPT free terms verified via the official FAQ (GPT-5.2, usage within a five-hour window — the third-party 'unlimited GPT-5.6 Luna' reports were unsupported); Perplexity's 3 Pro Searches/day verified; Poe cut free points 3,000 → 300/day (third-party); GitHub Copilot Free moved premium requests to AI Credits (2026-06-01, verified); **GitHub Spark was retired entirely (Aug 31, 2026, verified).**

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

- [Google AI Studio (Gemini Developer API)](https://ai.google.dev/) — ✅ verified. Free plan with free input/output tokens for Flash-family models (exact free models vary). Model-dependent; public page did not state RPM/TPM/RPD numbers — account/project Limits page is authoritative. Gotchas: Free-tier inputs/outputs may be used to improve Google's products; Rate limits vary by project and region; exact numbers behind sign-in; Older 2.5-model access restricted for new projects (~2026-09-18); Pro models moved out of the general free tier earlier in 2026.
- [Groq](https://groq.com/) — ✅ verified. Recurring free developer plan with per-model organization limits. Official table e.g. openai/gpt-oss-120b, openai/gpt-oss-20b, openai/gpt-oss-safeguard-20b, qwen/qwen3.8-27b: 30 RPM / 1,000 RPD / 8,000 TPM / 200,000 TPD; Whisper models: 20 RPM / 2,000 RPD / 7,200 ASH / 28,800 ASD — actual organization limits may differ; signed-in Limits page authoritative. Gotchas: Limits differ per model (classifiers/audio differ); 'No card required' not explicitly stated on opened official pages — not confirmed.
- [Cerebras](https://inference-docs.cerebras.ai/support/rate-limits) — ✅ verified. Free Trial tier: `gpt-oss-120b` and `qwen-3.8-27b` at **5 RPM / 30K uncached TPM / 90K total TPM / 1M TPH / 1M TPD each** (dual-bucket). The old permanent no-card tier is gone (lost ~2026-08-17); Sept 2026 reports describe a $5 trial credit after adding a verified payment method, expiring in 30 days — third-party, not restated on the fetched page.
- [OpenRouter (:free)](https://openrouter.ai/docs/api_reference/limits) — ⚠️ unverified. `:free` model IDs cost $0 per input/output token. Reported platform limits: 20 RPM / 50 RPD on unfunded accounts, 1,000 RPD after ≥$10 lifetime purchase; daily UTC reset, account-wide; some free models require prompt logging; negative balance can block even free models. Catalog rotates.
- [Fireworks AI](https://docs.fireworks.ai/faq-new/billing-pricing/) — ✅ verified. $1 in free credits — starter credit. No expiry, recurrence, no-card terms, or RPM stated on the page. Gotchas: Not a permanent recurring tier; expiry and limits unconfirmed; Prepaid credits after exhaustion.
- [Nebius Token Factory](https://docs.tokenfactory.nebius.com/) — ✅ verified. $1 trial credit on first signup. Valid 30 days. Gotchas: Billing setup mandatory — card required to complete onboarding; card can be auto-charged at threshold or on negative balance; Product renamed to Nebius Token Factory — old AI Studio docs may be stale.
- [Hugging Face Inference Providers](https://huggingface.co/docs/inference-providers) — ✅ verified. Free users: $0.10/month; PRO users: $2/month (subject to change). Auto-applied to routed requests; no public numeric request-rate limit stated. Gotchas: Extra usage requires purchased credits; custom provider keys don't receive HF credits; Upstream model availability rotates and may 404/410; $0.10/month is small — heavy models drain it in a few turns.
- [Pollinations.ai](https://pollinations.ai/) — ✅ verified. 'Free Pollen for prototypes & testing' earned via Quests; user-pays BYOP model — apps let end users spend their own Pollen. No fixed public quota stated. Gotchas: Legacy anonymous endpoint / hourly refill / 1-Pollen-per-IP claims not established by opened official material — omitted; Split platform: legacy anonymous vs new keyed system — check which endpoint you're using.
- [Puter.js](https://puter.com/) — ✅ verified. User-pays model: developer infrastructure cost $0; every user starts with a free monthly allowance (amount unstated), prompted to upgrade when exhausted. No API keys; built-in Puter authentication. Gotchas: Not a provider-funded developer API — free usage depends on the end user's own Puter account; Users see a sign-in popup before AI calls work; Browser/client SDK only — not a server-side API key model.
- [Cloudflare Workers AI](https://developers.cloudflare.com/workers-ai/platform/pricing/) — ✅ verified. **10,000 Neurons/day at no charge** on both Workers Free and Paid plans ("Our free allocation allows anyone to use a total of 10,000 Neurons per day at no charge"); resets daily at 00:00 UTC; excess ops fail with an error. Gotchas: some frontier models require a Workers Paid plan ($5/mo minimum) even before the allowance is exhausted; account + account ID + API token required.
- [Cohere](https://cohere.com/) — ✅ verified. Free evaluation keys. Trial keys: 1,000 API calls/month; Chat 20 RPM; transcription 5/min; Embed 2,000 inputs/min; EmbedJob 5/min; Rerank 10/min; Tokenize 100/min; Parse/default 500/min. Gotchas: 'Evaluation-only / non-production' and training-data-use claims not established by the opened page — omitted unless separately verified.
- [Mistral La Plateforme](https://mistral.ai/) — ✅ verified. 'Free mode' — create API keys and use included monthly usage. Actual limits shown in signed-in Admin Panel → API → Limits (completion limits include tokens/minute and requests/second); no public quota numbers. Gotchas: 1B tokens/mo / 1 RPS / 500K TPM / no-card / all-model-access / training-default claims not established on the opened page — omitted.
- [Zhipu / Z.ai GLM (API)](https://docs.z.ai/guides/overview/pricing) — ✅ verified. GLM-4.7-Flash, GLM-4.5-Flash, GLM-4.6V-Flash fully free (input, cached input, cache storage, output). No public rate/concurrency or card/phone terms stated. Gotchas: Newer GLM-5.x Flash models are paid; 'limited-time Free' referred only to cache storage; Card/phone requirements conflict by region/source; Distinct from the consumer chat at chat.z.ai — API and chat quotas are separate.
- [Alibaba Cloud Model Studio (Qwen)](https://www.alibabacloud.com/help/en/model-studio/new-free-quota) — ✅ verified. 1,000,000 tokens per eligible model, International (Singapore) region only; account info must be completed. Valid 90 days from activation/model release/approval (whichever latest); real-time inference only; input+output share one quota. Gotchas: PAYG starts automatically after expiry/exhaustion unless 'Free Quota Only' is enabled (disabled by default); Eligible Sept-2026 model roster not verified — check the live table; Alibaba states submitted data is not used for model training; No free quota in other regions.
- [Novita AI](https://novita.ai/) — ✅ verified. Ling 3.1 Flash and Ling 3.0 Flash Sante priced Free (input and output free). No public usage quota stated. Gotchas: Sandbox voucher ($100/90-day) and ~$0.50 signup credit claims not confirmed on the page — omitted; The $100 sandbox voucher is compute credit, NOT LLM API inference credit; Sandbox terms reportedly prohibit commercial use without written permission.
- [Parasail](https://parasail.io/) — ⚠️ unverified. "Serverless - Free" tier for prototyping, reportedly 5 RPM (Qwen, DeepSeek, Llama series); third-party registry flags a linked payment method as required. Evidence is thin — verify on Parasail's pricing page.
- [Anthropic (starter credits)](https://platform.claude.com/) — ⚠️ unverified. Small one-time starter credit for new Console accounts — amount deliberately unpublished, no expiry stated; **no permanent API free tier**. Distinct from claude.ai free chat and from the Claude-for-Open-Source program (6 months of Max 20x for qualifying maintainers, launched Feb 2026).
- [DeepSeek (API grant)](https://platform.deepseek.com/) — ⚠️ unverified. Widespread third-party claim: 5M signup tokens, ~30-day expiry, no card — **but absent from DeepSeek's official pricing page**, so treat as unverified. Off-peak pricing is discounted, not free.
- [MiniMax (API trial)](https://www.minimax.io/) — ⚠️ unverified. No permanent free API tier; limited new-account trial credits (amount/expiry not reliable). Do NOT confuse with MiniMax Agent *consumer* credits (reportedly 1,000 signup + 200 daily-login credits).

---

## Free chat apps

No-cost chat surfaces and their message/model limits. Nearly all require a login; nearly all reserve the right to train on free-tier chats — see [privacy notes](docs/privacy-and-data-notes.md).

- [ChatGPT](https://chatgpt.com) — ✅ verified. ChatGPT Free includes GPT-5.2, web search, data analysis, file/image upload, image creation, GPT use, and voice. Usage limited within a five-hour window (no numeric message count published); tool limits are separate. Gotchas: Official FAQ still names GPT-5.2 — page text may lag current model names; Exact free quota is unpublished; Consumer chats used for training by default (opt-out available); Login required; Older free models retired on a schedule (GPT-5 retired Feb 13, 2026); Region restrictions in some countries.
- [Claude](https://claude.ai) — ✅ verified. Free: $0 — web/desktop/mobile chat, web search, file creation & code execution, memory, apps/tools connections, Artifacts. Limits reset on rolling five-hour windows; no fixed message count (varies by conversation complexity, model, features); Pro has ≥5x Free per five-hour session. Gotchas: Claude Code only in paid plans; Model training is opt-out; Login required.
- [Gemini app](https://gemini.google.com) — ✅ verified. Free (no AI plan): Gemini 3 Flash-Lite, Gemini 3 Flash, Gemini 3 Pro; 32K context; Canvas, Gems, Storybook, connected apps, Deep Research, Nano Banana 2 image generation, audio overviews. 'Standard limits' — compute-based, refreshing every five hours up to a weekly cap; no exact prompt count published; limits can change without notice; free users restricted first during high demand. Gotchas: Daily brief, Gemini Spark, video, scheduled actions, and Nano Banana Pro redo are NOT available on free; Google account required; Gemini Apps activity may be used for training unless paused.
- [Grok](https://grok.com) — ✅ verified. Free: $0/month — real-time web/X search, voice, connectors, 'generous limits'. No numeric prompt cap published on the official page; no official free-model name stated. Gotchas: Image/video creation and frontier models gated to paid SuperGrok; Login required (reports say X account 7+ days old with verified phone — unconfirmed on page).
- [Microsoft Copilot](https://copilot.microsoft.com) — ✅ verified. Free at no cost — chat, web-grounded answers, Edge summaries. No published numeric chat limit on this official page. Gotchas: No sign-in required for basic chat; signing in adds history, image creation, longer conversations, voice; Microsoft 365 desktop-app integration requires an eligible subscription; Copilot Pro retired late 2025; Data used for ads/personalization (opt-out exists).
- [Meta AI](https://www.meta.ai) — ⚠️ unverified. Free in WhatsApp, Instagram, Facebook, Messenger and meta.ai; no published message cap (platform rate limits only); Llama-based. Image generation reportedly limited (~25/day per one review); "Meta One" paid add-ons now exist. AI chats processed by Meta and may train models / personalize ads; person-to-person WhatsApp chats remain E2EE.
- [DeepSeek chat](https://chat.deepseek.com) — ⚠️ unverified. Web + app chat fully free, no ads, no in-app purchases (per official-doc mirror); DeepThink reasoning toggle, web search, file uploads; reviews report unlimited queries. Login via email/Google/Apple. Hosted in China — busy-period slowdowns, privacy scrutiny, regional restrictions.
- [Qwen Chat](https://chat.qwen.ai) — ⚠️ unverified. Consumer Qwen Chat free with Qwen3-series models (Qwen3.7-Max reportedly free for all since 2026-05-22); no published request cap. Account via email/phone. Note: Qwen's free *developer* OAuth/coding API route ended 2026-04-15 — consumer chat unaffected.
- [Kimi](https://www.kimi.com) — ✅ verified. Free basic services plus paid value-added services (official terms effective Aug 31, 2026); registration via phone or supported third-party account. Exact models, features, and query limits are not stated; responsiveness not guaranteed due to technical/resource limits. Gotchas: Inputs/outputs and feedback may be used for model optimization — contact Kimi to opt out; Login required.
- [Mistral Vibe (formerly Le Chat)](https://chat.mistral.ai) — ✅ verified. Free includes web/mobile Vibe, latest models, chat/search/creation, limited messages and web searches, limited coding sessions, image generation, Studio access, $10/mo API credits, 100+ connectors; task scheduling up to 5; document-upload storage limited. Exact baseline message/search/image counts unpublished (paid comparisons only: up to 6x Free messages, 5x searches, 40x image generations). Gotchas: Product rebranded from 'Le Chat' to 'Vibe'; Paid plans are model-training opt-out — Free is not shown as opt-out; Login required.
- [Perplexity](https://www.perplexity.ai) — ✅ verified. Free (Standard): practically unlimited basic searches, 3 Pro Searches/day, 1 Research query/month, automatic model selection, limited basic file uploads. 3 Pro Searches/day; 1 Research query/month. Gotchas: No advanced model selection, no image generation, no premium support; Free privacy tier is 'Standard' (no AI-training opt-out — paid consumer plans have opt-out); Account/login required.
- [ChatGLM (Z.ai)](https://chat.z.ai) — ⚠️ unverified. Consumer chat free with GLM-5.x-era model access; one third-party guide claims ~50 requests/day (unverified). Account via phone/email. Do not conflate chat quotas with the free API Flash models.
- [Doubao](https://www.doubao.com) — ⚠️ unverified. Consumer app reportedly free for daily chat/copywriting/lookup; paid Professional tiers (¥68/200/500/mo) launched 2026-06-24 — unconfirmed on official pages. unverified. Gotchas: China-focused; Chinese phone-number signup typical; Data hosted by ByteDance; Verification: official ByteDance consumer sites unreachable (timeouts) this session; 'free unlimited' claim softened — paid tiers exist per third-party reports, ByteDance's free-basics commitment unconfirmed officially (2026-09-30).
- [ERNIE Bot (Wenxin Yiyan)](https://yiyan.baidu.com) — ⚠️ unverified. **Fully free since April 1, 2025**, including latest ERNIE models, long-document processing, deep search, AI art, multilingual chat — no paid tier for chat, no explicit cap found. Baidu account + real-name verification; mainland-China availability.
- [GitHub Copilot Free (VS Code)](https://github.com/features/copilot) — ✅ verified. Copilot Free: limited access to a selection of Copilot features at no cost; 2,000 code completions/month plus a limited monthly allowance of GitHub AI Credits for chat and agent features; models via auto model selection only. Chat/agent usage varies with model and tokens processed (no fixed message count). Gotchas: From April 24, 2026 GitHub may use Free/Pro/Pro+ inputs/outputs for model training unless the user opts out; Free only for individuals without org/enterprise seat access; GitHub account required; telemetry/training settings configurable.
- [HuggingChat](https://huggingface.co/chat) — ⚠️ unverified. Free chat over ~120+ models; reviews claim no daily cap, but a mid-2026 technical doc says free accounts get only **$0.10/month inference credit** (~8–10 turns on expensive models) and heavy models drain it fast. HF login required; model availability and queueing are dynamic.
- [Poe](https://poe.com) — ⚠️ unverified. Bot-aggregator free tier: **300 compute points/day since ~2026-03-30** (down from 3,000/day), no rollover; each bot/message costs a different number of points — not a fixed message count.
- [You.com](https://you.com) — ⚠️ unverified. Free core chat/search with usage limits — but current 2026 free model/quota could not be reliably verified (old docs say unlimited basic chat; a 2025 aggregate says 25-query trial). Stale/conflicting data.
- [Duck.ai](https://duck.ai) — ✅ verified. Free within a daily limit; no account required; anonymized/proxied access to popular chatbots (GPT-4o mini, o3-mini, Llama 3.3, Mistral Small 3, Claude 3 Haiku — models periodically updated). Daily limit exists but exact number unpublished on the official page. Gotchas: Chats anonymized via proxying and never used for AI model training; recent chats stored locally on-device only; DuckDuckGo states it plans to keep the current level of access free.
- [Venice.ai](https://venice.ai) — ✅ verified (official blog). Privacy-first free tier, **no login**: **10 text prompts/day + 15 image prompts/day**, base models; Pro $18/mo = unlimited text, 1,000 images/day. No video/API on free; no training on inputs; chats stored in-browser by default.
- [LMArena](https://lmarena.ai) — ⚠️ unverified. **100% free**, no sign-up: anonymous side-by-side model battles, direct chat with featured models, voting, leaderboards; file uploads up to ~10MB per one guide. Research project — prompts are logged and may enter published datasets; don't share sensitive data.

---

## Open-weight models you can run locally

Download once, run forever: open weights mean zero marginal cost (your hardware is the bill). Runners are listed at the end.

- [Llama (Meta)](https://www.llama.com/models/llama-4/) — ✅ verified. Open weights under the Llama 4 Community License — free to download, intended for commercial and research use, zero marginal cost once downloaded. Hardware: Scout fits single H100 (Int4); Maverick FP8 fits a single H100 DGX host, BF16 needs multi-GPU. Gotchas: Custom Llama 4 Community License — NOT open source (no OSI approval); Attribution ('Built with Llama') required on redistribution; Use must comply with Meta's Acceptable Use Policy; Licensees over 700M monthly active users need a separate license from Meta; Muse Glimmer (30B, Apache-2.0) shipped Aug 2026 per third-party reports — unverified on an official page.
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
- [IBM Granite 4.x](https://huggingface.co/ibm-granite/granite-4.0-350m) — ✅ verified. Open weights under Apache 2.0 — free use for both research and commercial purposes, zero marginal cost. Hardware: spans laptop to GPU class (micro/tiny/small dense + MoE-hybrid variants, via ibm-granite/* on Hugging Face).
- [Liquid AI LFM2.5](https://huggingface.co/LiquidAI) — ✅ verified (HF org). Tiny hybrids (230M/350M/1.2B) with official 4-bit MLX artifacts — edge-first, phones/edge devices.
- [OpenBMB MiniCPM5](https://huggingface.co/openbmb) — ✅ verified. Open weights under Apache 2.0 — zero marginal cost. Hardware: laptop/edge class with MLX 4-bit.
- [inclusionAI (Ant) Ling](https://huggingface.co/inclusionAI) — ⚠️ unverified. Ling-2.6-flash (104B-A7.4B) and Ling-3.0-flash (124B-A5B hybrid KDA+MLA, true 256K), MIT (third-party). 100B+ class — multi-GPU.
- [ByteDance Seed-OSS-36B](https://huggingface.co/ByteDance-Seed/Seed-OSS-36B-Instruct) — ✅ verified. Dense 36B (Aug 2025) with 512K native context, Apache 2.0 (third-party) — single high-end GPU class.

### Runners — how to actually run them

- [Ollama](https://ollama.com/library) — ✅ verified. `ollama run <model>` — pulls, quantizes, and serves behind a local OpenAI-compatible API (MIT). Tags in the wild: `gpt-oss:20b`, `qwen3.5:2b`, `gemma4:e2b-it-qat`, `phi4-mini:3.8b`, `nemotron-3-nano:4b`, `kimi-k2.5`.
- [llama.cpp / GGUF](https://github.com/ggml-org/llama.cpp) — ✅ verified. Bare-metal C++ inference engine + the GGUF quantization standard; built-in `llama-server` (MIT). Best cost-performance on non-NVIDIA hardware (laptops, Apple Silicon, edge); MLX is the Apple-Silicon sibling.
- [LM Studio (runner)](https://lmstudio.ai) — ✅ verified. Free desktop app for downloading, discovering, and running local LLMs (GGUF/MLX) — zero marginal cost. Your hardware is the limit; available for macOS, Windows, Linux (llama.cpp; MLX on Apple Silicon). Gotchas: App itself is proprietary (not open source); free to download and use; Optional paid Enterprise tier reported by third-party guides — not confirmed on official pages; GUI-first: easiest path for non-CLI users to run local models.
- [vLLM](https://github.com/vllm-project/vllm) — ✅ verified. High-throughput serving engine (PagedAttention) with an OpenAI-compatible API — the standard multi-GPU choice for large MoE (Apache 2.0). SGLang is its closest alternative.

---

## Retired / changed free tiers

Free tiers that ended or changed materially, newest first.
- **GitHub Spark** (Aug 2026, verified) — officially retired Aug 31, 2026 (no new users since Aug 4, 2026); deployed apps still run. GitHub Models inference retired July 30, 2026.

- **Cerebras** (Sept 2026) — permanent no-card 1M tokens/day tier → card-gated Free Trial (dual-bucket limits, verified).
- **SambaNova** (~Aug 2026, delisted by trackers 2026-09-23) — free tier gone for new accounts; "Add a payment method and purchase credits to run your first requests". Stale docs still describe the old free tier.
- **Together AI / DeepInfra** (June–Sept 2026) — old signup-credit claims ($1/$5/$25) appear obsolete; minimum credit purchase required.
- **ChatGPT free quotas** (Sept 2026, verified) — official FAQ names GPT-5.2 with usage limited within a five-hour window; the third-party 'unlimited GPT-5.6 Luna' claims were unsupported by the official page.
- **xAI API** (Sept 2026, verified) — no free API tier on the official page (API billed per token; Playground included for testing); signup-credit/data-sharing-credit claims absent from official pages.
- **GitHub Copilot free** (Apr–Jun 2026, verified Sept 2026) — premium requests converted to AI Credits (2026-06-01); Free = 2,000 code completions/month + a limited monthly AI Credits allowance; Free/Pro/Pro+ inputs may train models unless opted out.
- **Mistral La Plateforme** (Sept 2026, verified) — official docs now describe a 'Free mode' with included monthly usage; quota numbers sit behind the signed-in Admin Panel (the old Experiment-tier numbers were never restated officially).
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

