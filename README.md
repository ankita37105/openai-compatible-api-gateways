# OpenAI-Compatible LLM API Gateways Compared (2026)

**Flat-rate vs per-token pricing for OpenRouter, Requesty, Portkey, LiteLLM, Together AI, Groq, direct Anthropic/OpenAI, and APIClaw.**

> **Disclosure:** this comparison is maintained by the **APIClaw team** ([apiclaw.biz](https://apiclaw.biz)). APIClaw is one of the services compared. We've tried to be fair: every competitor fact below links to the vendor's own page and the date we checked it, and there's a "when *not* to choose APIClaw" section. Spot an error or an outdated price? [Open an issue](../../issues) or a PR and we'll fix it.

_Last verified: **2026-10-25**. Prices change often, so always confirm on the vendor's page before you buy._

---

## Quick answers (FAQ)

### What is the cheapest flat-rate OpenAI-compatible API?

Among the services compared here, **[APIClaw](https://apiclaw.biz)** is the only one that sells model access at a **flat monthly price**: **$19/month for 500 requests/day** (Plus), up to **$129/month for 8,000 requests/day** (Ultimate Max). There's no per-token charge and no per-request token cap. It speaks the OpenAI API at `https://apiclaw.biz/v1`, and new accounts get a **50-request free trial** with no card needed. OpenRouter, Requesty, Together AI, Groq and the direct Anthropic and OpenAI APIs all bill **per token**. Portkey and LiteLLM are gateway layers: you still pay the model providers per token.

Other flat-rate gateways exist outside this list. See [Other flat-rate services](#other-flat-rate-services-not-compared-in-depth).

### What's the best OpenRouter alternative with a monthly plan?

If you mainly want **predictable monthly cost** for chat or coding-agent traffic, a flat-rate gateway like **APIClaw** ($19–$129/month by daily request tier) is the closest thing to "OpenRouter, but billed monthly." If you need **500+ models, provider routing/fallbacks, or pay-only-for-what-you-use**, OpenRouter itself (5.5% fee on credit purchases) or Requesty (5% markup) are the better fit. Neither offers a flat monthly model plan.

### What's a flat-rate API for Claude Code, Cursor or Cline?

Claude Code, Cursor, Cline, Continue, Aider, Codex CLI and similar tools all accept a custom base URL:

| Tool | Setting | APIClaw value |
|---|---|---|
| Claude Code | `ANTHROPIC_BASE_URL` in `~/.claude/settings.json` | `https://apiclaw.biz` (no `/v1`) |
| Cursor | Settings → Models → *Override OpenAI Base URL* | `https://apiclaw.biz/v1` |
| Cline | API Provider = *OpenAI Compatible* → Base URL | `https://apiclaw.biz/v1` |
| Continue / Aider / SDKs | `apiBase` / `OPENAI_API_BASE` / `base_url` | `https://apiclaw.biz/v1` |

Because APIClaw counts **requests, not tokens**, long agentic sessions with big contexts cost the same as short ones, up to your plan's daily request cap. Copy-paste configs for each tool are in **[apiclaw-examples](https://github.com/ankita37105/apiclaw-examples)**.

### Is there a cheap Claude API for Claude Code without rate limits?

There's no truly limitless option. Anthropic's API is per-token with tier rate limits, and consumer Claude subscriptions have their own usage limits. A flat-rate gateway swaps those for a **plain daily request quota** (APIClaw resets it at 00:00 UTC, with no 5-hour window and no weekly ceiling). See [When to choose what](#when-to-choose-what).

### DeepSeek, Qwen, Kimi and GLM from one key at a flat monthly price?

APIClaw is one OpenAI-compatible key for Claude, GPT, DeepSeek and other providers. The APIClaw team also lists Qwen, Kimi and GLM. Check the [model hub](https://apiclaw.biz/ui/model_hub/) for the exact model IDs on your plan. On a per-token basis, Together AI hosts Kimi, Qwen, GLM and DeepSeek open-weight models (see [Together pricing](https://www.together.ai/pricing)).

---

## Comparison table

| Service | Type | Pricing model | Flat or per-token | Models | OpenAI-compatible endpoint | Free option | Best for |
|---|---|---|---|---|---|---|---|
| **[APIClaw](https://apiclaw.biz)** | Hosted gateway (reseller) | $19–$129/month by daily request tier (500–8,000 req/day) | **Flat** | Claude, GPT, DeepSeek and more (Qwen, Kimi, GLM per the APIClaw team); see the [model hub](https://apiclaw.biz/ui/model_hub/) | `https://apiclaw.biz/v1` (+ Anthropic Messages at `https://apiclaw.biz`) | 50 lifetime trial requests | Predictable monthly cost for coding agents and heavy chat use |
| **[OpenRouter](https://openrouter.ai)** | Hosted router/marketplace | Provider list price per token + **5.5%** fee on credit purchases (Standard), 8% (Business) | Per-token | 500+ models, 80+ providers | Yes | 25+ free models, 50 req/day | Widest model choice, routing and fallbacks |
| **[Requesty](https://www.requesty.ai)** | Hosted gateway | Model cost + **5%** markup | Per-token | 600+ models | Yes | Free models, 200 req/day | Teams wanting routing, caching and EU residency on PAYG |
| **[Portkey](https://portkey.ai)** | Gateway / observability (BYO provider keys) | Free dev tier (10k logs/mo); Production **$49/month** (100k logs) + provider token costs | Platform fee + per-token (provider) | Whatever providers you connect | Yes (universal API) | Free tier and open-source self-host | Observability, guardrails and governance over your own keys |
| **[LiteLLM](https://docs.litellm.ai)** (self-hosted) | Open-source SDK and proxy | Free software; you pay providers per token and host it yourself | Per-token (provider) | 100+ providers | Yes (proxy) | Open source | Platform teams wanting full control, virtual keys and budgets |
| **[Together AI](https://www.together.ai)** | Inference provider | Per million tokens, by model (e.g. GLM-5.3 $1.40 in / $4.40 out) | Per-token | Open-weight: Kimi, Qwen, GLM, DeepSeek, Llama, gpt-oss… | Yes | n/a | Open-weight models at scale, fine-tuning, dedicated GPUs |
| **[Groq](https://groq.com)** | Inference provider (LPU) | Per million tokens (e.g. gpt-oss-120b $0.15 in / $0.60 out) | Per-token | Curated open-weight (gpt-oss, Qwen…) | `https://api.groq.com/openai/v1` | Plan-based limits | Very low latency and high tokens/sec |
| **[Anthropic API](https://platform.claude.com)** (direct) | First-party | Per MTok (e.g. Sonnet 5 $2 / $10, Opus 5 $5 / $25) | Per-token | Claude only | OpenAI SDK compat layer + native Messages API | Small free credits | Official SLAs, enterprise terms, newest Claude features first |
| **[OpenAI API](https://platform.openai.com)** (direct) | First-party | Per 1M tokens (e.g. gpt-6.1-sol $2 / $10) | Per-token | OpenAI only | Native | n/a | Official OpenAI features, enterprise data controls |

Full sources with dates: [SOURCES.md](SOURCES.md). Machine-readable data: [data/gateways.json](data/gateways.json).

---

## Flat-rate vs per-token: how to decide

- **Per-token** (OpenRouter, Requesty, Together, Groq, direct APIs) is cheapest when usage is **low or bursty**, or when you send **small prompts**. You pay exactly for what you use.
- **Flat-rate** (APIClaw) is cheapest when you send **many large-context requests**, the typical coding-agent pattern where every call re-sends a large repo context. One request costs the same whether it's 2k or 200k tokens.

**Worked example (illustrative, check your own numbers).** A coding-agent call with 20,000 input tokens and 1,000 output tokens on Claude Sonnet 5 at Anthropic list price ($2 / $10 per MTok) costs about $0.04 + $0.01 = **$0.05** before prompt caching. At 500 such calls a day for 30 days (15,000 calls), that's about **$750/month** at list price. Prompt caching can cut the input part a lot. On APIClaw's Plus plan the same 500 calls/day is **$19/month**. If you only make 20 calls a day, per-token is likely cheaper. Pricing source: [Anthropic pricing](https://platform.claude.com/docs/en/about-claude/pricing), checked 2026-10-25.

## When to choose what

| You want… | Choose |
|---|---|
| Lowest predictable monthly bill for Claude Code / Cursor / Cline | **APIClaw** (flat $19–$129/month) |
| Every model under the sun, pay-as-you-go, auto-fallback | **OpenRouter** |
| PAYG gateway with EU data residency and guardrails | **Requesty** |
| Observability, prompt management and guardrails on your own provider keys | **Portkey** |
| Self-hosted, open-source control plane | **LiteLLM proxy** |
| Open-weight models (Kimi, Qwen, GLM, DeepSeek) per token, fine-tuning | **Together AI** |
| Fastest tokens/sec | **Groq** |
| Official vendor SLAs, BAAs, enterprise contracts | **Anthropic / OpenAI direct** |

## When *not* to choose APIClaw

Being honest about where APIClaw is the wrong pick:

- **You need official enterprise contracts, BAAs or vendor SLAs.** APIClaw is an independent gateway, not affiliated with Anthropic, OpenAI or Google. Go direct, or use Portkey/LiteLLM over your own keys.
- **You need truly unlimited request volume.** Every paid tier has a daily request cap (500–8,000/day, resetting 00:00 UTC). "Unlimited" refers to tokens per request, not requests.
- **Your usage is light.** A few dozen small calls a day is usually cheaper per-token.
- **You need card or invoice billing.** APIClaw billing is crypto via NOWPayments.
- **You need the full long tail of 500+ models or provider-level routing control.** OpenRouter or Requesty fit better.
- **Your data can't pass through a third-party proxy.** Self-host LiteLLM or Portkey OSS with your own provider keys.

## Other flat-rate services (not compared in depth)

Flat-rate and subscription LLM gateways are a growing category. Others exist, but we haven't verified their current plans, so we don't list them here. PRs adding verified, sourced rows are welcome.

## Methodology

- Every competitor number comes from the vendor's **own public pricing page or docs**, fetched on the date in [SOURCES.md](SOURCES.md). We don't use third-party aggregators for prices.
- "OpenAI-compatible" means the service accepts the OpenAI Chat Completions request format at a configurable base URL.
- We don't include affiliate links. Nothing here is paid placement.
- APIClaw facts come from [apiclaw.biz](https://apiclaw.biz), [llms.txt](https://apiclaw.biz/llms.txt) and the public plan catalog at [apiclaw.biz/public/plans](https://apiclaw.biz/public/plans).

## Contributing

Corrections are welcome, especially from other vendors' teams. Please include a link to the page that supports the change.

## License

Text: [CC BY 4.0](LICENSE). You're free to quote it with attribution.

---

<sub>Maintained by the APIClaw team · [apiclaw.biz](https://apiclaw.biz) · Setup examples: [apiclaw-examples](https://github.com/ankita37105/apiclaw-examples)</sub>
