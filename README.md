# Bridge the Gap — Dublin Airbnb Market Analysis

**UCI Atlantis Datathon 2024 hosted by [Data@UCI](https://www.dataatuci.com/)** | Team project

The short-term vacation rental market has grown rapidly in recent years, but supply and demand remain mismatched in many markets. We analyzed two weeks of Dublin Airbnb booking data to characterize the market, identify what drives successful transactions, and provide actionable insights for hosts and the platform.

📊 [View presentation (Canva)](https://www.canva.com/design/DAGB-j1Vfck/jLOiOJgd5YFA5TE8TsmQZQ/view)

---

## Tools
| Layer | Tool |
|-------|------|
| Data wrangling & EDA | Python (Pandas, NumPy, Plotly) |
| Machine learning | scikit-learn |
| Presentation | Canva |

---

## Data

Two tables provided by the datathon organizers covering approximately two weeks of Dublin Airbnb activity:

**`contacts.tsv`** — Guest inquiries with timestamps for contact, host reply, acceptance, and booking confirmation.

**`searches.tsv`** — Guest search activity including check-in/check-out dates, party size, origin country, and filters applied.

---

## Project structure

```
├── datathon_24.ipynb     # EDA and ML modeling notebook
├── contacts.tsv          # Inquiry-level data (not included — datathon data)
├── searches.tsv          # Search-level data (not included — datathon data)
└── README.md
```

---

## Analysis

### Data cleaning
- Audited null rates across both tables; removed unusable columns (e.g. `filter_neighborhoods`)
- Derived boolean features: `accepted` and `booked` to track funnel conversion
- Handled extreme outliers that reduced model quality on raw data

### Exploratory data analysis
- Modeled the full booking funnel: guest search → inquiry → host reply → acceptance → booking
- Analyzed weekday and monthly patterns in search and contact activity
- Examined guest behavior by origin country and stay characteristics (length, party size, lead time)
- Calculated conditional probabilities at each funnel stage (e.g. P(booking | accepted))

### Machine learning
Built two classification models to predict whether a guest inquiry would result in a booking:

| Model | Accuracy |
|-------|----------|
| Logistic Regression | ~81% |
| Random Forest | ~90% |

Models were trained on both raw and processed versions of the data to assess the impact of cleaning on predictive performance.

---

## Key findings

- **Host acceptance is the primary conversion bottleneck** — the vast majority of accepted inquiries converted to bookings
- **Guests prefer longer stays with larger groups** and tend to book further in advance
- **Dublin City Centre and peak seasonal periods** are underserved relative to demand
- **Origin country** correlates with booking conversion rate, suggesting geographic segmentation has predictive value

---

## Insights for hosts & platform
- Hosts should prioritize responding to and accepting inquiries — acceptance is strongly predictive of a completed booking
- Airbnb Dublin should expand supply around high-demand periods and central neighborhoods
- Pricing and availability strategies should account for guest lead time and party size signals

---

## Limitations & future work
- Dataset spans only ~two weeks — a longer time horizon would improve model stability and allow for seasonal forecasting
- Key variables are absent: price, room type, neighborhood of booked properties
- The same methodology could be applied to other cities by incorporating region-specific holidays and events

---

## Team
- Adityakrishnan Radhakrishnan
- Andrew Kang
- Cole Hajek
- Kian Kermani

---

## Notes
Data was provided exclusively for datathon use and is not included in this repository.
