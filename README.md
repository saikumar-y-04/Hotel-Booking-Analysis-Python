# 🏨 AtliQ Hotels – Hospitality Data Analysis (EDA)

An end-to-end Exploratory Data Analysis project on AtliQ Hotels' booking data to uncover revenue trends, occupancy patterns, and platform performance insights using Python.

---

## 📌 Project Overview

AtliQ Hotels is a fictional hospitality chain operating across multiple Indian cities. This project analyzes **1,34,600 booking transactions** to help the business understand occupancy rates, revenue drivers, and booking behavior — the kind of insights that inform pricing, staffing, and platform investment decisions.

---

## 📂 Dataset

| File | Description |
|------|-------------|
| `fact_bookings.csv` | 1,34,600 individual booking records with revenue, ratings, and booking status |
| `fact_aggregated_bookings.csv` | Property-level daily booking counts and room capacity |
| `dim_hotels.csv` | Hotel metadata — name, city, and category (Luxury / Business) |
| `dim_rooms.csv` | Room type mapping (RT1–RT4 → Standard, Premium, Elite, Presidential) |
| `dim_date.csv` | Date dimension with week number, month, and day type (weekday/weekend) |

---

## 🛠️ Tools & Libraries

- **Python 3.11**
- **Pandas** — data manipulation, groupby aggregations, merging
- **NumPy** — statistical computations
- **Matplotlib** — bar charts, pie charts, trend visualizations

---

## 🔄 Project Workflow

### 1. Data Import & Exploration
- Loaded all 5 datasets and explored schema, data types, and shape
- Identified 25 unique properties across multiple cities
- Found 6 booking platforms: direct online, direct offline, logtrip, makeyourtrip, tripster, others

### 2. Data Cleaning
- **Invalid guests**: Removed records with negative guest count (data entry errors)
- **Revenue outliers**: Applied mean ± 3×standard deviation rule to filter extreme values in `revenue_generated`; confirmed no outliers in `revenue_realized` for RT4 (Presidential Suite) rooms
- **Null values**: Identified 77,897 missing ratings in `fact_bookings` — retained as-is (replacing with mean/median would distort guest satisfaction analysis); imputed 2 missing `capacity` values in aggregated bookings with the column median
- **Data integrity**: Filtered 6 records where `successful_bookings` exceeded room `capacity`

### 3. Data Transformation
- Engineered `occ_pct` (occupancy percentage) column: `successful_bookings / capacity × 100`
- Merged dimension tables with fact tables to enable city, room class, and date-based analysis
- Appended August 2022 data to existing May–July dataset for continuous monthly tracking

### 4. Insights Generation

| # | Business Question | Key Finding |
|---|-------------------|-------------|
| 1 | Average occupancy by room class | Presidential Suite (RT4) had the highest occupancy |
| 2 | Average occupancy by city | Occupancy varied significantly across cities |
| 3 | Weekday vs. weekend occupancy | Weekends showed higher average occupancy |
| 4 | City-wise occupancy in June 2022 | Ranked cities by June occupancy performance |
| 5 | Month-by-month revenue trend | Revenue tracked across May–August 2022 |
| 6 | Revenue realized per city | City-level revenue contribution identified |
| 7 | Revenue by booking platform | Platform share visualized via pie chart |
| 8 | Average guest rating per city | City-wise satisfaction benchmarked |
| 9 | Revenue per hotel property | Individual property revenue ranked |

---

## 📊 Sample Visualizations

- Bar chart: Booking platform distribution
- Bar chart: City-wise occupancy for June 2022
- Bar chart: Total bookings per property
- Pie chart: Revenue realized by booking platform

---

## 💡 Key Takeaways

- Weekends consistently outperform weekdays in occupancy — useful for dynamic pricing strategy
- Presidential Suite rooms (RT4) generate disproportionately high revenue per booking
- A significant share of ratings are missing (~58% of bookings have no rating) — indicates a gap in guest feedback collection
- Certain cities drive the majority of revenue, pointing to where marketing investment is concentrated

---

## 📁 Project Structure

```
atliq-hotels-eda/
│
├── datasets/
│   ├── fact_bookings.csv
│   ├── fact_aggregated_bookings.csv
│   ├── dim_hotels.csv
│   ├── dim_rooms.csv
│   ├── dim_date.csv
│   └── new_data_august.csv
│
├── exercise_solution.ipynb   ← Main analysis notebook
└── README.md
```

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/saikumar-y-04/atliq-hotels-eda.git
cd atliq-hotels-eda

# Install dependencies
pip install pandas numpy matplotlib jupyter

# Launch the notebook
jupyter notebook exercise_solution.ipynb
```

---

## 👤 Author

**Yelkagudem Saikumar**  
[LinkedIn](https://linkedin.com/in/saikumar-yelkagudem) • [GitHub](https://github.com/saikumar-y-04)
