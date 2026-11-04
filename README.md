
# 🏥 Health Claims Analytics | Power BI Dashboard

> An interactive Power BI dashboard that analyzes healthcare claims from 2022 to 2024: how much is billed versus paid, which claim types, diagnoses and procedures drive cost, where payments fall short, and what the business can do about it.

---
# 🎯 Business Problem

Healthcare costs are rising, and a large share of billed charges is never paid. Claims analysts and finance leaders need to know:

- How much is being billed versus paid, and how is that changing year over year?
- Which claim types, diagnoses and procedures drive most of the cost?
- Where do payments fall short, and which gaps matter most in dollars?
- What actions can control cost growth and improve claims accuracy?

---
# 🛠 Tools & Skills
- Power BI Desktop for data modeling and dashboard design
- DAX for measures (totals, weighted paid ratio, year-over-year trends)
- Data modeling
- Skills demonstrated: KPI design, cost-driver analysis, segmentation, data storytelling, business recommendations

---
## 📊 Dashboard Overview

| KPI | Value |
|---|---|
| Total Claims | 449 |
| Total Billed | $2.06M (+19.39% vs. prior year) |
| Total Paid | $1.55M (+20.01% vs. prior year) |
| **Paid Ratio (weighted)** | **75.20%** (+0.52 pts vs. prior year) |
| Avg Paid Ratio (per claim) | 0.83 |
| Unpaid Billed Charges | ~$511K (24.8% of billed) |

---
## 🔍 Key Insights

### 1. About a quarter of billed charges goes unpaid, mostly on larger claims
The portfolio holds 449 claims averaging about $4,593 billed and $3,454 paid. The weighted paid ratio is **75.2%**, leaving **~$511K (24.8%)** of billed charges unpaid. The per-claim average ratio (0.83) is higher than the weighted ratio, which means **larger claims are paid at lower rates than small ones**.

### 2. Spending is driven by claim severity, not claim volume
Claim volume is spread evenly across types (17-23% each), but spend is not.

| Claim type | Claims | Share of claims | Paid | Share of paid | Paid per claim |
|---|---|---|---|---|---|
| Inpatient | 99 | 22% | $1.09M | **70.45%** | ~$11.0K |
| Emergency | 88 | 20% | $0.29M | 18.99% | ~$3.3K |
| Outpatient | 105 | 23% | $0.13M | 8.32% | ~$1.2K |
| Pharmacy | 81 | 18% | ~$11K | <1% | ~$140 |
| Lab | 76 | 17% | ~$23K | ~1.5% | ~$300 |

Inpatient claims are a fifth of volume but **70% of paid dollars**, at about **3x** the portfolio average cost per claim. Outpatient has the most claims (105) but only 8% of spend.

### 3. A handful of codes drive most of the cost
- The top 10 **ICD (diagnosis) codes** account for about **60%** of paid amount (~$936K). Essential hypertension (**I10**) leads at **$259.6K (~17%)**, and the top 3 diagnoses make up ~36%.
- The top 10 **CPT (procedure) codes** account for about **62%** (~$956K). CPT **67890** leads at **$242.7K (~16%)**, and the **top 4 codes alone make up 44%**.
- Chronic conditions such as hypertension appear at the top of the diagnosis list, so ongoing condition management is a visible cost lever.

### 4. The lowest paid ratio is not the biggest loss
In the provider detail table, one pharmacy claim (PRV00214) was paid **0%** on $210 billed, a likely full denial. But ranked by unpaid dollars, the largest gaps are high-value inpatient claims:

| Provider | Claim type | Billed | Paid | Ratio | **Unpaid** |
|---|---|---|---|---|---|
| PRV00002 (CPT 00123) | Inpatient | $29,500 | $18,500 | 62.71% | **$11,000** |
| PRV08910 (CPT 27650) | Inpatient | $12,850 | $5,120 | 39.84% | **$7,730** |
| PRV00003 (CPT 99285) | Emergency | $7,600 | $4,200 | 55.26% | $3,400 |
| PRV04567 (CPT 93000) | Emergency | $4,200 | $1,260 | 30.00% | $2,940 |
| PRV00214 (CPT 54321) | Pharmacy | $210 | $0 | 0.00% | $210 |

Two inpatient claims account for about **$18.7K** of unpaid charges, roughly 90x the pharmacy denial. Prioritizing review by **unpaid dollars rather than paid ratio** targets the biggest opportunities first. Some claims are also paid at exactly **100%** of billed, which is unusual because paid amounts are normally below billed after contractual adjustments, and is worth auditing.

### 5. Costs are growing about 20% a year, with only a marginal improvement in payment
Year over year, billed amounts grew **19.39%** and paid amounts **20.01%**, while the paid ratio improved only **0.52 points**. Cost growth, not payment accuracy, is the bigger pressure on the portfolio. Monthly volume is strongest in the first half of the year and drops sharply in months 11-12. _Confirm whether late-year data is complete before treating this as a real seasonal decline._

---

## 💡 Strategic Recommendations

| # | Problem | Recommendation | Target KPI |
|---|---|---|---|
| 1 | Inpatient claims are 22% of volume but 70% of paid cost | Introduce pre-authorization and utilization review for high-cost admissions, audit claims above a dollar threshold (e.g. $10K), and negotiate case-rate or bundled pricing with high-volume facilities | Inpatient paid per claim, inpatient paid ratio |
| 2 | Largest unpaid gaps sit on a few high-value claims | Create a priority worklist ranked by **unpaid amount** and review the largest gaps first, separating discounts, patient share and denials | Unpaid $ reviewed, $ recovered or validated |
| 3 | Full denials (paid = 0) such as PRV00214 | Capture a denial reason code, track denial rate by provider and procedure, and fix root causes (authorization, coding, duplicates) through provider education and front-end claim edits | Denial rate, % of claims with paid = 0 |
| 4 | 10 diagnosis codes drive ~60% of spend, led by hypertension | Launch chronic-condition management (care coordination, medication adherence, preventive visits) for members with repeat hypertension and diabetes claims | Cost per member for chronic diagnoses |
| 5 | Top 4 CPT codes drive 44% of paid cost | Review pricing, medical necessity and bundling rules for the top procedure codes, and benchmark against the fee schedule | Paid per claim for top 4 CPT codes |
| 6 | Claims paid at exactly 100% of billed | Audit these claims for fee-schedule enforcement and possible overpayment | % of claims paid at 100%, overpayments recovered |
| 7 | Costs growing ~20% a year | Add monthly monitoring of billed, paid, unpaid and denial rate with alerts for providers or codes that deviate from trend | Year-over-year paid growth |

**Illustrative impact (not a forecast):**
- A **5% reduction in inpatient paid cost** would save about **$54K** (5% of $1.09M).
- If paid growth of ~20% continues, annual paid cost would rise to about **$1.86M**, roughly **$310K** more.
- Each **1-point** change in the weighted paid ratio equals about **$20.6K** on the current billed volume.

**Priority:** start with recommendations 2, 3 and 7 (low effort, immediate visibility), then 1 and 5 (high impact, more effort), followed by 4 and 6.

⭐ If you found this project useful, please star the repo!
---
