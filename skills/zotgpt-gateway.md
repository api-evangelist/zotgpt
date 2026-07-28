---
name: zotgpt-gateway
description: >-
  Call UC Irvine's ZotGPT Gateway — the campus unified AI API gateway — to run
  chat completions or embeddings against any model in the UCI Model Catalog,
  routing to OpenAI, Anthropic on AWS Bedrock, Google, or Azure through a single
  endpoint and a single campus-issued virtual key. Use when working inside UC
  Irvine and you need model access that stays under campus data policy and
  campus budget control.
generated: '2026-07-28'
method: generated
source:
  - https://zotgpt.uci.edu/services/gateway/
  - https://zotgpt.uci.edu/services/gateway/clients/
  - https://zotgpt.uci.edu/services/migrate-azure-api/
api: openapi/zotgpt-gateway-openapi.yml
provider: ZotGPT (UC Irvine)
providerId: zotgpt
---

# Using the ZotGPT Gateway

The ZotGPT Gateway is UC Irvine's single front door to AI models. It is not a
model — it is an indirection layer. You name a campus alias and a model slug; UCI
holds the vendor contracts, the vendor keys, and the budget behind it.

## Before you start

1. Sign in at the Gateway portal with your UCInetID. There is no separate
   registration and no Active Directory account required.
2. Mint a **virtual API key** inside your workspace. Treat it as a password.
3. Confirm your entitlement. Faculty, staff, and graduate students qualify
   directly and get **$50 in free credits**. Undergraduates need a sponsoring PI.
   Higher budgets require KFS account validation.

## The three-step setup, for any client

UCI documents the same pattern regardless of what you are wiring up:

1. Point the base URL at the Gateway instead of the vendor default.
2. Replace the vendor API key with your virtual key.
3. Select a model slug from the Model Catalog and restart.

## Base URLs

| Client shape | Base URL |
|---|---|
| OpenAI-compatible | `https://api.portkey.ai/v1` |
| Anthropic-style | `https://api.portkey.ai` |

## Authentication

Send your virtual key in the `x-portkey-api-key` header. Anthropic-style clients
such as Claude Desktop are documented to use the `bearer` auth scheme instead.

## Choosing a provider and a model

Routing is by campus alias, carried either in the `x-portkey-provider` header or
as a prefix on the model slug:

- `@zotgpt-api-bedrock` — Anthropic models via AWS Bedrock
- `@openai-prod` — OpenAI models

A full documented slug looks like:

```
@zotgpt-api-bedrock/us.anthropic.claude-opus-4-7
```

New models are added to the catalog continuously **without code changes** on your
side. Prefer selecting from the catalog over hardcoding a vendor model name.

## Chat completions

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_VIRTUAL_KEY",
    base_url="https://api.portkey.ai/v1",
)

resp = client.chat.completions.create(
    model="@zotgpt-api-bedrock/us.anthropic.claude-opus-4-7",
    messages=[{"role": "user", "content": "Summarize this syllabus in five bullets."}],
)
```

Set `stream=True` for Server-Sent Events. Embeddings use the same base URL and
key against `/embeddings`.

## Migrating off the deprecated Azure API

The old endpoint is being switched off in three phases: signups frozen, a
three-month self-migration window, then all remaining Azure keys disabled. Model
names and request structures do not change — only the host and the credential.

```python
# before
client = OpenAI(api_key="YOUR_AZURE_API_KEY",
                base_url="https://api.azureapi.zotgpt.uci.edu/v1")

# after
client = OpenAI(api_key="YOUR_VIRTUAL_KEY",
                base_url="https://app.portkey.ai/v1")
```

## Budget, not rate limits

UCI publishes **no requests-per-minute or tokens-per-minute ceiling**. What it
publishes is a spend ceiling: dollar-denominated credits, per-key spend limits,
and workspace budget enforcement. Plan for budget exhaustion, not throttling —
and note that the effective cost of a call depends on which model and which cloud
you routed to. If you hit a ceiling, request a tier upgrade with a KFS account
rather than retrying.

## Data handling you are agreeing to

- Everything runs under UC Irvine's **P3** protection standard.
- **Level 4 protected data is not permitted.** Do not send PHI.
- Content is retained up to 12 months, auto-deleted after, and deletable manually
  at any time.
- Campus data is not used to train vendor models.

## What is not there

Be aware of the gaps before you build against this:

- No published error catalog and no documented idempotency or retry contract.
- No machine-readable model catalog endpoint — the catalog is a portal page.
- No budget-remaining response header; check the portal.
- No first-party UCI SDK. Use the upstream Portkey SDKs (Python, JavaScript,
  .Net today; Java, PHP, Ruby, Go announced) or any OpenAI/Anthropic client.

## Getting help

- Bugs and feature requests: `zotgpt-support@uci.edu`
- Department or workflow integration: `oit-ai@uci.edu`
