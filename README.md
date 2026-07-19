# E-Commerce-Marketing-ROI-Dashboard-Power-BI
An end-to-end marketing analytics project: cleaning messy, multi-channel ad campaign data and building an interactive Power BI dashboard to identify which channels and campaigns actually deliver return on ad spend.

Note: This project uses simulated data designed to mimic real-world data quality issues (mixed date formats, duplicates, missing values, inconsistent text formatting) commonly found in marketing platform exports.


Business Problem

An e-commerce business runs paid campaigns across Meta Ads, Google Ads, and Email, but has no consolidated way to see which channels and campaigns are actually profitable. Ad spend is tracked separately per platform, with no unified view of:


Which channel delivers the best return on spend
Which individual campaigns are worth scaling vs. cutting
How revenue trends month over month


What I Did

1. Data Cleaning (Excel)

Started with 298 raw campaign performance records containing realistic data quality issues:

Issue: Mixed date formats (4 variants, including ambiguous day/month cases)
How I Handled It: Standardized all dates; manually resolved ambiguous cases using the known valid date range as a validation check17 duplicate campaign recordsIdentified and removed using CampaignID as the unique keyMissing Spend, Clicks, Conversions, and Revenue valuesFilled using the average value per Channel + Campaign combination, not a flat global averageInconsistent Channel text formatting (EMAIL, " Email ", hidden non-breaking spaces)Standardized using PROPER/TRIM plus a SUBSTITUTE step to catch non-printable whitespace charactersZero-conversion edge casesGuarded ROAS/CAC formulas to return 0 instead of a division error

Result: 298 → 281 clean, deduplicated records.

2. Metric Calculation

Derived two core performance metrics not present in the raw data:


ROAS (Return on Ad Spend) = Revenue ÷ Spend
CAC (Customer Acquisition Cost) = Spend ÷ Conversions


Used blended ROAS (Sum of Revenue ÷ Sum of Spend) at the channel and campaign level rather than a simple average of per-row ROAS, to avoid distortion from outlier campaigns.

3. Power BI Dashboard

Built a 3-page interactive report:


Overview — KPI summary cards, monthly revenue trend, key insights panel, channel slicer
Channel Deep-Dive — Revenue and blended ROAS by channel
Campaign Performance — Revenue and blended ROAS by individual campaign, ranked


Key Insights


Email is the most efficient channel, returning $5.89 per $1 spent — nearly 4x more efficient than Meta Ads ($1.57). Recommend reallocating budget from Meta Ads toward Email.
April was the peak month (~$55K revenue), followed by a sharp ~50% drop in May (~$27K) — worth investigating the cause to avoid repeating the dip.
Promo Blast is the highest-ROI campaign (9.62x) despite a modest budget, while Retargeting and Brand Awareness rank lowest on both revenue and ROI — strong candidates to pause or restructure. Notably, the highest-revenue campaign (Welcome Series) is not the most efficient one, highlighting why both metrics matter.
