# ZotGPT (UC Irvine) (zotgpt)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

ZotGPT is the University of California, Irvine's institutionally-operated generative AI platform, built and run in-house by the [UCI Office of Information Technology](https://oit.uci.edu) AI Team rather than purchased as a vendor seat. It launched to faculty and staff in January 2024 and to students in April 2024, and now spans four end-user products, a training arm, and two generations of developer API. The platform is deliberately multi-cloud and multi-model: every interactive product runs on UC Irvine's own AWS accounts in us-west-2 behind Shibboleth SSO, the first-generation developer API was fronted by Azure API Management, and models are sourced across OpenAI, Anthropic on AWS Bedrock, Google, Azure, and open-source options.

- APIs.json: https://raw.githubusercontent.com/api-evangelist/zotgpt/refs/heads/main/apis.yml
- Website: https://zotgpt.uci.edu/

## Type

Index / Provider / 1st-Party

## Tags

Artificial Intelligence, Generative AI, LLM, AI Gateway, Higher Education, University, Multi-Cloud, Multi-Model, Chat Completions, Embeddings, Model Routing, Identity, United States, California

## APIs

- **ZotGPT Gateway** — Unified AI API gateway on the Portkey specification. One endpoint over OpenAI, Anthropic via AWS Bedrock, Google, and Azure; virtual API keys with per-key spend limits; provider routing by campus alias. [Docs](https://zotgpt.uci.edu/services/gateway/) · [Clients](https://zotgpt.uci.edu/services/gateway/clients/)
- **ZotGPT API (Deprecated)** — First-generation OpenAI-compatible chat completions endpoint fronted by Azure API Management, serving gpt-4o with $200 in starter credits. In phased retirement. [Docs](https://zotgpt.uci.edu/services/api/) · [Migration](https://zotgpt.uci.edu/services/migrate-azure-api/)

## Products

| Product | What it is |
|---|---|
| [Chat](https://zotgpt.uci.edu/services/chat/) | Free general-purpose AI chat for all of UCI. File upload, LaTeX, large context, multi-media. |
| [ClassChat](https://zotgpt.uci.edu/services/classchat/) | Course-scoped AI. Up to 1,200 pages of material per module; instructor prompts and visibility by design. |
| [Creator](https://zotgpt.uci.edu/services/creator/) | No-code custom assistant builder with document knowledge bases and an Agents feature. 1,000+ bots built. |
| [Prompt Library](https://zotgpt.uci.edu/prompts/) | 44 curated prompts across ~30 tags. |
| [Academy](https://zotgpt.uci.edu/services/academy/) | Self-paced AI literacy training. |
| [Marketplace](https://zotgpt.uci.edu/services/marketplace/) | Hub for community-created AI tools. |

## Specs

Neither API publishes a retrievable machine-readable spec — the Azure API Management developer portal gates its definitions behind sign-in, and the documented data-plane hosts do not resolve in public DNS. Both OpenAPIs below are marked `generated` and were built strictly from base URLs, headers, provider aliases, model slugs, and operations UC Irvine names verbatim in its own documentation.

- [openapi/zotgpt-gateway-openapi.yml](openapi/zotgpt-gateway-openapi.yml)
- [openapi/zotgpt-api-openapi.yml](openapi/zotgpt-api-openapi.yml)

## Artifacts

- Authentication: [authentication/zotgpt-authentication.yml](authentication/zotgpt-authentication.yml)
- Conventions: [conventions/zotgpt-conventions.yml](conventions/zotgpt-conventions.yml)
- Examples: [examples/zotgpt-gateway-examples.yml](examples/zotgpt-gateway-examples.yml)
- Packages & clients: [packages/zotgpt-packages.yml](packages/zotgpt-packages.yml)
- Agent skill: [skills/zotgpt-gateway.md](skills/zotgpt-gateway.md)
- Lifecycle & deprecation: [lifecycle/zotgpt-lifecycle.yml](lifecycle/zotgpt-lifecycle.yml)
- Changelog: [changelog/zotgpt-changelog.yml](changelog/zotgpt-changelog.yml)
- Conformance & compliance: [conformance/zotgpt-conformance.yml](conformance/zotgpt-conformance.yml)
- Domain security: [security/zotgpt-domain-security.yml](security/zotgpt-domain-security.yml)
- Well-known probe: [well-known/zotgpt-well-known.yml](well-known/zotgpt-well-known.yml)
- llms.txt: [llms/zotgpt-llms.txt](llms/zotgpt-llms.txt)

## Plans / Rate Limits / FinOps

- Plans & Pricing: [plans/zotgpt-plans-pricing.yml](plans/zotgpt-plans-pricing.yml)
- Rate Limits: [rate-limits/zotgpt-rate-limits.yml](rate-limits/zotgpt-rate-limits.yml)
- FinOps: [finops/zotgpt-finops.yml](finops/zotgpt-finops.yml)

ZotGPT is free to the entire UCI community. Developer access is metered in dollar-denominated credits rather than request rates — $50 on the Gateway free tier, higher budgets on KFS account validation. No requests-per-minute or tokens-per-minute ceiling is published anywhere.

## Infrastructure

Verified by live probe on 2026-07-28:

| Host | Cloud | Terminates on |
|---|---|---|
| zotgpt.uci.edu, chat.zotgpt.uci.edu | AWS us-west-2 | `zotgpt-lb.zot-gpt-prod.aws.uci.edu` |
| classchat.zotgpt.uci.edu | AWS us-west-2 | `oit-instrbt-lb.oit-instructorbot-prod.aws.uci.edu` |
| creator.zotgpt.uci.edu | AWS us-west-2 | `oit-creator-lb.oit-zotgptcreator-prod.aws.uci.edu` |
| portal.azureapi.zotgpt.uci.edu | Azure West US 2 | `oit-apim-usw2.azure-api.net` |
| api.zotgpt.uci.edu | — | does not resolve publicly |

Every human surface redirects to the campus Shibboleth IdP at `shib.service.uci.edu`.

## Gaps

- No anonymously retrievable OpenAPI on any host.
- Empty `/.well-known/` surface — no security.txt, llms.txt, API catalog, OIDC discovery, or agent card.
- No status page, no published SLA, no machine-readable changelog.
- No error catalog, no idempotency contract, no budget-remaining header.
- No machine-readable model catalog — the catalog is a portal page.
- No first-party SDK; UCI points at upstream Portkey SDKs.

## Timestamps

- Created: 2026-07-28
- Modified: 2026-07-28

## Review

[review.yml](review.yml)
