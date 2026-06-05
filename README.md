# IBM Data Science Capstone — Predicting Falcon 9 First-Stage Landing Success

Final project for the **IBM Data Science Professional Certificate (Applied Data Science Capstone)**.

SpaceX advertises Falcon 9 launches at roughly \$62M, against \$165M+ for competitors, largely because it
recovers and reuses the first stage. Whether that first stage lands successfully therefore determines a
large share of the cost of a launch. This project builds an end-to-end pipeline that collects historical
Falcon 9 launch data, engineers features, explores the drivers of landing success, and trains classification
models to **predict whether the first stage will land**, given launch attributes such as payload mass, orbit,
launch site, and booster history.

## Problem statement

Given the characteristics of a planned launch (payload mass, target orbit, launch site, booster version,
flight number, and reuse history), can we predict whether the Falcon 9 first stage will land successfully?
A reliable prediction lets a competitor estimate the true cost of a launch and informs bidding strategy.

## Goals

- Collect Falcon 9 launch records from the SpaceX REST API and from Wikipedia.
- Wrangle the data and derive a binary training label (`Class`: 1 = successful landing, 0 = unsuccessful).
- Explore the data with SQL and with visualization to identify the factors associated with success.
- Build interactive analytics: a Folium launch-site map and a Plotly Dash dashboard.
- Train and compare four classifiers (Logistic Regression, SVM, Decision Tree, KNN) and select the best.

## Repository structure

```
ibm-ds-ps-capstone-spacex/
├── README.md                     # This file
├── TASKS.md                      # Task tracker mirroring the project's GitHub issues
├── requirements.txt              # Python dependencies
├── .gitignore
├── spacex_dash_app.py            # Plotly Dash dashboard (run: python spacex_dash_app.py)
├── spacex_launch_dash.csv        # Data consumed by the Dash app (read from the working directory)
├── spacex_launch_map.html        # Rendered Folium map (open in a browser)
├── notebooks/
│   ├── 1-jupyter-labs-spacex-data-collection-api.ipynb   # Data collection via SpaceX REST API
│   ├── 2-jupyter-labs-webscraping.ipynb                  # Data collection via web scraping
│   ├── 3-labs-jupyter-spacex-Data-wrangling.ipynb        # Wrangling + Class label
│   ├── 4-edadataviz.ipynb                                # EDA with visualization + feature engineering
│   ├── 5-jupyter-labs-eda-sql-coursera-sqllite.ipynb     # EDA with SQL
│   ├── 6-lab-jupyter-launch-site-location.ipynb          # Interactive Folium map
│   └── 7-SpaceX-Machine-Learning-Prediction-Part-5.ipynb # Predictive modeling
└── data/
    ├── dataset_part_1.csv        # Cleaned Falcon 9 dataset (output of notebook 1)
    ├── dataset_part_2.csv        # Wrangled dataset with Class label (output of notebook 3)
    ├── dataset_part_3.csv        # One-hot encoded feature matrix (output of notebook 4)
    ├── spacex_web_scraped.csv    # Scraped launch table (output of notebook 2)
    ├── spacex_launch_geo.csv     # Geocoded launch records (input to the Folium map)
    └── spacex_launch_dash.csv    # Data for the Dash app
```

## Pipeline and notebooks

| # | Notebook | Stage | Key output |
|---|----------|-------|-----------|
| 1 | [Data collection — API](notebooks/1-jupyter-labs-spacex-data-collection-api.ipynb) | `GET` request → `json_normalize` → filter to Falcon 9 → impute missing `PayloadMass` | `dataset_part_1.csv` |
| 2 | [Data collection — web scraping](notebooks/2-jupyter-labs-webscraping.ipynb) | Request Wikipedia page → BeautifulSoup → parse launch table → DataFrame | `spacex_web_scraped.csv` |
| 3 | [Data wrangling](notebooks/3-labs-jupyter-spacex-Data-wrangling.ipynb) | Compute landing outcomes → derive `Class` label | `dataset_part_2.csv` |
| 4 | [EDA with visualization](notebooks/4-edadataviz.ipynb) | Scatter/bar/line charts → one-hot encode features | `dataset_part_3.csv` |
| 5 | [EDA with SQL](notebooks/5-jupyter-labs-eda-sql-coursera-sqllite.ipynb) | Launch sites, payloads, success rates, rankings, date analysis | SQL result tables |
| 6 | [Interactive map (Folium)](notebooks/6-lab-jupyter-launch-site-location.ipynb) | Site markers, success/fail clusters, proximity distances | `spacex_launch_map.html` |
| 7 | [Predictive modeling](notebooks/7-SpaceX-Machine-Learning-Prediction-Part-5.ipynb) | Train/test split, GridSearchCV for 4 models, evaluation | Confusion matrices |

## Selected results

- **Data**: 90 Falcon 9 launches retained after filtering; the scraped Wikipedia table yields 121 rows. The
  binary `Class` label is derived from the textual landing outcomes.
- **EDA (SQL)**: four launch sites; total NASA (CRS) payload mass ≈ 45,596 kg; average Falcon 9 v1.1 payload
  ≈ 2,928 kg; first successful ground-pad landing on 2015-12-22.
- **EDA (visualization)**: success rate rises with flight number (accumulated experience) and varies sharply by
  orbit type; the 2,000–4,000 kg payload band shows the strongest success rate; the yearly trend is upward.
- **Predictive modeling**: Logistic Regression, SVM, Decision Tree, and KNN all reach **0.833 accuracy** on the
  held-out test set (18 samples). On cross-validation the Decision Tree achieves the best score (~0.89). With a
  test set this small the four models are effectively tied, so model choice should be revisited with more data.

## How to run

```bash
pip install -r requirements.txt

# Notebooks (each is self-contained and downloads its inputs at runtime)
jupyter lab    # then open the notebooks in notebooks/ in order 1 → 7

# Interactive dashboard
python spacex_dash_app.py     # serves at http://127.0.0.1:8050
```

## Tech stack

Python · pandas · NumPy · Matplotlib · Seaborn · BeautifulSoup · requests · SQLite / ipython-sql · Folium ·
Plotly · Dash · scikit-learn.

---

*Course: IBM Data Science Professional Certificate — Applied Data Science Capstone.*
