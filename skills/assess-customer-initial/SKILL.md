---
name: assess-customer-initial
description: Generate a pre-visit customer judgment card for cross-border ecommerce prospects that have not yet deployed RPA/AI+RPA or do not have usable automation assets. Use when Codex receives limited customer fields such as business model, category, product type, supply model, sales platforms, team size, SKU volume, ERP/system status, or business stage, and needs to infer a mixed customer profile, likely money-making logic, pain-point hypotheses, interview priorities, CSM discovery questions, and AI+RPA entry points before an early customer meeting.
---

# Assess Customer Initial

## Purpose

Create a concise CSM pre-visit battle card for cross-border ecommerce customers before RPA/AI+RPA has landed. The goal is not to produce a full solution proposal; the goal is to infer how the customer likely makes money, where high-value problems may exist, and how a CSM should open discovery so the customer feels understood.

Use this skill when the customer has no RPA application list or the application assets are too thin to diagnose. If the user provides a substantial RPA app inventory, say that the inventory is better suited for the RPA asset diagnosis skill, then use this skill only as customer-profile support.

## Inputs

Continue even when fields are incomplete. Mark uncertainty clearly and avoid invented facts.

Useful fields include:

- Customer name
- Customer model: brand-led, boutique, refined assortment, mass listing, or unclear
- Category and product type
- Supply model: trading, R&D/manufacturing/sales integrated, OEM, ODM, 1688, distributor, own factory
- Sales platforms: Amazon, TikTok Shop, independent site, Temu, eBay, Walmart, Ozon, Shopee, Lazada, multi-platform
- Team size
- SKU count and launch frequency
- ERP/system status
- Business stage
- Known context such as ad spend, influencer marketing, social media, supply chain, or organization structure

## Workflow

Follow this chain in order:

1. Judge input completeness.
2. Build a mixed customer profile using primary type + secondary type + possible transition direction.
3. Summarize the customer's likely money-making logic in one sentence.
4. Map customer signals to cross-border ecommerce business links.
5. Produce the Top 3 high-value pain-point hypotheses.
6. Rank visit topics by business value and discovery usefulness.
7. Exclude weak or premature AI+RPA entry points.
8. Output the battle card in the required structure.

Read `references/judgment-framework.md` when customer fields are provided or when detailed mappings, questions, exclusions, or the exact output template are needed.

## Core Rules

- Do not force the customer into one type. Use a percentage-style mixed profile such as `boutique 60% + brand transition 30% + refined assortment 10%`.
- Do not state pain points as facts. Use hypothesis language with evidence, likely business impact, AI+RPA fit, confidence, and validation questions.
- Do not ask generic questions such as "Do you need automation?", "Do you want RPA?", or "Do you want AI?"
- Ask around the customer's money-making logic, core metrics, business losses, roles, frequency, data sources, and decision chain.
- Prefer the Top 3 likely high-value topics over broad scenario lists.
- Keep the output like a CSM battle card, not a consulting report.
- If information is weak, explicitly state the judgment boundary and questions that must be validated.

## Quality Bar

A good output must:

- Explain the customer type without forcing a single label.
- Explain how the customer likely makes money.
- Derive business-link complexity from the provided fields.
- Give Top 3 pain hypotheses with evidence and validation questions.
- Tell the CSM what to discuss first and exactly how to ask.
- Identify directions not worth leading with.
- Stay business-focused, concrete, and executable.
