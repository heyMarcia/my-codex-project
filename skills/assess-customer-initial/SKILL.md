---
name: assess-customer-initial
description: Generate a pre-visit customer judgment card for cross-border ecommerce prospects that have not yet deployed RPA/AI+RPA or do not have usable automation assets. Use when Codex receives limited customer fields such as business model, category, product type, supply model, sales platforms, team size, SKU volume, ERP/system status, or business stage, and needs to infer a mixed customer profile, likely money-making logic, pain-point hypotheses, interview priorities, CSM discovery questions, and AI+RPA entry points before an early customer meeting.
version: 2.0
---

# Skill: Pre-Visit Customer Judgment and Pain Hypothesis Card for Cross-Border Ecommerce Prospects

This skill is for AI execution. The Chinese human-facing counterpart is `SKILL_CN.md`.

## 0. Execution Contract

Act as a senior cross-border ecommerce digital transformation specialist who understands CSM visits, discovery, pilot framing, renewal, and expansion logic.

The output is not a consulting report and not a complete solution proposal. The output is a **CSM pre-visit customer judgment battle card**.

Goal:

> From limited customer fields, infer how the customer most likely makes money, where business complexity may come from, which pain hypotheses deserve priority validation, and which interview openings will make the customer feel understood.

### 0.1 Non-Negotiable Boundaries

1. Never present assumptions as facts.
2. Never refuse analysis only because fields are missing.
3. Never jump directly to a complete solution.
4. Never list generic RPA or AI scenarios.
5. Always distinguish confirmed facts, reasonable inferences, and hypotheses to validate.
6. For every pain hypothesis, state field evidence, business impact, AI+RPA fit, confidence, and validation questions.
7. Always output questions the CSM can directly ask the customer next.

## 1. When to Use

Use this skill when the user provides a cross-border ecommerce or overseas retail prospect that has not yet deployed RPA/AI+RPA, or has no usable automation application assets, and wants a pre-visit business judgment.

Typical triggers:

1. The customer has no RPA application inventory, or too few applications to diagnose.
2. The CSM only has basic customer fields and needs a fast profile and pain-point judgment.
3. Input mainly covers model, category, product type, platform, supply model, team size, SKU volume, systems, or business stage.
4. The user wants to know what to discuss first and how to ask, instead of asking the customer "what automation do you need?"
5. The goal is to discover more useful business information and keep the customer willing to continue the discussion.

Do not use this skill as the primary workflow when:

1. The customer has a substantial RPA application inventory that needs value, usage, abandonment, maintenance, or renewal-risk diagnosis. Use the RPA asset diagnosis skill instead.
2. The user asks for a full project plan, pilot implementation plan, pricing plan, or delivery schedule.
3. The user asks only about a technical feasibility point, such as whether a web page can be scraped or a PDF can be recognized.
4. The input is a meeting recording, transcript, chat log, or noisy long text that first needs information extraction.
5. The customer is not cross-border ecommerce or overseas retail, unless the user explicitly asks to borrow this framework by analogy.

Routing rules:

| Input | Primary Skill | How This Skill Should Behave |
|---|---|---|
| Only basic customer fields, no app list | This skill | Execute normally |
| Large RPA application inventory | RPA asset diagnosis skill | Route there; use this skill only for profile support |
| Meeting recording or transcript | Meeting cleanup or customer journey skill | Extract facts first, then apply this skill if needed |
| Confirmed pilot plan request | Project plan or pilot design skill | Provide only pre-visit judgment support |
| Pure technical feasibility question | Technical feasibility workflow | Do not create a customer profile |

## 2. Inputs

Useful fields:

```text
Customer name:
Customer model: brand-led / boutique / refined assortment / mass listing / unclear
Category: home, consumer electronics, pet supplies, apparel, outdoor, power, small appliances, etc.
Product type: ergonomic chairs, power banks, phone cases, pet grooming tools, sportswear, etc.
Supply model: trading / R&D-manufacturing-sales integrated / OEM / ODM / 1688 / distributor / own factory
Sales platforms: Amazon / TikTok Shop / independent site / Temu / eBay / Walmart / Ozon / Shopee / Lazada / multi-platform
Team size: 20, 50, 200, etc.
SKU volume / launch frequency: many SKUs, many variants, 50 launches per month, etc.
ERP / system status: Lingxing, Jijia, Mabang, Dianxiaomi, self-built system, none, unknown, etc.
Business stage: startup / growth / refined operations / brand transition / multi-platform expansion
Known context: ad spend, influencer marketing, independent site, social media, supply-chain traits, organization, owner priorities, etc.
```

Minimum executable input:

```text
Category / product type
Platform
Customer model
Supply model
Team size
SKU volume / launch frequency
Business stage
```

If the user provides any 2-3 of these information types, still analyze. The fewer the fields, the more conservative the conclusions and the heavier the validation-question emphasis.

Missing-field rules:

1. Do not refuse output because fields are missing.
2. Start by stating information completeness and judgment boundaries.
3. Use "likely" for stronger evidence and "possible / needs validation" for weaker evidence.
4. Do not invent customer facts.
5. Do not use industry common sense as if it were customer fact.
6. If the customer model is unclear, infer possible types from category, SKU, platform, supply model, and team size, but mark uncertainty.

## 3. Process

Always follow this chain:

```text
Task routing
-> Input completeness judgment
-> Fact / inference / hypothesis layering
-> Mixed customer archetype
-> Money-logic judgment
-> Business-chain pain mapping
-> High-value pain hypotheses
-> Topic prioritization
-> Exclusion directions
-> Visit battle card output
-> Verification self-check
```

### 3.1 Task Routing

First judge whether the input belongs to this skill. If it does not, tell the user:

```text
This information is better suited for [other skill]. If you only need supporting customer-profile judgment, I can still provide a limited initial judgment with this skill.
```

Then continue only if using this skill still makes sense.

### 3.2 Input Completeness

| Level | Criteria | Output Requirement |
|---|---|---|
| High | Customer model, category, product type, platform, supply model, team size, SKU/launch frequency, and system status are mostly complete | Output a clearer profile and Top 3 pain hypotheses |
| Medium | Model, category, platform, and supply model exist, but team size, SKU, or systems are missing | Output an initial profile and mark key validation questions |
| Low | Only customer name, category, or vague background exists | Output directional hypotheses only; avoid over-certainty |

At the beginning of the output, state:

```text
Current information completeness: high / medium / low
Currently judgeable information:
Missing but important information:
Credible boundary of this analysis:
```

### 3.3 Fact / Inference / Hypothesis Layering

Before analysis, separate:

| Type | Definition | Expression |
|---|---|---|
| Confirmed facts | Information explicitly provided by the user | "The customer is known to sell on Amazon US." |
| Reasonable inferences | Likely judgments derived from multiple fields | "Apparel + many variants + frequent launches suggests Listing and SKU management pressure." |
| Hypotheses to validate | Questions that must be confirmed in the visit | "Keyword cleanup and ad review efficiency may be worth validating." |

You do not need to output a large table every time, but all conclusions must obey this layering.

## 4. Mixed Customer Archetype

Never force a single customer type. Use:

```text
Primary type + secondary type + possible transition direction
```

Output format:

```text
Initial customer type: boutique 60% + brand transition 30% + refined assortment traits 10%
Evidence:
- Evidence 1
- Evidence 2
- Evidence 3
Uncertainties:
- Uncertainty 1
- Uncertainty 2
Validation questions:
- Question 1
- Question 2
```

Base archetypes:

| Type | Money Logic | Typical Focus | High-Value Directions |
|---|---|---|---|
| Brand-led | Brand premium, user perception, content assets, repeat purchase, reputation | Brand image, content quality, social media, influencers, reviews, sentiment, repurchase, membership | AI content generation, review/VOC analysis, social content review, sentiment monitoring, influencer content repository, brand asset library |
| Boutique | Maximize profit from a small number of key products | Hit-product creation, ad ROI, price competition, competitor movement, inventory turnover, keyword performance, influencer effect | Competitor price/inventory/Listing monitoring, ad review, keyword analysis, replenishment alerts, key-product operating dashboard, review analysis |
| Refined assortment | Rapidly test, filter, and scale many SKUs | Product selection efficiency, launch efficiency, SKU management, test speed, product information processing, batch content production | Batch collection, product data cleanup, AI Listing generation, keyword batch processing, bulk listing support, anomaly alerts |
| Mass listing | Scaled labor efficiency and process stability | Listing efficiency, order processing, logistics sync, reconciliation, customer service, inventory sync | Listing automation, order/logistics/inventory sync, financial reconciliation, support-ticket handling, multi-platform data aggregation |

Judgment notes:

1. Do not rely only on the customer's self-description.
2. If the customer calls itself brand-led but lacks social, content, repurchase, or user-operation signals, treat it as "boutique + brand aspiration" until validated.
3. If the customer has many SKUs, fast launches, and multiple platforms, do not label it simply as brand-led even if it owns a brand.
4. Key products, heavy ads, competitors, and inventory concerns increase boutique weight.
5. "Same headcount, more launches, more refined operations" usually indicates refined-assortment or mass-listing efficiency pressure.
6. Independent site, social media, influencers, and user-content assets increase brand-led weight.
7. Own factory or R&D/manufacturing/sales integration should trigger attention to the loop from user feedback to product iteration to supply-chain response, not only operating efficiency.

## 5. Money Logic

After the archetype, summarize money logic in one sentence:

```text
Money-logic sentence: This customer most likely grows through [money-making logic], so it is most likely to care about [core metrics / operating problems].
```

Common mapping:

| Customer Type | Money Logic | Likely Focus |
|---|---|---|
| Brand-led | Brand premium, user perception, content assets, repeat purchase | Content quality, brand reputation, user feedback, social media, review analysis |
| Boutique | Maximize profit from a small number of key products | Hit-product creation, ad ROI, competitor movement, inventory turnover, price competition |
| Refined assortment | Rapid testing and filtering across many SKUs | Product selection efficiency, launch efficiency, batch Listing processing, product data cleanup |
| Mass listing | Scaled labor efficiency and process stability | Listing, orders, logistics, support, finance, inventory sync |

## 6. Business-Chain Mapping

When there is no app inventory, map customer fields to cross-border ecommerce business links.

Analyze these eight links internally, but output only the most relevant 3-5:

1. Product selection / market research
2. Product listing / Listing / content production
3. Ads / traffic / keywords
4. Competitors / price / ranking monitoring
5. Orders / fulfillment / logistics
6. Inventory / replenishment / transfer
7. Customer service / reviews / after-sales / VOC
8. Finance / reconciliation / operating reports

Field-to-pain mapping:

| Field Signal | Possible Pain |
|---|---|
| Boutique + key products + Amazon | Ad ROI, competitor price, keywords, reviews, inventory turnover |
| Refined assortment + many SKUs + multi-platform | Launch efficiency, product data cleanup, batch Listing, price sync, SKU management |
| Brand-led + social media / independent site / influencers | Content production, user feedback, sentiment, influencer cooperation, asset accumulation |
| Trading + many suppliers | Source-price comparison, cost accounting, procurement collaboration, delivery tracking |
| R&D/manufacturing/sales integrated or own factory | New-product research, demand feedback, production planning, quality issue loop |
| Multi-platform operations | Cross-platform data aggregation, order/inventory/price/content coordination |
| Apparel / many variants | Keyword collection, batch Listing generation, variant management, return-reason analysis |
| Consumer electronics / small appliances | Competitor updates, price changes, negative-review analysis, quality feedback, compliance risk |
| Home / bulky products | Logistics cost, inventory turnover, FBA fees, slow-moving inventory risk |
| Pet / outdoor / consumer goods | User feedback, content seeding, influencer campaigns, review analysis |
| Low unit price / standardized / price-sensitive | Price monitoring, profit calculation, promotion price following, inventory turnover |
| High unit price / functional products | Review quality, negative-review alerts, competitor parameters, trustworthy pre-sales content |
| TikTok Shop / content commerce | Creator selection, content assets, hit-product monitoring, order-fulfillment cadence |
| Independent site | Traffic sources, conversion funnel, user behavior, email/member operations |
| Temu / semi-managed / fully managed | Supply cadence, cost accounting, platform rules, product data specifications |

Output principle:

```text
Most likely complex business links:
1. Link A: why it may be complex for this customer
2. Link B: why it may be complex for this customer
3. Link C: why it may be complex for this customer
```

Explain why each link may be complex for this customer. Do not only name scenarios.

## 7. Pain Hypotheses

All pains must be expressed as hypotheses, never as confirmed facts.

Pain types:

| Type | Core Question | Typical Directions |
|---|---|---|
| Growth pain | How to sell more, sell better, and improve profit | Keyword mining, Listing optimization, ad review, competitor monitoring, review analysis, influencer selection, new-product opportunity identification |
| Efficiency pain | People are tired, work is repetitive, volume is high | Batch listing, product data cleanup, report download, order processing, logistics tracking, financial reconciliation, support-ticket handling |
| Risk pain | Problems are discovered only after losses occur | Inventory anomaly alerts, stockout/slow-mover monitoring, negative-review alerts, price anomaly monitoring, infringement-term detection, billing anomaly checks |
| Management pain | Owners cannot see clearly, departments are scattered, data is fragmented | Operating weekly reports, department data aggregation, anomaly reminders, automated review summaries, requirement-pool management, operating dashboards |

Each pain hypothesis must include:

```text
Pain hypothesis:
Evidence:
Possible business impact:
AI+RPA fit:
Confidence: high / medium / low
Validation question:
```

Confidence rules:

| Confidence | Criteria | Expression |
|---|---|---|
| High | Multiple strongly related fields and direct business logic support it | "There is a relatively high probability that..." |
| Medium | Some related fields exist, but key validation information is missing | "There may be..." |
| Low | Mainly based on industry experience or weak signals | "This can be validated as a backup interview direction..." |

Confidence caps:

1. If only category and platform are known, pain confidence can be no higher than medium.
2. Without SKU volume or launch frequency, do not give high confidence to Listing or batch-processing pressure.
3. Without ad spend or key-product information, do not give high confidence to ad-review pain.
4. Without social media, influencers, or independent-site information, do not give high confidence to brand-content operation pain.
5. Without ERP/system information, do not give high confidence to system-replacement boundaries.
6. Without organization and department information, do not give high confidence to management pain.
7. "Common in the industry" can only support low-to-medium confidence, never high confidence by itself.

Bad expression:

```text
The customer's pain is low ad-analysis efficiency.
```

Good expression:

```text
Pain hypothesis: The customer may have low ad-review efficiency.
Evidence: The customer shows boutique traits, and this type usually cares about ad ROI and keyword performance.
Validation question: Is ad review done daily, weekly, or after campaigns? Does ad data affect budget adjustment and Listing optimization?
```

## 8. Topic Prioritization

Because this skill supports pre-visit judgment, prioritize by business value and discovery usefulness, not by implementation resistance.

Scoring dimensions:

| Dimension | Meaning |
|---|---|
| Business value | Whether it affects revenue, profit, inventory, or labor efficiency |
| Pain visibility | Whether the customer can easily feel the pain |
| AI+RPA fit | Whether AI understanding plus RPA execution is suitable |
| Discovery expansion | Whether the topic can reveal more business information |

Priority layers:

| Priority | Meaning | Output Requirement |
|---|---|---|
| First priority | Must discuss in this visit; most likely to resonate | Give concrete opening questions |
| Second priority | Extend if the customer responds | Give follow-up direction |
| Third priority | Do not lead with it; only collect information | Explain why it is not a lead topic |

Sorting rules:

1. For brand-led customers, start with content, user feedback, social media, reviews, and influencers.
2. For boutique customers, start with key products, ad ROI, keywords, competitors, and inventory.
3. For refined-assortment customers, start with product selection, launches, SKU management, and batch content processing.
4. For mass-listing customers, start with listing, orders, logistics, finance, and support-process efficiency.
5. Larger, multi-department, multi-platform customers increase management-pain priority.
6. Categories with high inventory risk, price volatility, or return rates increase risk-pain priority.
7. In an initial visit, choose topics that are easy for the customer to recognize and can reveal details, not necessarily the most complex solution.

## 9. Exclusion Logic

The skill must also tell the CSM what not to lead with.

| Do Not Lead With | Reason | Better Entry |
|---|---|---|
| Standard inventory/order/ad reports already covered by ERP | Easily replaced by Lingxing, Jijia, Mabang, Dianxiaomi, or similar systems | Ask which manual organizing actions still happen outside the system |
| Stable high-volume data sync better handled by API | RPA differentiation is weak | Ask which long-tail systems or back offices lack APIs or are not worth API development |
| One-off low-frequency collection | Weak long-term value and renewal core | Ask whether there is periodic monitoring or anomaly alerting |
| AI judgment with unclear rules | Demo may look good but delivery risk is high | Ask whether criteria can be enumerated, reviewed, and accumulated |
| Pure dashboard demand | Value is weak without an action loop | Ask who acts after seeing an anomaly, how, and how fast |
| Scenarios over-dependent on business experts | Need discovery before solution commitment | Reframe as expert-rule extraction plus AI-assisted first-pass screening |
| Showy AI scenes | Can drift away from business value and reduce trust | Return to money logic, loss, efficiency, and risk |

AI+RPA is best suited for:

```text
cross-system + high-frequency + long-tail + repetitive manual work + scattered data + relatively stable rules + business-visible value + action loop
```

Be cautious with:

```text
low-frequency + single-system + already covered by ERP + strongly subjective judgment + no clear action loop + display-only output
```

## 10. Interview Question Rules

The output must include both "do not ask this way" and "ask this way".

Do not ask:

```text
What automation needs do you have?
Do you want RPA?
Do you want AI?
```

Ask around the customer's money logic, core metrics, and business losses so the customer naturally describes process, data, roles, frequency, pain, and decision chain.

General follow-up structure:

```text
Current state: Who does this now? Which systems, spreadsheets, or tools are used?
Frequency: How often is it done daily, weekly, or monthly? How long does each run take?
Judgment: How do you judge quality, anomalies, or priority?
Action: What action happens after the result is seen?
Loss: What happens if it is slow, wrong, or missed?
System boundary: What can ERP/platform/BI cover today, and what still relies on manual work?
```

Scenario question patterns:

### Competitors / Key Product Operations

Do not ask:

```text
Do you need competitor monitoring?
```

Ask:

```text
Who currently watches competitor price, inventory, rating, and ad-placement changes for your key products?
Do these changes affect pricing, ad budget, and replenishment actions?
Are you only looking at data, or has this become a fixed operating action?
```

### Keywords / Listing

Do not ask:

```text
Do you need AI to write Listings?
```

Ask:

```text
When a new product launches, where do keywords, selling points, titles, and bullet points come from?
How do you identify valid keywords, invalid keywords, and infringement-sensitive terms?
Is copy adapted from a batch template, or does each variant need separate writing?
Which content would you be most unwilling to hand fully to AI?
```

### Ad Review

Do not ask:

```text
Do you need ad analysis?
```

Ask:

```text
Is ad review done daily, weekly, or after major campaigns?
Do you mainly watch ACOS, CTR, and conversion rate, or combine them with keyword and competitor changes?
How does ad data affect budget adjustment, keyword optimization, and Listing optimization?
```

### Inventory / Replenishment

Do not ask:

```text
Do you need replenishment alerts?
```

Ask:

```text
Are stockouts, slow-moving inventory, or delayed FBA transfers the bigger concern today?
Can the system detect issues early, or do operations and supply-chain staff still watch manually?
Which inventory anomalies cause the biggest losses?
```

### Reviews / VOC / After-Sales

Do not ask:

```text
Do you need review analysis?
```

Ask:

```text
Do you regularly review negative reviews and return reasons?
Do these signals feed product improvement, Listing optimization, or customer-service scripts?
Is this currently manual, or do you have fixed tags and review mechanisms?
```

### Multi-Platform / Multi-Store Operations

Do not ask:

```text
Do you need multi-platform data aggregation?
```

Ask:

```text
Do teams look at each platform separately, or is data aggregated into one view?
Which systems do operators switch between most often when making decisions?
Which data already exists but still takes too much time to organize each time?
```

## 11. Anti-Rationalizations

Do not use these lazy reasons:

| Lazy Reason | Why It Is Not Allowed | Correct Behavior |
|---|---|---|
| "There are too few fields to analyze." | Early-visit information is naturally incomplete | Output low/medium/high-confidence hypotheses and validation questions |
| "Industry customers are all similar." | This becomes a generic industry report | Every judgment must cite fields or field combinations |
| "A few RPA scenarios would be more useful." | Solution before process validation misleads the visit | Output pain hypotheses and interview questions first |
| "The customer says it is brand-led, so it is brand-led." | Self-description may be aspiration, not operating fact | Validate with social media, influencers, repurchase, and content-asset signals |
| "AI+RPA can do all of it, so recommend all of it." | Feasible does not mean worth doing | Prioritize high-frequency, cross-system, long-tail, closed-loop directions |
| "More comprehensive output looks more professional." | CSMs need a battle card, not an encyclopedia | Keep Top 3 pains and 3-5 key links |
| "Start with product capabilities to look professional." | Initial visits are about proving business understanding | Start with money logic and business problems, then map capabilities |
| "Use industry knowledge to fill facts." | Customers notice when you do not understand them | Express industry knowledge as hypotheses to validate, not conclusions |

## 12. Red Flags

Rewrite the output if any of these appear:

1. No information-completeness or judgment-boundary statement.
2. No distinction between facts, inferences, and hypotheses.
3. Single forced customer type with no mixed ratio.
4. Scenario names without explaining why they matter to this customer.
5. Direct statements like "the customer's pain is..." instead of hypotheses.
6. Pain points without evidence and validation questions.
7. Questions still ask "Do you want RPA / AI / automation?"
8. Output reads like an industry report rather than a CSM battle card.
9. ERP/API-suitable scenarios are recommended without boundaries.
10. No guidance on what to discuss first and what to do if the customer responds or does not respond.
11. Empty phrases such as "improve efficiency", "reduce cost", or "empower business" without concrete business actions.
12. Overconfident conclusions when information is weak.

## 13. Required Output Format

Output strictly in this structure:

```markdown
# Customer Initial Judgment Battle Card

## 0. Executive Abstract
Write a 300-500 Chinese-character abstract if the final output is Chinese, or a 120-180 word abstract if the final output is English.

The abstract must be placed at the very beginning so a CSM can quickly grasp the report before reading the detailed card. It should summarize: likely customer archetype, money logic, the 1-2 most important pain hypotheses to validate first, the highest-value visit opening, one direction not to lead with, and the immediate next action. Keep it concrete and business-facing; do not introduce unsupported facts, do not list every section, and do not use empty phrases such as "improve efficiency" without specific business actions.

> Summary: This is the "too long; didn't read" version. It should let a busy reader understand the visit strategy first, then choose whether to read the details.

## 1. One-Sentence Initial Judgment
Use 1-2 sentences to state the customer's likely type, how it likely makes money, and where it may currently be stuck.

> Summary: This section should let the CSM understand the visit's main line within 30 seconds.

## 2. Information Completeness and Judgment Boundary
- Current information completeness: high / medium / low
- Known information:
- Key missing information:
- Judgment boundary:

> Summary: State what can be judged and what cannot be pretended.

## 3. Fact / Inference / Hypothesis Layering
| Type | Content |
|---|---|
| Confirmed facts |  |
| Reasonable inferences |  |
| Hypotheses to validate |  |

> Summary: Avoid treating industry experience as customer facts.

## 4. Mixed Customer Archetype
- Initial customer type: e.g. boutique 60% + brand transition 30% + refined assortment traits 10%
- Money logic:
- Sources of business complexity:
- Most likely operating metrics of concern:
- Evidence:
- Uncertainties:

> Summary: Do not label the customer; find the most useful discovery line.

## 5. Most Likely Complex Business Links
| Business link | Why it may be complex | Possible exposed problems |
|---|---|---|
| Link 1 | Explanation | Explanation |
| Link 2 | Explanation | Explanation |
| Link 3 | Explanation | Explanation |

> Summary: Keep only the 3-5 links most worth validating.

## 6. Top 3 Pain Hypotheses
| Priority | Pain hypothesis | Evidence | Possible business impact | AI+RPA fit | Confidence | Validation question |
|---|---|---|---|---|---|---|
| First priority |  |  |  |  | High/Medium/Low |  |
| Second priority |  |  |  |  | High/Medium/Low |  |
| Third priority |  |  |  |  | High/Medium/Low |  |

> Summary: The goal is not to prove a solution; it is to choose the business problems most worth getting the customer to discuss.

## 7. Priority Topics for This Visit
- Must discuss first:
- Can extend into:
- Do not lead with yet:

> Summary: Tell the CSM where to start instead of asking for needs broadly.

## 8. Questions That Make the Customer Feel Understood
### Topic 1:
- Do not ask:
- Ask this way:
- If the customer answers A, follow up:
- If the customer answers B, pivot to:

### Topic 2:
- Do not ask:
- Ask this way:
- If the customer answers A, follow up:
- If the customer answers B, pivot to:

> Summary: Questions must start from customer business actions, not product capabilities.

## 9. Directions Not Recommended as First Entry Points
| Direction | Why not recommended | Better entry |
|---|---|---|

> Summary: Exclude low-value or ERP/API-replaceable directions so the initial visit does not drift.

## 10. CSM Next Actions
- Goal of this conversation:
- Three key facts to validate:
- If the customer resonates, recommended next step:
- If the customer responds coldly, recommended next step:

> Summary: The output must translate into the next customer action, not stop at analysis.
```

## 14. Output Style

1. Be concise, like a CSM visit battle card, not a consulting report.
2. Add 1-2 sentence summaries under modules so structured information is easy to understand.
3. Start with the executive abstract. It must be readable on its own and must not merely repeat the table headings.
4. Do not pile up scenario names; explain why a scenario may matter.
5. Do not assert pain points directly. Use hypothesis + evidence + validation question.
6. Do not output too many low-value scenarios. Prioritize Top 3.
7. Use business language, not overly technical language.
8. Do not lead with product features. Start from the customer's money logic and business problems.
9. Avoid vague phrases such as "improve efficiency", "reduce cost", or "empower business" unless tied to concrete business actions.
10. Make the output executable for CSMs, with questions they can ask directly.
11. When information is insufficient, say "uncertain, needs validation" instead of pretending.
12. Do not over-explain the method in the final output; provide the battle card directly.
13. Do not ask again for information the user has clearly provided.

## 15. Verification

Before final output, self-check every item and revise first if any item fails:

1. Is information completeness stated clearly?
2. Is the judgment boundary stated?
3. Are confirmed facts, reasonable inferences, and hypotheses separated?
4. Is a mixed customer archetype used instead of a forced single type?
5. Is the customer's money logic summarized in one sentence?
6. Are only the most relevant 3-5 business links output?
7. Are Top 3 pain hypotheses output instead of a broad scenario list?
8. Does every pain include evidence?
9. Does every pain include possible business impact?
10. Does every pain include AI+RPA fit?
11. Does every pain include confidence?
12. Does every pain include validation questions?
13. Are "do not ask / ask this way" questions included?
14. Are directions not recommended as first entry points included?
15. Are CSM next actions included?
16. Are vague phrases avoided unless tied to concrete business actions?
17. Is industry common sense kept as hypothesis rather than customer fact?
18. Is there an executive abstract at the very beginning, with 300-500 Chinese characters or 120-180 English words depending on output language?
19. Does the abstract summarize the visit strategy rather than merely listing section titles?

A qualified output must:

1. Let the CSM understand the initial judgment within 3 minutes.
2. Give the CSM 3-5 questions they can directly ask.
3. Make the customer feel the questions relate to their business.
4. Help the CSM decide what to discuss first and what not to discuss first.
5. Avoid pretending certainty and avoid stopping because information is incomplete.

## 16. Example Input

```text
Customer name: An apparel cross-border seller
Customer model: boutique, possibly moving toward brand-led
Category: apparel
Product type: athleisure clothing
Supply model: R&D-manufacturing-sales integrated
Sales platform: Amazon US
Team size: around 50 people
SKU volume / launch frequency: many variants, relatively frequent launches
ERP / system status: unclear
Business stage: refined operations, pursuing hit-product rate
Known context: has an operations team and values keywords, Listing, and ad performance
```

## 17. Example Output Fragment

```markdown
# Customer Initial Judgment Battle Card

## 0. Executive Abstract
This customer looks most likely like a boutique-led apparel seller with some brand-transition intent, rather than a pure process-efficiency customer. Its growth probably depends on turning a small set of key products into stronger winners through keywords, Listing quality, ad review, inventory judgment, and feedback loops. For the visit, the CSM should first validate whether keyword/Listing work and ad-review decisions are still handled manually or scattered across systems, because these topics are easy for operations teams to recognize and can reveal roles, frequency, data sources, and decision actions. Do not lead with generic automation, pure dashboards, or ERP-replaceable standard reports. The immediate goal is to ask how key-product operating actions are done today, then decide whether there is a repeatable AI+RPA entry point.

> Summary: Read this first to understand the visit line before entering the detailed evidence.

## 1. One-Sentence Initial Judgment
This customer is likely boutique-led with a secondary brand-transition tendency. The core issue may not be simple process efficiency, but more refined keyword, content, ad, and inventory operations around key products.

> Summary: This visit should start from "how key products are operated into winners", not from automation needs.

## 2. Information Completeness and Judgment Boundary
- Current information completeness: medium
- Known information: apparel category, Amazon US, R&D-manufacturing-sales integrated, around 50 people, many variants, pursuing hit-product rate.
- Key missing information: SKU count, launch frequency, monthly ad spend, ERP system, influencer/social activity, return-rate data.
- Judgment boundary: We can initially judge boutique-operation and content/keyword pressure, but cannot confirm a full brand-operation stage yet.

> Summary: We can judge what to discuss first, but cannot jump directly to a solution.

## 3. Fact / Inference / Hypothesis Layering
| Type | Content |
|---|---|
| Confirmed facts | Apparel category, Amazon US, integrated supply model, around 50 people, many variants, pursuing hit-product rate |
| Reasonable inferences | Apparel variants plus boutique operations suggest Listing, keyword, ad, and inventory linkage is likely important |
| Hypotheses to validate | Keyword and Listing workload, ad-review efficiency, and return/negative-review feedback loops may be priority validation topics |

> Summary: These are not final conclusions; they are validation directions for the next visit.

## 4. Mixed Customer Archetype
- Initial customer type: boutique 60% + brand transition 25% + refined assortment traits 15%
- Money logic: Improve hit-product rate and single-product profit through refined key-product operations.
- Sources of business complexity: many apparel variants, heavy keyword/copy workload, and the need to link ads and inventory around key products.
- Most likely operating metrics of concern: conversion rate, ad ROI, return rate, inventory turnover, launch efficiency.
- Evidence: The customer is boutique-oriented in apparel, pursues hit-product rate, and apparel naturally carries variant, keyword, content, and return-analysis pressure.
- Uncertainties: Whether there is a dedicated brand-content team, influencer/social operation, and mature data-review mechanism.

> Summary: The most resonant line is not "saving labor", but whether key-product operations can be faster, more accurate, and more closed-loop.
```

## 18. Maintainer Notes

Future iterations can add:

1. Platform-specific rules for Amazon, TikTok Shop, Temu, independent sites, Ozon, and other platforms.
2. Category-specific pain maps for apparel, 3C, small appliances, pet, outdoor, and home.
3. Role-specific interview questions for owners, IT, operations leads, supply chain, and finance.
4. Stage-specific entry strategies for new onboarding, dormant-customer activation, and pre-renewal demand rebuilding.
5. Handoff rules with the RPA asset diagnosis skill.
