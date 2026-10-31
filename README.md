# Awesome-SAAS-Billing-Credit-Management

# Top SaaS Billing & Credit Management Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Usage Metering, Credit Wallets & Self-Hosted Billing Engines*  
**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **SaaS Billing & Credit Management**. These tools enable businesses to meter usage, manage prepaid credits and wallets, handle subscriptions, and generate invoices—turning complex pricing models (usage-based, hybrid, credit-based) into accurate, auditable revenue.

**Examples** include Atlassian Wallet, Stripe Billing, Chargebee, Maxio, Zuora, Recurly, Lago, Orb, Metronome, and Ordway (the category leaders).

**Open-source emphasis**: SaaS Billing & Credit Management is a domain where open-source tooling has **matured significantly, with several production-grade engines now available**. **OpenMeter** leads for usage-based and credit-based models—Apache 2.0 licensed, with real-time metering, prepaid credits, entitlement enforcement, and invoice generation, processing billions of events in production . **Lago** is the healthiest open-source Stripe Billing/Chargebee alternative (AGPL-3.0, 96/100 health score, 11k stars), focused on metering and usage-based billing . **Kill Bill** remains the most mature subscription billing platform (Apache 2.0, in production since 2010) with payments, invoicing, and dunning . For credit-ledger specifically, **Bursar** provides a canonical PostgreSQL schema with reserve-then-settle leases and multi-language SDKs , while **PayCan** offers a self-hosted credit wallet engine with drop-in UI modals for AI/SaaS apps . The critical caveat: **Atlassian Wallet (BambooHR's product) is a commercial wallet system** with no open-source equivalent—it handles manual reloads and store credit within its own ecosystem, not general SaaS billing .

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Atlassian Wallet](https://crosslinktax.atlassian.net/wiki/spaces/CSC/pages/1869295407)**  
  Commercial wallet and credit system (within the Atlassian/BambooHR ecosystem) for managing prepaid balances and store credit; supports manual reloads via vaulted credit cards or ACH (with signature capture), and applies credits toward purchases and services . **Scope-limited**—it manages wallet balances within its own platform, not general SaaS subscription billing or usage metering.

- **[Stripe Billing](https://stripe.com/billing)**  
  The developer-standard for recurring billing; subscriptions, invoicing, proration, usage-based billing, and dunning with deep integration into Stripe's payment ecosystem.

- **[Chargebee](https://www.chargebee.com/)**  
  Subscription management platform with revenue recognition (Chargebee RevRec), supporting complex billing models, dunning, and integrations with major payment gateways.

- **[Maxio](https://www.maxio.com/)**  
  Financial operations platform for B2B SaaS combining subscription billing (Chargify) and revenue recognition (SaaSOptics).

- **[Zuora](https://www.zuora.com/)**  
  Enterprise subscription management and revenue recognition platform for recurring revenue businesses; covers billing, collections, and RevPro compliance.

- **[Recurly](https://recurly.com/)**  
  Subscription management and billing platform focused on reducing churn and automating recurring billing workflows.

- **[Lago (Cloud)](https://www.getlago.com/)**  
  Managed version of the open-source Lago; usage-based billing with metering, invoicing, and payment provider integrations.

- **[Orb](https://www.withorb.com/)**  
  Usage-based billing platform for modern SaaS; focuses on flexible pricing models, metering, and revenue recognition.

- **[Metronome](https://metronome.com/)**  
  Usage-based billing platform for software companies; handles metering, pricing, invoicing, and revenue recognition for complex models.

- **[Ordway](https://ordwaylabs.com/)**  
  Billing and revenue automation platform for subscription businesses; handles complex pricing, invoicing, and revenue recognition.

## Open-Source GitHub Projects

### Usage Metering & Credit-Based Billing (OpenMeter)

- **[OpenMeter](https://github.com/openmeterio/openmeter)**  
  The **leading open-source metering and billing platform for AI, API, and usage-based products** (Apache 2.0) . Features: **real-time usage metering** via CloudEvents ingestion with flexible aggregations (SUM, COUNT, AVG, MIN, MAX); **usage-based billing** with tiered, graduated, and flat-fee pricing; **prepaid credits** with priority-based burn-down and expiration; **usage limits and entitlements** for feature gating; product catalog (plans, add-ons, rate cards); customer portal with token-based self-service; **LLM cost tracking** for AI token usage . Architecture: Go, PostgreSQL (billing), ClickHouse (usage analytics), Kafka (event streaming) . **Critical caveat**: releases are **beta and can include breaking changes**—the metering engine has run in production for years, but the billing layer is evolving . Docker Compose quickstart available. **Best for AI, API, and DevTool companies needing usage-based billing with prepaid credits**—the most complete open-source option for credit-based monetization .

### Subscription & Invoicing Platforms (Lago, Kill Bill)

- **[Lago](https://github.com/getlago/lago)**  
  The **healthiest open-source Stripe Billing/Chargebee alternative** (AGPL-3.0, 96/100 health score, 11k GitHub stars, active daily commits) . Focused on **metering and usage-based billing** with event ingestion, billable metrics, subscriptions, and invoicing. Docker image available. **Best for teams wanting a production-proven usage-based billing platform**—but AGPL copyleft may require legal review for commercial embedding, and it is less feature-dense than OpenMeter for credit/entitlement management.

- **[Kill Bill](https://github.com/killbill/killbill)**  
  The **most mature open-source subscription billing and payments platform** (Apache 2.0, in production since 2010, 5.8k stars, 95/100 health score) . Features: catalog and pricing (plans, phases, trials, add-ons), subscriptions (create/change/pause/cancel with proration), usage billing, invoicing, payments via gateway plugins, retries and dunning, tax plugins, multi-tenancy, and audit logs. **Best for complete subscription businesses** requiring payments and dunning alongside billing—but requires Java expertise and operational ownership.

### Credit Ledger & Wallet Engines (Bursar, PayCan, stapel-billing)

- **[Bursar](https://github.com/zonastery/bursar)**  
  Open-source **credit-ledger and billing SDK** for AI SaaS platforms . Features: **canonical accounting** (`credit_accounts.balance` as the only stored balance, `credit_ledger_entries` as the only monetary history); **reserve-then-settle leases** with idempotency keys, expiry, and strict-prepaid or overdraft policies; declarative versioned configuration (operations, rate cards, plans, allowances); AST-based safe expression evaluator (no `eval`); **identical behavior across Python, TypeScript, and Go SDKs** . PostgreSQL 16+ required. **Best for AI SaaS teams wanting a financially safe, audit-ready credit ledger** with multi-language support—but it is a ledger SDK, not a full billing platform with invoicing or payment processing.

- **[PayCan](https://github.com/gatewayhubs/paycan-credit)**  
  Open-source, self-hosted **payment and credit-management engine** for SaaS and AI apps . Features: **multi-type wallets** (e.g., `basic` compute vs. `premium` model tokens); automated top-ups on subscription renewals; **atomic metering and deductions** with metadata; **pre-built wallet modal UI components** (framework-agnostic, Shadow DOM, dark mode); admin panel with audit logs; **Stripe and PayPal** unified gateway; subscriptions and one-time products . **Best for developers wanting a drop-in credit wallet system** with UI components—but it is earlier-stage than OpenMeter or Kill Bill, and the admin panel requires Filament/PHP.

- **[stapel-billing](https://pypi.org/project/stapel-billing/)**  
  Open-source **Django app for per-user credit wallets** (v0.21.3) . Features: **credit lots with expiry** (spend walks expiring-soonest first); **reservations (hold/capture/release)** for work priced after it runs; **partial charges** recording uncovered amounts as collectable debt; plan bundles granted with or without a payment provider; Stripe-backed checkout; customer portal; idempotent webhooks . **Best for Django teams** wanting credit wallet primitives with expiry-aware lots and reservation semantics—but it is a framework-specific library, not a standalone platform.

### Additional Strong Open-Source Options

- **credit-management (PyPI)** — Open-source Python credit management library (v0.5.1) with FastAPI router, **reserve-then-deduct middleware** for AI token usage (reserves estimated credits, deducts actual usage from response), MongoDB or in-memory storage, and subscription plans . **Best for Python/FastAPI teams** wanting a lightweight credit middleware—but it is a library, not a full billing platform.
- **Invoice Ninja** — Open-source invoicing platform (Elastic-2.0, source-available, 10k stars, 96/100 health) with subscriptions, recurring invoices, and client portal . **Best for freelancers and small businesses** wanting invoicing—but it is invoice-centric rather than usage-metering-focused, and Elastic-2.0 is not OSI-approved.
- **Akaunting** — Open-source accounting software (BUSL-1.1, 10k stars) for small businesses and freelancers . **Best for basic accounting and invoicing**—not a SaaS billing engine with metering or credits.

**Frameworks for building custom systems**: For **usage-based billing with prepaid credits and entitlements**, OpenMeter is the most complete open-source option (accepting beta status for billing features) . For **metering and invoicing without credit complexity**, Lago (accepting AGPL) . For **subscription billing with payments and dunning**, Kill Bill . For **a financially safe credit ledger SDK**, Bursar . For **drop-in credit wallets with UI**, PayCan . For **Django credit wallet primitives**, stapel-billing . No open-source project matches **Atlassian Wallet's managed store-credit system**—that is a platform-internal feature, not a general SaaS billing product .

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- SaaS billing and credit management platforms handling payment data and financial records must comply with **PCI DSS** requirements and applicable tax regulations (VAT/GST/sales tax); **self-hosted solutions place full responsibility for payment gateway security, tax configuration, and financial data integrity on the operator**.
- **Open-source SaaS billing and credit management is mature but carries honest caveats**—OpenMeter provides the most complete usage-based and credit-based billing engine, but its billing releases are **beta with breaking changes** ; Lago is the healthiest metering/invoicing option but uses **AGPL copyleft** ; Bursar and stapel-billing provide credit-ledger primitives but are **SDKs/libraries, not full platforms** . **Atlassian Wallet is a commercial platform-internal wallet** with no open-source equivalent . Choose based on whether you need usage metering (OpenMeter, Lago), subscription payments (Kill Bill), or credit ledger primitives (Bursar, PayCan).
- Verify license terms for commercial use; OpenMeter uses Apache 2.0 , Lago uses AGPL-3.0 , Kill Bill uses Apache 2.0 , Bursar is open-source (check repository) , and PayCan is open-source (check repository) .

---

**Made for billing engineers, SaaS finance teams, and organizations choosing their monetization infrastructure.**  
Let's make SaaS billing and credit management more open, but with clear eyes about the beta status and licensing trade-offs that define each path.
