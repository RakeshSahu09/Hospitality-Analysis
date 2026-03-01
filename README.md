# 🏨 Hospitality Revenue & Occupancy Analysis

Exploratory data analysis on hotel booking data (May–Jul 2022) across 25 properties in 4 Indian cities. Covers data cleaning, occupancy rates, revenue leakage from cancellations, platform performance, and customer ratings. Built with Python, Pandas, Matplotlib & Seaborn.

---

## 📁 Project Structure

```
hospitality-analysis/
│
├── datasets/
│   ├── fact_bookings.csv           # 134,590 individual booking records
│   ├── fact_aggregated_bookings.csv # Aggregated bookings by property & room
│   ├── dim_date.csv                # Date dimension table
│   ├── dim_hotels.csv              # Hotel properties metadata
│   ├── dim_rooms.csv               # Room category metadata
│   └── new_data_august.csv         # New August 2022 data
│
└── analysis.ipynb                  # Main analysis notebook
```

---

## 📊 Dataset Overview

| Table | Rows | Description |
|---|---|---|
| `fact_bookings` | 134,590 | Individual bookings with revenue, platform, status |
| `fact_aggregated_bookings` | 9,200 | Daily capacity vs successful bookings per property |
| `dim_hotels` | 25 | Property names, cities, categories |
| `dim_rooms` | 4 | Room types (Standard, Elite, Premium, Presidential) |
| `dim_date` | — | Date, week number, day type (weekday/weekend) |

**Cities covered:** Mumbai, Delhi, Bangalore, Hyderabad  
**Period:** May 2022 – July 2022

---

## 🧹 Data Cleaning

- Removed **9 records** with invalid guest counts (`no_guests ≤ 0`)
- Removed **5 revenue outliers** using mean ± 3σ rule (`revenue_generated`)
- Removed **6 rows** where `successful_bookings > capacity` (impossible values)
- Filled **2 null capacity values** with median
- Fixed **date parsing** for mixed-format `check_in_date` column using `dayfirst=True`

---

## 🔍 Key Analyses & Insights

### Occupancy
- Average occupancy is uniform across room classes (~58–59%), with Presidential rooms slightly ahead at 59.3%
- City-level occupancy varies — visualized via bar charts and a heatmap (City × Month)

### Revenue
- Monthly revenue dipped in June (₹52.9M) compared to May (₹60.9M) and July (₹60.3M)
- Mumbai leads total revenue, consistent with having the most properties (8)
- Revenue leakage from cancellations analyzed per city by comparing `revenue_generated` vs `revenue_realized`

### Booking Platforms
- "Others" dominates booking volume; direct channels have lower cancellation rates
- Platform-level cancellation rates and revenue realized compared to identify the most valuable channels

### Customer Ratings
- ~58% of bookings have no rating, mostly from cancelled/no-show bookings
- Average ratings analyzed by city and platform to surface service quality gaps

---

## 📈 Visualizations

- Booking volume by platform (bar chart)
- Occupancy % by city, room class, and day type
- City × Month occupancy heatmap
- Monthly revenue trend
- Revenue generated vs realized by city
- Cancellation rate by platform and city
- Average customer rating by city and platform

---

## 🛠️ Tech Stack

- **Python 3.13**
- **Pandas** — data manipulation and cleaning
- **Matplotlib** — plotting
- **Seaborn** — statistical visualizations
- **Jupyter Notebook**

