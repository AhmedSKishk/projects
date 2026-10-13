# IMDb Top 1000 Movies — Data Cleaning & Analysis

An end-to-end data science project focused on exploring, cleaning, and analyzing the IMDb Top 1000 movies dataset using `pandas` and `numpy`.

## Project Structure
```text
├── dataset/
│   └── imdb_top_1000.csv
├── imdb_analysis.ipynb
├── requirements.txt
└── README.md
```

## Dataset Description
The dataset contains information on the top 1000 movies rated on IMDb. Key columns include:
- `Series_Title`: Title of the movie
- `Released_Year`: Year the movie was released
- `Certificate`: Age/content rating (e.g., U, A, PG-13, R)
- `Runtime`: Movie duration (e.g., "142 min")
- `IMDB_Rating`: IMDb user rating out of 10
- `Meta_score`: Metacritic score out of 100
- `Director` & `Star1`–`Star4`: The director and lead actors
- `No_of_Votes`: Number of user votes
- `Gross`: Box office gross revenue (USD)

---

## Data Cleaning Steps
To ensure data quality for the analysis, the following structural and logical cleaning steps were performed:
- **Feature Dropping:** Removed `Poster_Link` and `Overview` columns as they were not required for this quantitative analysis.
- **Handling False Duplicates:** Investigated the movie `Drishyam`, which appeared twice. Verification of the director and cast confirmed they were two different entries (original and remake) rather than a duplicated row; hence, both rows were intentionally kept.
- **Categorical Merging:** Standardized the `Certificate` column by merging conflicting written formats (e.g., merging `U/A` and `UA` into a single `UA` label).
- **Data Type Conversion & Formatting:**
  - Handled an anomaly in `Released_Year` where a value was set to "PG" by correcting it to its actual release year (`1995` for *Apollo 13*) and converting the column to an Integer.
  - Stripped the " min" suffix from `Runtime` and converted it to an Integer.
  - Removed comma separators from `Gross` earnings and converted the column to a Float.
- **Missing Values Triage:** Identified missing entries in `Gross` (16.9%), `Meta_score` (15.7%), and `Certificate` (10.1%). These were intentionally left as `NaN` rather than filled with statistical averages to prevent introducing invented or skewed data into the financial metrics.

---

## Key Findings & Insights
- **Highest Revenue:** *Star Wars: Episode VII - The Force Awakens* generated the highest gross revenue in the dataset (approx. **\$936.7M**), followed closely by *Avengers: Endgame* (**\$858.4M**) and *Avatar* (**\$760.5M**).
- **The 2000s Era:** There are 260 movies released between 2000 and 2010 in this dataset, pulling in an average gross revenue of **\$73.7M** per movie.
- **Director Runtimes:** Average runtimes differ significantly by cinematic style; *Kenneth Branagh* recorded the longest average duration (**242 min**), while *Buster Keaton* marked the shortest (**45 min**).
- **Score Convergence:** Across the 843 movies containing both rating systems, IMDb user ratings and critic Metascores rarely overlap perfectly at the absolute top. Only **one movie** (*The Godfather*) managed to secure a spot in both individual Top-10 ranking lists simultaneously.
- **Core Correlations:** 
  - A strong positive correlation exists between `No_of_Votes` and `Gross` (**0.57**) as well as `IMDB_Rating` (**0.49**), indicating that highly popular movies with massive voter turnouts yield larger box office returns and higher placement.
  - Interestingly, a movie's individual `IMDB_Rating` alone shows almost no direct correlation with its `Gross` revenue (**0.10**). 
  - A noticeable negative correlation (**-0.34**) was found between `Meta_score` and `Released_Year`, implying that modern entries tend to receive stricter critical scores compared to classic titles.

---

## Dataset Limitations
- **Rating Boundary Bias:** Since the source data is pre-filtered to represent a "Top 1000" chart, the `IMDB_Rating` range is restricted exclusively between 7.6 and 9.3, making comprehensive population generalizations difficult.
- **Financial Data Gaps:** 16.9% of the films lack `Gross` box office information, which slightly limits the absolute certainty of the financial correlation models.

## How to Run the Project
1. Clone this repository to your machine.
2. Install the necessary dependencies using:
   ```bash
   pip install -r requirements.txt
   ```
3. Open `imdb_analysis.ipynb` using Jupyter Notebook or VS Code to explore the complete workflow.
