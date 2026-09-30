# Contributing

Thanks for helping keep this the most current directory of free-to-use LLMs!

## Adding an entry

1. **Check it fits:** an LLM, API tier, chat app, or open-weight model family that a user can genuinely use for **free** — no paid plan required to start. A PR must point at a primary source: the vendor's free-tier/pricing/docs page or the project's repo.
2. **Add to the right section** of `README.md`:
   - Free API tiers & inference endpoints → vendor free tiers, free-credit offers, and always-free inference endpoints
   - Free chat apps → no-cost chat/copilot surfaces with their message and model limits
   - Open-weight models you can run locally → model families with downloadable weights; one bullet per family
   - Retired / changed → free tiers that ended or changed materially, with the date
3. **One entry = one bullet.** Format:
   `- [Name](https://official-site-or-docs) — ` one-line description + what "free" actually means (limits, credits, expiry) inline.
   Tag free-tier confidence honestly: write `✅ verified 2026-09-29` only when you read the free-tier terms on the vendor's official page yourself; otherwise mark it `⚠️ unverified`. **Never invent a limit or credit amount.**
4. **Add the matching record** to `data/free-llms.json` with these exact fields:

| field | type | values |
|---|---|---|
| `name` | string | service / app / model family name |
| `vendor` | string | vendor / organization |
| `url` | string | official https:// URL (free-tier or docs page) |
| `description` | string | one sentence |
| `free_tier` | string | what "free" means, e.g. `"1,500 req/day, no card"` or `"unverified"` |
| `limits` | string | rate/credit/quota limits, or `"unverified"` |
| `gotchas` | string[] | 2–5 caveats (login, data-for-training, waitlist, region, expiry) |
| `free_verified` | bool | `true` only if you read the free terms on an official page |
| `source_url` | string | official page where the free terms appear, or `""` |
| `status` | string | `active` / `maintenance` / `archived` / `commercial` |
| `category` | string | `api` / `chat` / `local` |

5. **Status changes:** if a free tier ends, changes limits materially, or a chat app removes free access, update its README entry *and* add a row (newest-first) to the "Retired / changed free tiers" section.

## Style rules

- Link the **official site** (vendor free-tier/docs page or project repo), never a blog post or reseller.
- Facts that can change (limits, credits, model versions) get "as of" context in prose or are omitted — link the source instead of hard-coding numbers that rot.
- Vendor claims stay labeled as vendor claims ("vendor claims", "reported by community sources").
- Free-tier details in the README are stamped with their verification date; never guess a number. If the official page is ambiguous, mark it `⚠️ unverified`.
- Privacy-relevant facts (whether free-tier data trains models) must be sourced — see `docs/privacy-and-data-notes.md`.

## CI

Every PR runs:
- **Link check** (lychee) over all markdown files — no dead links.
- **JSON validation** — `data/free-llms.json` must parse, every record must have the required fields, and `status`/`category` must be from the allowed sets above.

Run locally before pushing:

```bash
python3 -c "import json; json.load(open('data/free-llms.json')); print('ok')"
```
