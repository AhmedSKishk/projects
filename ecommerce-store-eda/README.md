# Ecommerce Store: End-to-End Data Analysis

An end-to-end analysis of an online clothing store's sales (Jan 1 – Oct 24, 2021): from loading the data out of a MySQL database, through cleaning and feature engineering, to answering business questions with interactive Plotly charts.

## Business questions

1. Where are the customers? (customers per state)
2. How are sales trending? (weekly revenue, average daily revenue per month)
3. What sells best? (product type, top products, size, colour)
4. Who buys? (age group, gender)
5. When do customers buy? (weekday pattern)
6. How long does delivery take? (overall and by state)

## Dataset

Four related MySQL tables, created by `database/store_database.sql` in the database `store_db`:

| Table | Description |
|-------|-------------|
| `customers` | Customer profile: name, gender, age, address, state |
| `orders` | Order date and delivery date per customer |
| `products` | Product type, style, size, colour, stock |
| `sales` | Line items: product, quantity, unit price, total price |

They are merged into one table (`customers → orders → sales → products`) of **5,000 line items**, **616 customers** and about **999 orders**.

## Key findings

- **Revenue:** about **$1.03M** in total, split almost evenly between Jackets ($357K), Trousers ($341K) and Shirts ($334K).
- **Trend:** no clear growth. Average daily revenue peaks in **March (~$4,238)** and dips in **May (~$2,761)**.
- **Weekday:** **Sunday** is the strongest day (~$4,152/day), about 34% above **Friday** (~$3,103), the weakest.
- **Customers:** female customers and the 30–39 age group spend the most per customer, but group sizes are small.
- **Delivery:** takes about **13–15 days** on average in every state; New South Wales and South Australia are the slowest.
- **Size and colour:** demand is spread nearly evenly across sizes; Blue is the most popular colour.

The full conclusions, recommendations and limitations are in section 8 of the notebook.

## Project structure

```
.
├── ecommerce-store-eda-project.ipynb   # the full analysis
├── database/
│   └── store_database.sql              # creates and fills the store_db database
├── data/                               # source data files
├── requirements.txt                    # Python dependencies
├── .env.example                        # template for database credentials
├── .gitignore
└── README.md
```

## How to run

1. **Create the database** (MySQL must be installed and running):
   ```bash
   mysql -u <user> -p < database/store_database.sql
   ```
2. **Set your credentials:** copy `.env.example` to `.env` and fill in your values.
   ```bash
   cp .env.example .env
   ```
3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
4. **Open the notebook** in Jupyter or VS Code and run all cells.

> Charts use the static `png` renderer (needs `kaleido`) so they show up on GitHub. To get interactive charts locally, remove the `pio.renderers.default = 'png'` line in the Setup cell.

## Tech stack

Python, pandas, NumPy, Plotly, MySQL (`mysql-connector-python`), python-dotenv, Jupyter.

## Notes

- `.env` holds credentials and is excluded through `.gitignore`. Never commit it.
- The data looks synthetic (very uniform distributions), so treat the findings as a demonstration of the analysis workflow rather than real market insight.
