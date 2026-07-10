# 📊 Meta Ad Performance Dashboard – Power BI Project

An interactive **Power BI dashboard** that analyzes paid advertising performance on **Facebook and Instagram** — covering reach, engagement, conversions, and budget utilization. Built to help a marketing team identify the best-performing platform, audience, ad format, and timing for future campaigns.

This project simulates a real-world business analytics workflow: starting from a Business Requirements Document, through data modeling, to a fully interactive Power BI dashboard with actionable insights.

---

## 🗂️ Dataset

The project uses the **Meta Ads Performance Dataset**, a set of related tables modeled after how Facebook/Instagram (Meta) ad platforms capture campaign, ad, user, and event-level data.

📥 **Dataset link:** https://github.com/Priya-DharshiniRamesh/meta-ad-performance-dashboard/tree/main/datasets

### Tables & Schema

| Table | Description | Key Columns |
|---|---|---|
| `ad_events` | **Fact table** — every user–ad interaction event | event_id, ad_id, user_id, timestamp, day_of_week, time_of_day, event_type (Impression, Click, Share, Comment, Purchase) |
| `ads` | Ad creative metadata and targeting | ad_id, campaign_id, ad_platform, ad_type, target_gender, target_age_group, target_interests |
| `campaigns` | Campaign-level budget and timeframe | campaign_id, name, start_date, end_date, duration_days, total_budget |
| `users` | User demographics and interests | user_id, user_gender, user_age, age_group, country, location, interests |

**Data Model:** Star schema — `ad_events` (fact) joins to `ads`, `campaigns`, and `users` (dimensions).

```
ad_events → ads       (ad_id)       → platform, ad type, targeting details
ads       → campaigns (campaign_id) → budget, duration
ad_events → users      (user_id)     → demographics, geography
```

**Coverage:**
- **Platforms:** Facebook, Instagram *(Messenger and Audience Network are out of scope)*
- **Ad Types:** Image, Video, Carousel, Story
- **Event Types:** Impression, Click, Share, Comment, Purchase
- **Audience:** Gender, age group, country, location, interests
- **Engagement type:** Paid ads only *(organic engagement is out of scope)*

---

## 📈 Dashboard Overview

The `.pbix` file contains a KPI summary view plus **7 core visuals**, all driven by a single dynamic metric-selector parameter (switch between Impressions, Clicks, Engagements, Purchases, etc. across the whole report):

| Visual | Type | What it Shows |
|---|---|---|
| **Target Gender** | Donut chart | Which gender segment drives the selected metric |
| **Target Age Group** | Bar chart | Which age group is most responsive to campaigns |
| **Country** | Map | Geographic view of campaign reach and engagement |
| **Calendar Month** | Calendar Heatmap | Seasonal trends, peak ad months/days |
| **Weekly Trend** | Stacked column (by ad type) | Ad-type contribution to performance over weeks |
| **Hourly Trend** | Area chart | User activity patterns by hour of day (0–23) |
| **Ad Type** | Matrix | Metric comparison across ad type × platform |

### Key Metrics (Measures) Used
- Impressions / Clicks / Shares / Comments / Purchases
- Engagements (Clicks + Shares + Comments)
- CTR – Click Through Rate: (Clicks ÷ Impressions) × 100
- Engagement Rate: (Engagements ÷ Impressions) × 100
- Conversion Rate: (Purchases ÷ Clicks) × 100
- Purchase Rate: (Purchases ÷ Impressions) × 100
- Total Budget / Avg. Budget per Campaign

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** – data modeling, DAX measures, and dashboard visuals
- **DAX (Data Analysis Expressions)** – calculated KPIs, measures, and dynamic metric parameters
- **Star schema modeling** – 1 fact table (`ad_events`) + 3 dimension tables (`ads`, `campaigns`, `users`)

---

## 🚀 How to Use

1. Clone or download this repository.
   ```Bash
   https://github.com/Priya-DharshiniRamesh/meta-ad-performance-dashboard.git
   ```
2. Open `Meta_Ad_Performance_Dashboard.pbix` in **Power BI Desktop** free download from [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/).
3. Use the **metric-selector parameter** at the top of the report to switch the KPI shown across all visuals (Impressions, Clicks, Engagements, Purchases, etc.).
4. Use the slicers to filter by platform, ad type, country, gender, age group, or date range.

> If the data source path breaks after downloading, go to **Home → Transform Data → Data Source Settings** in Power BI and repoint it to your local copy of the dataset.

---

## 📁 Repository Structure

```
meta-ad-performance-dashboard
│
├── datasets/
│   ├── ad_events.csv
│   ├── ads.csv
│   ├── campaigns.csv
│   └── users.csv
│
├── images/
│   └── dashboard.png
│
├── Meta_Ad_Performance_Dashboard.pbix
│
├── README.md
│
└── (Optional - add these)
    ├── Business_Requirements_Document.pdf
    └── Domain_Knowledge_Document.pdf
```

---

## 🔍 Key Insights

- **Strong top-of-funnel, weak bottom-of-funnel:** CTR (11.76%) and Engagement Rate (13.56%) are well above industry benchmarks, but Purchase Rate is only 0.61% out of 216K impressions — a classic case of strong awareness/interest but weak action (purchase).
- **Best audience:** Females aged 18–30 (especially early 20s) drive the most engagement; engagement drops sharply after 35+.
- **Best geographies:** US, India, Brazil, Germany, and UK are the top engaged countries — India & US show high volume/high engagement potential, while Germany/UK show stronger conversion potential due to higher purchasing power.
- **Best ad format:** Video ads lead on CTR, Conversion Rate, and Engagement Rate, followed closely by Stories; Image and Carousel formats convert slightly less well.
- **Best timing:** Engagement peaks in the afternoon/evening (~15:00–20:00) and is lowest overnight (~0:00–5:00); weekly engagement stays fairly consistent with spikes around specific promotional dates (e.g. 19th–21st, 25th–27th).

### Recommendations
1. Improve landing pages, offers, and retargeting campaigns to close the purchase-funnel gap.
2. Prioritize targeting females aged 18–30, especially in India and Brazil.
3. Shift more budget toward Video and Story ad formats.
4. Schedule ad delivery for afternoon and evening slots.
5. Reallocate budget toward the highest-performing geographies and ad formats.
   
---

## 👤 Author

**Priya Dharshini R**\
📧 srpriyadharshini16@gmail.com

---

## 📄 License

This project is open-sourced for learning and portfolio purposes. Feel free to explore, fork, and adapt it.
