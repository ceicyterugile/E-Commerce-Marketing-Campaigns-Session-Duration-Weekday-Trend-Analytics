# E-Commerce Marketing Campaigns: Session Duration & Weekday Trend Analytics

## 📌 Project Overview & Strategic Business Goal
The primary objective of this project is to model user web traffic and evaluate cross-campaign performance trends on an enterprise e-commerce platform. Specifically, this analysis investigates whether user engagement (measured via session duration on-site) fluctuates across different weekdays, and isolates how this behavior shifts across distinct marketing campaigns.

The ultimate goal is to translate raw clickstream events into a structured presentation that equips marketing managers with data-backed insights to optimize budget allocation, campaign scheduling, and user retention.

## 📋 Data Infrastructure & Structural Constraints
- **Data Source:** BigQuery Workspace (`turing_college.raw_events` table).
- **Core Challenge (Session Modeling):** The raw dataset lacks pre-defined session identifiers. Because single users visit the platform across multiple days, calculating a flat on-site time creates skewed metrics. 
- **Analytical Solution:** Implemented a logical session-reconstruction model using custom time-threshold constraints (e.g., partitioning user event sequences by date and calculating elapsed intervals between the first and terminal event timestamps within a single day boundary).

## 🛠️ Requirements & Technical Pipeline

### 1. Advanced SQL Engineering (BigQuery Architecture)
* **Feature Extraction:** Identified and isolated relevant campaign tags, user identifiers, and timestamp metrics.
* **Date Functions:** Extracted days of the week (`EXTRACT(DAYOFWEEK FROM timestamp)`) to facilitate granular weekday aggregations.
* **Time Conversion Logic:** Programmatically converted raw Unix/timestamp differences into seconds and transformed them into standard, human-readable hours and minutes (`TIMESTAMP_DIFF`, `SEC_TO_TIME` or mathematical hour/minute reductions).
* **Code Optimization:** Applied Common Table Expressions (CTEs) and Window Functions to maintain readability and execution performance.

### 2. Analytical Data Visualization
* Structured a clear, interactive visual presentation utilizing professional analytics dashboards (**Tableau / Looker Studio / Google Sheets**).
* Built cross-tabulations and comparative trend lines mapping average session durations across weekdays, broken down by individual campaigns (e.g., isolating performance variations like the *Black_Friday_V1* campaign).

## 📊 Strategic Business & Operational Insights

The exploratory phase of this project focuses on dissecting user behavior under two distinct interpretive lenses:
- **The Engagement Paradox:** Evaluating why prolonged session durations can indicate excellent user interest (deep browsing, product discovery) or dangerous platform friction (poor UI, navigation confusion, checkout bottlenecks).
- **Campaign Optimization:** Pinpointing exact operational milestones—such as identifying which specific marketing campaign captures the highest average session duration on target weekdays like Thursdays and Fridays.

## ⚠️ Analytical Drawbacks & Strategic Recommendations
- **Identified Limitations:** Without explicit session cookies or inactivity timeouts (e.g., a standard 30-minute expiration window), calculations run the risk of overestimating durations for users who leave tabs open in the background.
- **Future Enhancements:** 
  1. Implement a true 30-minute inactivity session stitch logic using SQL `LAG()` window variables.
  2. Merge clickstream duration charts with bottom-of-the-funnel conversion rates to verify if longer sessions actively translate to higher completed transactions.

## 🚀 Repository Structure
- `/queries`: Houses the fully formatted, human-readable `.sql` BigQuery files.
- `/presentation`: Contains the analytical insights slide deck.
- `/dashboards`: Links to the live, interactive data visualization canvas.


Sprint: Marketing Analytics Project: Marketing Campaign Comparison The link: https://colab.research.google.com/drive/1VayZhfELJNt04LoKY4D9E4wVW-wBf-9T#scrollTo=Me4mHdszc1KL
