---
name: diagnose-rpa-assets
description: Diagnose cross-border ecommerce customer RPA application assets and recommend adjacent AI+RPA expansion opportunities. Use when the user provides RPA app names, automation inventories, customer background, or an opportunity-map spreadsheet for Amazon/TikTok/Temu/eBay/Shopify/Ozon/Shopee/Lazada sellers and wants application classification, current automation maturity, opportunity-map coverage, gap analysis, prioritized adjacent expansion ideas, AI+RPA upgrade paths, risks, and CSM next-step recommendations. Do not use for customers with no landed RPA applications; use assess-customer-initial instead.
---

# Cross-Border Ecommerce RPA Asset Diagnosis

Version: V0.4

Use this skill to diagnose a customer's existing RPA application assets and turn them into adjacent AI+RPA expansion opportunities. The job is not to list every possible automation scenario. The job is to infer the customer's current automation profile, business focus, value gaps, adjacent expansion paths, and the next demand-entry points a CSM should verify.

For the Chinese human-readable counterpart, see `SKILL_CN.md`.

## Core Contract

Always start from the customer's existing RPA assets.

1. Analyze what the customer has already automated before recommending what to expand.
2. Separate confirmed facts, reasonable inferences, and hypotheses to verify.
3. Recommend adjacent expansion paths: next step of the same app, deeper work in the same role, same data-chain extension, or AI+RPA upgrade.
4. Risk-filter every P0/P1 recommendation for ERP, API, in-house system, page stability, AI trust, data definition, and business ownership risks.
5. Serve the CSM's next action: whom to talk to, what to ask first, how to probe, and which pilot to choose.
6. Do not generate a full project plan, quote, or implementation schedule unless the user explicitly asks after the diagnosis.
7. Do not copy the opportunity map as a scenario list. Use it only as a reference.

## When To Use

Use this skill when the user provides any of the following:

- Existing RPA app names, robot names, automation inventory, screenshots, or exported app data.
- A request to identify which business roles, workflows, or departments current RPA apps cover.
- A request to infer next expansion needs from existing RPA apps.
- A request to compare current apps with a cross-border ecommerce automation opportunity map.
- A request to identify which existing RPA apps can become AI+RPA pilots.
- A CSM use case such as renewal, upsell, AI pilot, executive report, customer visit, or demand discovery.

Do not use this skill when the customer has no landed RPA apps or no app list. Use `assess-customer-initial` instead. If the user provides meeting notes without an extracted app list, first extract the app facts. If the user asks for stability, success rate, or usage-rate evaluation, request or use runtime data; app names alone only support name-level diagnosis.

## Default Reference

The default opportunity map is:

```text
references/cross-border-ecommerce-automation-opportunity-map.xlsx
```

When using this skill, try to open this file first and use it as the main reference for scenario matching, coverage analysis, and gap finding. If the user provides a newer opportunity map, use the user's file instead.

Read the Excel with `openpyxl.load_workbook(..., read_only=False, data_only=True)` when possible. Some sheets may appear as only `A1` in `read_only=True` mode because of worksheet dimension metadata.

## Input Handling

Minimum input:

```text
Customer name: optional
RPA app names:
1.
2.
3.
```

Preferred additional fields: customer type, sales platforms, category, product type, supply model, ERP/system, team size, SKU count, store count, app usage state, and current objective.

If fields are missing, do not stop and do not invent facts. Continue with conservative conclusions and place missing items in "questions to verify".

Boundary rules:

- With only app names, output conservative classification, likely roles/workflows, current RPA profile, adjacent expansion directions, and verification questions.
- Do not assert customer type, organization structure, leadership intent, true pain points, or ROI without evidence.
- If ERP/system is missing, explicitly flag ERP replacement risk as unverified.
- If runtime data is missing, do not equate app count with value.

## Required Thinking Flow

Follow these steps in order:

1. Identify input completeness and current objective.
2. Standardize app names while preserving original names in output.
3. Decompose each app name into platform, business object, action, data/file type, and business intent.
4. Match app -> business object -> action -> role -> workflow -> opportunity point.
5. Judge confidence, automation level, and pain type.
6. Aggregate the customer's RPA usage profile.
7. Compare with the opportunity map by role/workflow coverage.
8. Find only related gaps near existing apps or data chains.
9. Generate adjacent expansion suggestions.
10. Identify AI+RPA upgrade paths.
11. Risk-filter and prioritize P0/P1/P2.
12. Output CSM next-step actions.
13. Run the verification checklist.

## Classification Rules

### Role Matching

Use business object first, action second, platform third, and customer background only as a correction.

| App signals | Primary role |
|---|---|
| ads, ACOS, CPC, SP/SB/SD, bulk, keyword, negative keyword, budget, campaign | Ad operations |
| bills, settlement, reconciliation, invoices, tax, fees, profit, payment, vouchers | Finance/reconciliation |
| orders, labels, shipping, logistics, warehouse, inventory, FBA shipment, overseas warehouse | Warehouse/logistics |
| suppliers, purchasing, 1688, inquiry, reminder, delivery date, factory, replenishment | Supply chain/procurement |
| reviews, emails, tickets, refunds, returns, claims, account health, negative reviews | Customer service/after-sales |
| listing, title, bullet points, variation, publishing, A+, images | Operations |
| BSR, competitors, new products, category, market research, pricing band, sales estimate | Product research |
| influencers, KOL, TikTok creators, Instagram, YouTube, social, content | Marketing |
| daily report, monthly report, dashboard, performance, profit attribution, management report | Management decision |

### Ambiguous Terms

- Inventory is not always logistics. Inventory sync/update is logistics; replenishment risk is supply chain/logistics; inventory value and turnover are management/finance; FBA inventory compensation is finance/after-sales.
- Keywords are not always ads. Ad keywords and negative keywords are ad operations; ABA/search ranking/natural keywords are operations; competitor/category keywords are product research; listing keywords are operations/ad operations.
- Reviews are not always customer service. Competitor reviews are product research; buyer review replies are after-sales; social comments are marketing; review pain-point extraction is product/operations.
- FBA depends on suffix. Shipment creation is logistics; inventory difference/compensation is finance/after-sales; FBA fees are finance; FBA replenishment is supply chain/logistics.
- Reports must be classified by content: sales report, ad report, finance report, executive dashboard, or multi-platform operations report.

### Automation Level

| Level | Signals | Current value | Next direction |
|---|---|---|---|
| L1 data moving | download, export, scrape, collect, upload, sync, copy, input, screenshot, archive | Reduce repetitive operations | summarize, clean, analyze, alert |
| L2 rule processing | summarize, clean, compare, validate, classify, rename, match, convert, split, merge | Apply business rules | detect exceptions, explain causes, generate reports |
| L3 analysis/alerting | analyze, monitor, alert, score, attribute, diagnose, review, trend, anomaly | Support management and decisions | AI+RPA pilot, executive reporting |
| L4 decision loop | recommend, strategy, auto-handle, auto-submit, smart assignment, dynamic pricing, replenishment/negative-keyword suggestion | High value but high risk | human review, permission boundaries, logs |

### Confidence

- High: business object and action are clear and match a role/workflow.
- Medium: the direction is clear but multiple roles may apply.
- Low: generic names such as "data processing", "operations table", "automation flow", "system sync", "test app". Low-confidence items should not drive strong recommendations.

## Coverage And Gap Rules

Coverage is by role/workflow, not by exact opportunity-map item.

- High coverage: multiple related apps indicate a responsible role, recognition, and usable foundation.
- Medium coverage: a few related apps; continue probing.
- Low coverage: almost no related apps; do not push aggressively unless the user's objective or background supports it.
- Unknown: app names are too generic.

Gap finding must be constrained:

1. First inspect gaps inside high-coverage roles.
2. Then inspect adjacent data-chain gaps.
3. Then inspect gaps strongly related to customer type, category, platform, or current objective.
4. Only then consider executive management or cross-department gaps.

Each gap must explain: map role/workflow, why it is a gap, how it relates to existing apps, why it is worth discussing now, priority, and what to verify.

## Recommendation Priority

P0 means worth discussing immediately. It should be strongly related to existing apps, have available data, a clear stakeholder, explainable value, manageable technical risk, and a natural question from "what happens after the current app runs?"

P1 means suitable for a pilot. It has clear value but needs more samples, business rules, human review, or cross-team coordination.

P2 means reserve for later. It has potential but lacks current asset support, needs new departments, requires more data integration, overlaps heavily with ERP/BI/in-house systems, or is too big for a first conversation.

Prefer these expansion paths in order:

1. Next step of the same app.
2. Deeper workflow in the same role.
3. Same data-chain extension.
4. Upgrade RPA execution into AI+RPA analysis.
5. Adjust based on the current business objective.
6. Related gap from the opportunity map.
7. Entirely new business direction, usually P2 only.

## Risk Filtering

Check every P0/P1 suggestion:

| Risk | Check | Treatment |
|---|---|---|
| ERP replacement | Does Lingxing, Jijia, Dianxiaomi, Mabang, etc. already cover it? | If highly covered, reposition as cross-platform, long-tail, or non-standard workflow support |
| API replacement | Is it standard system-to-system sync better handled by API? | Do not frame RPA as the advantage; frame process orchestration or non-standard supplement |
| In-house replacement | Does the customer have IT/dev capacity? | Emphasize fast validation, low-cost pilot, and business-side configuration |
| Page stability | Complex pages, frequent redesigns, captcha, anti-bot? | Reduce commitment; prefer files/API or add human fallback |
| AI trust | Ads, finance, pricing, infringement, refunds, or other high-risk judgments? | Use candidate lists and human confirmation, not full automation |
| Business ownership | Who is responsible if the AI suggestion is wrong? | Add approval, permission boundaries, and logs |
| Data definition | Are multi-platform/account metrics consistent? | Validate on samples before promising full accuracy |
| Organization coordination | Does the flow require cross-team rules or permissions? | Start with one role or one department pilot |

Never package high-risk scenarios as "AI automatically negative-matches", "AI automatically prices", or "AI automatically decides". Package them as "AI generates a candidate list; business users confirm; RPA executes in batch."

## Output Requirements

Default density:

- App profile: one short paragraph.
- App classification table: list all apps if fewer than 20; otherwise group and disclose grouping.
- Opportunity coverage: only high/medium coverage and relevant low coverage.
- Gap analysis: at most 5 gaps.
- P0 suggestions: at most 3.
- P1 suggestions: at most 3.
- P2 suggestions: at most 2.
- AI+RPA paths: at most 5.
- Verification questions: 3-5.
- Add a short module summary after each major module.

Use this exact output structure:

```markdown
# Customer RPA Asset Diagnosis and Demand Expansion Analysis

## 1. One-Sentence Conclusion

## 2. Input Completeness and Judgment Boundary

- Input completeness: high / medium / low
- Confirmed facts:
- Reasonable inferences:
- Hypotheses to verify:
- Key missing information:
- Judgment boundary:

**Module summary:**

## 3. Current RPA Usage Profile

**Module summary:**

## 4. RPA App Classification Details

| App name | Role | Workflow | Capability type | Automation level | Confidence | Evidence / notes |
|---|---|---|---|---|---|---|

**Module summary:**

## 5. Opportunity Map Coverage Analysis

| Role / module | Coverage | Existing app signals | Expandable gaps | Judgment |
|---|---|---|---|---|

**Module summary:**

## 6. Gap Analysis Against Scenario Map

| Gap direction | Role / workflow | Why it is a gap | Relation to existing apps | Recommend? | Priority | Information to verify |
|---|---|---|---|---|---|---|

**Module summary:**

## 7. Demand Expansion Directions

| Priority | Direction | Source evidence | Why recommend | Target stakeholder | Replacement / delivery risk |
|---|---|---|---|---|---|

**Module summary:**

## 8. AI+RPA Upgrade Paths

| Existing RPA app | Current value | Upgrade direction | AI role | RPA role | Risk control |
|---|---|---|---|---|---|

**Module summary:**

## 9. CSM Next-Step Recommendations

### 9.1 Priority departments
### 9.2 Suggested conversation topics
### 9.3 Recommended pilot
### 9.4 Directions not recommended for now
### 9.5 Questions to verify

1.
2.
3.
4.
5.

**Module summary:**
```

## CSM Question Bank

Prefer concrete questions tied to existing apps:

- Who uses this app now, and how often does it run?
- After the app runs, who reads the result? Does it enter a daily report, weekly report, or decision process?
- Does the app mainly save time, or does it affect business judgment?
- Which three apps are most valuable today, and why?
- Which apps are low-frequency, stopped, or replaced by ERP/in-house systems?
- After data is downloaded, who analyzes it? Is there a fixed template or rule?
- Which exceptions are still found manually?
- If data is already available, what should AI help inspect next?
- Which judgments must remain human-reviewed?
- Should this scenario be a reminder, a recommendation, or an automatic execution?

## Verification Checklist

Before final delivery, confirm:

1. The output is based on existing customer apps, not generic recommendations.
2. Input completeness and judgment boundary are stated.
3. Facts, inferences, and hypotheses are separated.
4. Each app or app group has role, workflow, level, confidence, and evidence.
5. Each P0/P1 has clear source evidence from existing apps or data chains.
6. ERP/API/in-house/page stability/AI trust/business responsibility risks are covered.
7. Gap analysis only includes related gaps.
8. The opportunity map is not copied wholesale.
9. CSM next questions are specific and usable.
10. No high-risk AI decision is framed as fully automatic without human review.
11. Each major module has a short summary.
12. The output is concise and focused.
