# Madrid Airbnb: Market Consolidation & Profitability Analysis

A SQL deep-dive into Madrid's Airbnb market structure: who controls the listings, where the money concentrates, and what the long tail looks like.

**Notebook:** [`Notebooks/01_madrid_sql_analysis.ipynb`](Notebooks/01_madrid_sql_analysis.ipynb)

## Headline findings

- **The top 10% of hosts control 53.3% of all Madrid Airbnb listings.** Just 32 hosts (0.3% of the host population) operate 17% of the market.
- **The largest "hosts" are property management companies** — Ukio (338 listings), Homeclub (324), MIT House (274), and Bemadrid (240) operate at corporate scale, not as individuals.
- **The Salamanca district dominates revenue per listing.** Recoletos (€40,410), Goya (€36,796), and Castellana (€32,646) take the top three spots in estimated annual revenue per listing.
- **Embajadores has the most listings (1,812) but ranks 14th in revenue per listing.** High volume, low margin.
- **Multi-listing hosts earn slightly less per night (€177 vs €185) and get worse reviews (4.61 vs 4.74)** than single-listing operators. Professionalization comes at a measurable experience cost.

## Stack

- **DuckDB** for in-process SQL against CSV files
- **Python + pandas** for orchestration
- **Plotly** for the four interactive visualizations
- **Jupyter** for the notebook environment

## SQL techniques on display

- Multiple chained CTEs
- Window functions: `NTILE(10)`, `RANK()`, `SUM(...) OVER ()`
- Joins across listings (23k rows) and calendar (8.4M rows)
- Conditional aggregations with `FILTER (WHERE ...)`
- Outlier handling with `BETWEEN` and `IS NOT NULL` guards

## Reproducing the analysis

1. Download these 4 files from [Inside Airbnb's Madrid page](http://insideairbnb.com/get-the-data) (free, no signup):
   - `listings.csv.gz`
   - `calendar.csv.gz`
   - `reviews.csv.gz`
   - `neighbourhoods.csv`
2. Unzip the `.gz` files (use `gunzip` on macOS if Archive Utility refuses).
3. Place all four `.csv` files in a folder named `Data/` at the project root.
4. Install dependencies: `pip install -r requirements.txt`
5. Open `Notebooks/01_madrid_sql_analysis.ipynb` and run cells top-to-bottom.

The CSV data is ~700 MB total and not committed to this repo. See Inside Airbnb's [terms of use](http://insideairbnb.com/about/).

## About

Built by Wissam Ezzedine.
- Portfolio: [wissam-ezzedine.netlify.app](https://wissam-ezzedine.netlify.app)
- LinkedIn: [linkedin.com/in/wissam-ezzedine](https://www.linkedin.com/in/wissam-ezzedine)
- Contact: wissamezzedine123@outlook.com