# Apizio — cheap OpenAI-compatible AI API

[![Discord](https://img.shields.io/badge/Discord-join-5865F2?style=flat-square&logo=discord&logoColor=white)](https://discord.gg/F6mBjR8Jnt)
[![API](https://img.shields.io/badge/API-OpenAI--compatible-412991?style=flat-square)](#quickstart)

<!--
  HERO IMAGE — do this before you launch.
  A screenshot or short GIF is the strongest conversion element on a README;
  visitors decide in about 15 seconds. Capture the Model Square (or a terminal
  running the cURL call below), drop it in the repo, then replace this comment
  with the image line:

  ![Apizio Model Square](docs/model-square.png)

  Deliberately left commented out so the README never shows a broken image.
-->

Apizio is a hosted AI gateway with an **OpenAI-compatible API**. Change one base
URL and reach **60 models** from OpenAI, Google, Alibaba, Zhipu, DeepSeek,
Moonshot, Meta, Mistral, xAI, Cohere, NVIDIA, MiniMax and more — on one key, one
balance and one bill.

**New accounts get $5 in free credits.**

**Most models are priced about 90% below the providers' published rates** — the
bulk of the catalogue sits at one tenth of list price. See [Pricing](#pricing).

| | |
|---|---|
| Base URL | `https://newapi.apizio.com/v1` |
| Web console | https://newapi.apizio.com |
| Model Square & live pricing | https://newapi.apizio.com/pricing |
| Live model rankings | https://newapi.apizio.com/rankings |
| Discord | https://discord.gg/F6mBjR8Jnt |

---

## Quickstart

Sign up, create a token on the Tokens page, then point any OpenAI-compatible
client at Apizio.

**cURL**

```bash
curl https://newapi.apizio.com/v1/chat/completions \
  -H "Authorization: Bearer $APIZIO_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gemini-2.5-flash-paid",
    "messages": [
      {"role": "user", "content": "Explain quantum entanglement in one paragraph."}
    ],
    "temperature": 0.7
  }'
```

**Python**

```python
from openai import OpenAI

client = OpenAI(
    base_url="https://newapi.apizio.com/v1",
    api_key="YOUR_APIZIO_KEY",
)

resp = client.chat.completions.create(
    model="gemini-2.5-flash-paid",
    messages=[{"role": "user", "content": "Hello"}],
)
print(resp.choices[0].message.content)
```

**Node / TypeScript**

```ts
import OpenAI from 'openai'

const client = new OpenAI({
  baseURL: 'https://newapi.apizio.com/v1',
  apiKey: process.env.APIZIO_API_KEY,
})

const resp = await client.chat.completions.create({
  model: 'gemini-2.5-flash-paid',
  messages: [{ role: 'user', content: 'Hello' }],
})
console.log(resp.choices[0].message.content)
```

Any client that accepts a custom OpenAI base URL can point here — no shim, no
adapter, no code rewrite.

---

## Why route through a gateway

- **One key for 60 models.** Instead of holding accounts with OpenAI, Google,
  Alibaba and Zhipu, keep one credential and one prepaid balance.
- **Swap models without touching code.** Change the `model` string and redeploy
  nothing. Useful when one provider has an outage or a price change lands.
- **Published pricing.** Every rate is listed in the Model Square, including
  cached-input rates, and it updates when upstream costs move.
- **Live performance data.** The [Rankings](https://newapi.apizio.com/rankings)
  board publishes latency, throughput and success rate per model, measured on
  real traffic — so you can pick on evidence rather than vibes.

<!--
  STRENGTHEN THIS SECTION. Anyone reading this already knows they can buy these
  models from the providers directly. The single most persuasive thing you can
  add is a plain explanation of where the discount comes from — which upstream
  you route through, and what the trade-off is. See 5-github-growth.md.
-->

---

## Endpoints

| Endpoint | Format | Notes |
|---|---|---|
| `POST /v1/chat/completions` | OpenAI | All 60 models |
| `POST /v1/images/generations` | OpenAI | `gpt-image-2-paid` |

**Authentication.** Send `Authorization: Bearer <TOKEN>`. Create and scope
tokens (by model, group, IP and rate limit) on the Tokens page of the console.

**Supported parameters:** `temperature`, `top_p`, `max_tokens`,
`frequency_penalty`, `presence_penalty`, `stop`, `seed`, `n`, `stream`,
`response_format`, `tools`, `tool_choice`, `logprobs`, `top_logprobs`,
`logit_bias`, `user`.

---

## Models

60 models are live. Browse the [Model Square](https://newapi.apizio.com/pricing)
for the authoritative list, current prices and per-model notes — the catalogue
moves, so this README lists families rather than pinning versions.

**OpenAI** — `gpt-5.6-terra-paid`, `gpt-5.6-sol-paid`, `gpt-5.6-luna-paid`,
`gpt-5.5-paid`, `gpt-5.4-paid`, `gpt-5.4-mini-paid`, `gpt-image-2-paid`, plus
`t/gpt-5-nano`, `t/gpt-5-4-mini`, `t/gpt-5-4-nano`, `t/gpt-4o-mini-2024-07-18`,
`t/gpt-oss-120b`, `t/gpt-oss-20b`

**Google Gemini** — `gemini-3.1-pro-preview-paid`, `gemini-3-flash-preview-paid`,
`gemini-2.5-pro-paid`, `gemini-2.5-flash-paid`, `t/gemini-3-1-flash-lite`,
`t/gemini-3-5-flash-lite`

**Qwen** — `d/qwen3.8-2.4t-a95b`, `d/qwen3.5-397b-a17b`

**Zhipu GLM** — `glm-5.3`, `glm-5.2`, `glm-4.7`, `GLM-5-Turbo`, `GLM-5v-Turbo`,
`d/glm-5.3`, `d/glm-5.2`, `d/glm-5.3-flash`, `n/glm-5.3`, `n/glm-5.3-flash`

**DeepSeek** — `deepseek-v4-pro-paid`, `d/deepseek-v4-pro`,
`d/deepseek-v4-pro-0813`, `d/deepseek-v4.1-flash`, `d/deepseek-v4-flash`,
`d/deepseek-v4-flash-0731`, `d/deepseek-v3.2`, `n/deepseek-v4.1-flash`,
`t/deepseek-v3-2`

**Moonshot / Kimi** — `d/kimi-k3`, `n/kimi-k3`, `d/kimi-k2.6`, `t/kimi-k2-5`,
`t/kimi-k2-thinking`

**Meta, Mistral, xAI, Cohere, NVIDIA, MiniMax** and others are served through the
`t/` namespace (`t/llama-4-maverick`, `t/llama-4-scout`, `t/mistral-small-4`,
`t/mistral-small-3-2-24b`, `t/grok-4-3`, `t/command-r7b-12-2024`,
`t/nemotron-3-ultra`, `t/minimax-m3`, `t/sonar`, …).

**Prefixes are routing, not tiers.** Some models are named with a prefix that
records the upstream they are routed through — `t/`, `d/` and `n/`. They are
normal, callable models: use the full name as the `model` string. They are
listed in the Model Square alongside the unprefixed ones and priced the same way.
(`t/auto` is the one special name — it routes a request to a suitable model
for you.)

> Some models carry a note in the Model Square such as *"Tool calling is
> broken."* That note is per-model, not global. Check the model's card before you
> rely on tool calling.

---

## Pricing

Priced per 1M tokens, USD. A representative sample — the
[Model Square](https://newapi.apizio.com/pricing) is the source of truth and
carries the full list, cached-input rates and per-group pricing.

**Most of the catalogue is set at roughly one tenth of the provider's own
published rate.** Models in the `-paid` group need a paid API key and carry a
smaller discount on the Gemini entries (about 40%); the GPT models in that group
are at the same ~90% as the rest.

| Model | Input | Output | Cached input |
|---|---|---|---|
| `gpt-5.6-luna-paid` | $0.02 | $0.12 | $0.002 |
| `gpt-5.4-mini-paid` | $0.075 | $0.45 | $0.0075 |
| `gpt-5.6-terra-paid` | $0.20 | $1.20 | $0.02 |
| `gpt-5.4-paid` | $0.25 | $1.50 | $0.025 |
| `gpt-5.6-sol-paid` | $0.40 | $2.00 | $0.04 |
| `gpt-5.5-paid` | $0.50 | $3.00 | $0.05 |
| `d/qwen3.8-2.4t-a95b` | $0.20 | $0.60 | $0.02 |
| `glm-4.7` | $0.06 | $0.22 | $0.011 |
| `gemini-2.5-flash-paid` | $0.18 | $1.50 | — |
| `gemini-3.1-pro-preview-paid` | $1.00 | $7.00 | $0.10 |

You pay from a single prepaid balance that covers every provider. The console
shows per-model cost and token statistics, and the
[Rankings](https://newapi.apizio.com/rankings) board publishes live latency,
throughput and success rates.

> **This table can be out of date — treat the website as the source of truth.**
> Rates move whenever upstream costs move, and this README is updated by hand, so
> it can lag. The always-current list is the Model Square pricing page:
> **https://newapi.apizio.com/pricing** — it carries every model, cached-input
> rates, per-group pricing and long-context tiers. Check it there before you
> budget anything. Table above last checked 2026-09-26.

> **GPT models are tiered by context length.** Above 272K input tokens the rate
> steps up: `gpt-5.6-luna-paid` goes to $0.04 / $0.18, `gpt-5.4-paid` to
> $0.50 / $2.25 and `gpt-5.5-paid` to $1.00 / $4.50. The Model Square lists both
> tiers per model.

> **Some models use dynamic pricing.** `d/deepseek-v4-flash`,
> `d/deepseek-v4-pro`, `d/deepseek-v4-pro-0813`, `d/deepseek-v4.1-flash`,
> `n/deepseek-v4.1-flash` and `t/minimax-m3` are billed by expression rather
> than a flat rate: the DeepSeek entries are cheaper off-peak and step up during
> weekday peak hours (UTC), and `t/minimax-m3` has a 524K-token long-context
> tier. The Model Square shows the currently-effective rate on each card.

### How that compares

Against the providers' published list prices (or the market rate where a vendor
does not sell the model directly). Rates are per 1M tokens, input / output.
Checked 2026-09-26.

| Model | Apizio | Provider list | You save |
|---|---|---|---|
| `t/gpt-5-nano` | $0.005 / $0.04 | $0.05 / $0.40 | **90%** |
| `t/gpt-4o-mini-2024-07-18` | $0.015 / $0.06 | $0.15 / $0.60 | **90%** |
| `t/command-r7b-12-2024` | $0.0037 / $0.015 | $0.0375 / $0.15 | **90%** |
| `t/kimi-k2-thinking` | $0.06 / $0.25 | $0.60 / $2.50 | **90%** |
| `t/gpt-oss-120b` | $0.003 / $0.017 | $0.15 / $0.60 | **98%** |
| `gemini-2.5-flash-paid` | $0.18 / $1.50 | $0.30 / $2.50 | **40%** |

Check any row against your own provider's pricing page, then against the
[Model Square](https://newapi.apizio.com/pricing), which is authoritative and
moves when upstream costs do.


## Support

Questions, model requests, issues and bug reports all go to **Discord** —
https://discord.gg/F6mBjR8Jnt.

---

## License

Apizio's own documentation and configuration in this repository are released
under the **MIT License** — see [LICENSE](LICENSE). The upstream projects it
builds on carry their own licenses, listed below.

<!--
  Add the LICENSE file before publishing this, and then uncomment the badge in
  the header row:

  [![License](https://img.shields.io/github/license/gaga-rgb/Cheap-ai-api?style=flat-square)](LICENSE)

  If you later publish code derived from New API, that code must be AGPL-3.0,
  not MIT. Only the non-code content here is MIT.
-->

---

## Built with

Apizio runs on [New API](https://github.com/QuantumNous/new-api), which is built
on [One API](https://github.com/songquanpeng/one-api). New API is licensed
AGPL-3.0; One API is MIT.

<!--
  AGPL-3.0 section 13: if you run a modified version of New API as a network
  service, you are required to offer the Corresponding Source to your users.
  If that applies to you, add a link to it here.
-->

---

If Apizio saves you money, a star on this repo is how the next person finds it.
