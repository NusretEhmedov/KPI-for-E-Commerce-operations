# E-Commerce Operations Analytics & KPI Framework

An advanced data engineering and analytical framework built to evaluate marketplace revenue trends, fulfillment performance, and vendor risks using transactional data from Olist (Brazil).

---

## 🛠️ Tech Stack & Key Files

* **Core Libraries:** Python 3.x, `pandas`, `matplotlib`, `seaborn`
* **Development Environment:** Jupyter Notebook / Interactive Python (`.ipynb` / `.py`)

### Submission Manifest

| File / Output | Description |
| :--- | :--- |
| `olist_kpi_framework.ipynb` | End-to-end ETL pipeline, data transformations, and visual analytics. |
| `note.md` | Comprehensive methodology summary, KPI scorecards, and strategic business takeaways. |
| `category_kpis.csv` | Aggregated metrics (Revenue, AOV, Delivery Days, Review Score) per product category. |
| `monthly_kpi_summary.csv` | Historical time-series tracking of key operational and financial metrics. |
| `seller_kpis.csv` | Merchant performance scorecard (GMV, order volume, mean review ratings). |
| `flagged_categories.csv` | Isolated list of operational bottleneck categories (slow delivery + low ratings). |

---

## 🔄 Data Pipeline Architecture

```text
[ olist_orders_dataset ]
       │
       ├── (Filter: order_status == "delivered")
       ▼
[ Base Orders ] ─── Join on order_id ───► [ olist_order_items_dataset ]
                                                 │
                                           Join on product_id
                                                 ▼
[ olist_order_reviews_dataset ] ──────► [ olist_products_dataset ]
  (Aggregated to 1 score / order)                │
                                           Join on product_category_name
                                                 ▼
                                  [ category_translation_dataset ]
                                                 │
                                                 ▼
                                     [ Unified Analytical Dataset ]
