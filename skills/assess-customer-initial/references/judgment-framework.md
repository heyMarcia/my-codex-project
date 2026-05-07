# Customer Initial Judgment Framework

Use this reference to produce a CSM pre-visit battle card for cross-border ecommerce customers without mature RPA/AI+RPA assets.

## Input Completeness

Start every analysis with:

```text
当前信息完整度：高 / 中 / 低
当前可判断的信息：
当前缺失但关键的信息：
本次分析的可信边界：
```

Completeness levels:

| Level | Criteria | Output expectation |
|---|---|---|
| 高 | Customer model, category, product type, platform, supply model, team size, SKU/launch frequency, and system status are mostly complete | Produce a clearer profile and Top 3 pain hypotheses |
| 中 | Customer model, category, platform, and supply model exist, but team size, SKU, or system status is missing | Produce an initial profile with key validation questions |
| 低 | Only customer name, category, or vague background exists | Produce directional hypotheses only and avoid over-certainty |

## Customer Models

Use `primary type + auxiliary type + transition direction`. Do not rely only on the customer's self-description.

| Type | Money-making logic | Typical concerns | High-value AI+RPA directions |
|---|---|---|---|
| 品牌型 | Brand premium, user mindshare, content assets, repurchase, reputation | Brand image, content quality, social media, influencers, reviews, VOC, user feedback | AI content generation, VOC/review analysis, social content review, sentiment monitoring, influencer content archive |
| 精品型 | Maximize profit from a small number of key products | Hero-product growth, ad ROI, price competition, competitor dynamics, inventory turnover, keywords | Competitor price/inventory/listing monitoring, ad review, keyword analysis, replenishment alerts, key-product dashboards |
| 精铺型 | Test, filter, and scale many SKUs quickly | Selection efficiency, launch speed, SKU management, batch product data, batch content | Batch collection, product data cleaning, AI Listing generation, keyword batch processing, listing assistance, SKU reports |
| 铺货型 | Scaled labor efficiency and stable processes | Listing efficiency, orders, logistics, finance reconciliation, customer service, inventory sync | Listing automation, order/logistics/inventory sync, finance reconciliation, service ticket handling, multi-platform data aggregation |

Judgment reminders:

- A claimed brand customer without social, content, repurchase, or user operations may be `精品型 + 品牌化意愿`.
- Many SKUs, fast launches, and multi-platform operations increase `精铺型` or `铺货型` weight even when the customer has its own brand.
- Heavy focus on key products, ads, competitors, and inventory increases `精品型` weight.
- Desire to sell more without adding people often signals refined assortment or mass-listing efficiency pressure.

Required mixed-profile format:

```text
初判客户类型：精品型 60% + 品牌化转型 30% + 精铺特征 10%
判断依据：
- ...
不确定点：
- ...
待验证问题：
- ...
```

## Money-Making Logic

After the profile, summarize:

```text
赚钱逻辑一句话：这个客户大概率主要靠 [赚钱方式] 获得增长，因此最可能关注 [核心指标 / 经营问题]。
```

Common mappings:

| Type | Money-making logic | Likely concerns |
|---|---|---|
| 品牌型 | Brand premium, user mindshare, content assets, repurchase | Content quality, reputation, user feedback, social media, review analysis |
| 精品型 | Maximize profit from key products | Hero-product growth, ad ROI, competitor dynamics, inventory turnover, price competition |
| 精铺型 | Fast SKU testing and selection | Selection efficiency, launch efficiency, batch Listing, product data |
| 铺货型 | Process scale and labor efficiency | Listing, orders, logistics, customer service, finance, inventory sync |

## Business-Link Mapping

Consider these 8 links, but output only the most relevant 3-5:

1. 选品 / 市场调研
2. 商品上架 / Listing / 内容生产
3. 广告 / 流量 / 关键词
4. 竞品 / 价格 / 排名监控
5. 订单 / 履约 / 物流
6. 库存 / 补货 / 调拨
7. 客服 / 评论 / 售后 / VOC
8. 财务 / 对账 / 经营报表

Signal mappings:

| Signal | Possible pain |
|---|---|
| 精品型 + key products + Amazon | Ad ROI, competitor price, keywords, reviews, inventory turnover |
| 精铺型 + many SKUs + multi-platform | Launch efficiency, product data processing, batch Listing, price sync, SKU management |
| 品牌型 + social/independent site/influencers | Content production, user feedback, sentiment, influencer collaboration, asset archive |
| Trading + many suppliers | Supply price comparison, cost calculation, procurement collaboration, delivery tracking |
| R&D/manufacturing/sales integrated or own factory | New product research, feedback loop, production plan, quality issue closure |
| Multi-platform | Cross-platform data aggregation, order/inventory/price/content coordination |
| Apparel or multi-variant category | Keyword collection, batch Listing generation, variant management, return reason analysis |
| 3C/small appliances | Competitor updates, price changes, negative review analysis, quality feedback, compliance risk |
| Home/furniture/bulky goods | Logistics cost, inventory turnover, FBA fees, slow-moving risk |
| Pet/outdoor/consumer goods | User feedback, content seeding, influencer marketing, review analysis |

Output:

```text
最可能存在复杂度的业务链路：
1. 链路 A：为什么可能复杂
2. 链路 B：为什么可能复杂
3. 链路 C：为什么可能复杂
```

## Pain Hypotheses

Use four pain categories:

| Category | Core issue | Typical directions |
|---|---|---|
| 增长型痛点 | Sell more, sell better, improve profit | Keywords, Listing optimization, ad review, competitor monitoring, review analysis, influencer screening, new opportunity discovery |
| 提效型痛点 | Repetitive work, large processing volume | Batch listing, product data, report downloads, orders, logistics, finance reconciliation, service tickets |
| 风险型痛点 | Problems are found after loss happens | Stockout/slow-moving alerts, bad review monitoring, price anomaly monitoring, infringement word checks, billing anomalies |
| 管理型痛点 | Boss cannot see clearly, teams are uncoordinated, data is scattered | Operating weekly report, department data aggregation, anomaly reminders, auto review summaries, demand pool, dashboards with action closure |

Each hypothesis must contain:

```text
痛点假设：
判断依据：
可能业务影响：
AI+RPA 适配方向：
可信度：高 / 中 / 低
待验证问题：
```

Correct style:

```text
痛点假设：客户可能存在广告复盘效率低的问题。
判断依据：客户具备精品型特征，且该类型通常高度关注广告 ROI 和关键词表现。
待验证问题：你们广告复盘是日维度、周维度还是大促后做？广告数据最后会不会影响预算调整和 Listing 优化？
```

## Visit Topic Priority

Rank candidate topics by:

| Dimension | Meaning |
|---|---|
| 业务价值 | Whether it affects revenue, profit, inventory, or labor efficiency |
| 问题显性度 | Whether the customer can easily feel the pain |
| AI+RPA 适配度 | Whether AI understanding plus RPA execution fits |
| 访谈延展性 | Whether the topic can reveal more business details |

Priority rules:

- 品牌型: content, user feedback, social media, reviews, influencers.
- 精品型: key products, ad ROI, keywords, competitors, inventory.
- 精铺型: selection, launch, SKU management, batch content processing.
- 铺货型: listing, orders, logistics, finance, customer service.
- Larger teams, many departments, or multi-platform operations increase management-pain priority.
- Inventory-sensitive, price-volatile, or high-return categories increase risk-pain priority.
- In first visits, prefer topics customers can feel and discuss concretely.

## Exclusion Logic

Tell the CSM what not to lead with.

| Direction | Reason |
|---|---|
| Standard ERP-covered inventory/order/ad reports | Easily replaced by Lingxing, Jijia, Mabang, Dianxiaomi, etc. |
| Stable high-volume data sync better served by APIs | RPA differentiation is weak |
| One-time low-frequency scraping | Weak long-term value and renewal logic |
| AI judgment with unclear rules | Easy demo, hard delivery |
| Pure dashboards | Weak value without action closure |
| Scenarios over-dependent on expert judgment | Must be clarified before promising a solution |
| Flashy AI scenarios customers do not care about | Distracts from business value and reduces trust |

Good AI+RPA fit:

```text
跨系统 + 高频 + 长尾 + 人工重复 + 数据分散 + 规则相对稳定 + 客户有业务感知
```

Weak or risky fit:

```text
低频 + 单系统 + 已被 ERP 覆盖 + 强依赖人脑主观判断 + 没有明确动作闭环
```

## Discovery Question Style

Always include "不要这样问" and "应该这样问".

General rule:

- Do not ask: `你们有什么自动化需求？` / `你们要不要做 RPA？` / `你们要不要用 AI？`
- Ask around the customer's money-making logic, core metrics, business losses, process, data, roles, frequency, pain, and decision chain.

Topic examples:

### Competitors / Key Products

Do not ask:

```text
你们要不要竞品监控？
```

Ask:

```text
你们现在重点产品的竞品价格、库存、评分、广告位变化，是谁在盯？
这些变化最后会不会影响调价、广告预算和补货动作？
现在是只看数据，还是已经形成固定经营动作？
```

### Keywords / Listing

Do not ask:

```text
你们要不要 AI 写 Listing？
```

Ask:

```text
你们新品上架时，关键词、卖点、标题、五点描述是怎么来的？
有效词、无效词、侵权词是怎么判断的？
文案是一套模板批量改，还是每个变体都要单独写？
哪些内容最不敢完全交给 AI？
```

### Ad Review

Do not ask:

```text
你们要不要广告分析？
```

Ask:

```text
你们广告复盘是日维度、周维度，还是大促后做？
现在主要看 ACOS、CTR、转化率，还是会结合关键词和竞品变化？
广告数据最后会怎么影响预算调整、关键词优化和 Listing 优化？
```

### Inventory / Replenishment

Do not ask:

```text
你们要不要补货预警？
```

Ask:

```text
你们现在最怕的是断货、滞销，还是 FBA 调拨不及时？
系统能不能提前发现，还是主要靠运营 / 供应链人工盯？
哪些库存异常发生时，损失最大？
```

### Reviews / VOC / After-Sales

Do not ask:

```text
你们要不要评论分析？
```

Ask:

```text
你们现在会定期看差评和退货原因吗？
这些反馈会不会进入产品改良、Listing 优化或客服话术调整？
现在是人工看，还是有固定的标签和复盘机制？
```

### Multi-Platform Operations

Do not ask:

```text
你们要不要多平台数据汇总？
```

Ask:

```text
你们现在不同平台的数据是各看各的，还是会统一汇总？
运营做决策时，最常切换哪些系统？
哪些数据明明有，但每次整理都很耗时间？
```

## Required Output Template

```markdown
# 客户初判作战卡

## 1. 一句话初判
用 1-2 句话说明客户大概率是什么类型，靠什么赚钱，当前最可能卡在哪里。

## 2. 信息完整度与判断边界
- 当前信息完整度：高 / 中 / 低
- 已知信息：
- 关键缺失信息：
- 本次判断边界：

## 3. 混合型客户画像
- 初判客户类型：如 精品型 60% + 品牌化转型 30% + 精铺特征 10%
- 赚钱逻辑：
- 业务复杂度来源：
- 当前最可能关注的经营指标：
- 判断依据：
- 不确定点：

## 4. 最可能复杂的业务链路
| 业务链路 | 为什么可能复杂 | 可能暴露的问题 |
|---|---|---|
| 链路 1 | 说明 | 说明 |
| 链路 2 | 说明 | 说明 |
| 链路 3 | 说明 | 说明 |

## 5. Top 3 痛点假设
| 优先级 | 痛点假设 | 判断依据 | 可能业务影响 | AI+RPA 适配方向 | 可信度 | 待验证问题 |
|---|---|---|---|---|---|---|
| 第一优先级 |  |  |  |  | 高/中/低 |  |
| 第二优先级 |  |  |  |  | 高/中/低 |  |
| 第三优先级 |  |  |  |  | 高/中/低 |  |

## 6. 本次拜访优先话题
- 必须先聊：
- 可以延展聊：
- 暂时不主推：

## 7. 让客户觉得“你懂我”的问法
### 话题 1：
- 不要这样问：
- 应该这样问：
- 如果客户回答 A，继续追问：
- 如果客户回答 B，转向追问：

### 话题 2：
- 不要这样问：
- 应该这样问：
- 如果客户回答 A，继续追问：
- 如果客户回答 B，转向追问：

## 8. 不建议优先切入的方向
| 方向 | 不建议原因 | 替代切入方式 |
|---|---|---|

## 9. CSM 下一步动作
- 本次沟通目标：
- 需要验证的 3 个关键信息：
- 如果客户有共鸣，下一步建议：
- 如果客户反应冷淡，下一步建议：
```
