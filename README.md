# MovieLens Ratings Analysis — SQL + Python

**Tools:** Python · SQL · SQLite · pandas · Matplotlib  
**Dataset:** MovieLens 100K (100,000 ratings · 1,682 movies · 943 users)  
**Notebook:** `sql_movie_analysis.ipynb`

---

## Overview

Most data analysis courses teach SQL in isolation from real workflows. This project demonstrates SQL used as the primary analytical tool inside a Python environment — loading a real dataset into a relational SQLite database, writing structured queries to answer business questions, and visualising the results.

---

## Key Findings

- **Rating bias:** Ratings skew heavily toward 4–5 stars; fewer than 15% of all ratings are below 3, suggesting users tend to self-select movies they already expect to enjoy
- **Popularity vs quality:** The most-rated movies are not necessarily the highest-rated — volume and quality are largely uncorrelated in this dataset
- **User activity is skewed:** The top 5% of users contribute a disproportionate share of all ratings, while the majority of users rated fewer than 50 movies
- **Minimum review threshold matters:** High average ratings on movies with fewer than 20 reviews are unreliable — filtering by minimum review count significantly changes the "best movies" ranking

---

## Screenshots

<!-- Upload your chart images to this repo, then replace the filenames below -->

![Rating Distribution](rating_distribution.png)
*Distribution of all ratings — clear skew toward positive scores*

![Most Rated Movies](images/most_rated_movies.png)
*Top 10 movies by number of ratings*

![User Activity Distribution](images/user_activity.png)
*Ratings per user — heavy-tailed distribution*

---

## SQL Questions Answered

| Question | Method |
|---|---|
| What is the average rating across all movies? | `AVG()` aggregate |
| Which movies have the most ratings? | `COUNT()` + `GROUP BY` + `ORDER BY` |
| Which movies are highest-rated (min 20 reviews)? | `HAVING COUNT() >= 20` filter |
| Who are the most active raters? | `GROUP BY user_id` + `ORDER BY COUNT()` |
| How are ratings distributed (1–5)? | `GROUP BY rating` frequency count |
| Does rating volume correlate with score? | Cross-query comparison |

---

## Project Workflow

**1. Database setup**
- Loaded raw MovieLens `.data` files into a structured SQLite database using Python
- Created `ratings` and `movies` tables with appropriate schema and data types

**2. SQL analysis**
- Wrote and ran queries entirely within Jupyter using `ipython-sql`
- Each query answers a specific analytical question with results displayed inline

**3. Visualisation**
- Pulled query results into pandas DataFrames
- Plotted distributions and rankings using Matplotlib

---

## How to Run
```bash
git clone https://github.com/Amr0024/SQL-Movie-dataset-Analysis-.git
cd SQL-Movie-dataset-Analysis-
pip install pandas matplotlib ipython-sql
jupyter notebook sql_movie_analysis.ipynb
```

Dataset: download from [GroupLens](https://files.grouplens.org/datasets/movielens/ml-100k.zip) and extract into the project folder.

---

## Author

**Amr Nabil** — Computer Science graduate, Data Science & Machine Learning  
[LinkedIn](https://www.linkedin.com/in/amr-nabil623813220/) · [GitHub](https://github.com/Amr0024)
