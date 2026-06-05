# Capstone Task Tracker

This file mirrors the project's GitHub Issues. Each section corresponds to one issue; checkboxes mirror the
issue checklists. Code/data work is complete; remaining unchecked items are the presentation deliverable and
the screenshots that must be captured from the running notebooks/app.

## Issue 1 — Data collection & wrangling
Collect the raw launch data and produce the cleaned dataset with the training label.

- [x] Run `1-jupyter-labs-spacex-data-collection-api.ipynb` end to end (GET → `json_normalize` → filter to Falcon 9 → handle missing values)
- [x] Run `2-jupyter-labs-webscraping.ipynb` (request Wiki page → BeautifulSoup → parse launch table → DataFrame)
- [x] Run `3-labs-jupyter-spacex-Data-wrangling.ipynb` and verify the `Class` label (1 = successful landing, 0 = not) is created correctly
- [x] Commit all three notebooks and the output CSVs (`spacex_web_scraped.csv`, `dataset_part_*.csv`)
- [x] Confirm each notebook URL resolves publicly

## Issue 2 — Exploratory data analysis (SQL + visualization)
Complete both EDA tracks and capture outputs for the results slides.

- [x] Run `5-jupyter-labs-eda-sql-coursera-sqllite.ipynb` (launch sites, payloads, success rates, rankings, date analysis)
- [ ] Screenshot each SQL query + its output for slide 1.12
- [x] Run `4-edadataviz.ipynb` (scatter plots, bar chart, yearly success-rate trend)
- [ ] Export each chart as an image for slide 1.11
- [x] Commit both notebooks and confirm URLs resolve

## Issue 3 — Interactive analytics (Folium + Dash)
Build the map and dashboard and capture the required views.

- [x] Run `6-lab-jupyter-launch-site-location.ipynb`
- [ ] Screenshot all launch-site markers
- [ ] Screenshot success/fail markers (color-coded / MarkerCluster)
- [ ] Screenshot proximity analysis with a calculated distance (coastline / railway / highway)
- [x] Run `spacex_dash_app.py` locally
- [ ] Screenshot the success pie chart (all sites + a single site)
- [ ] Screenshot the payload-vs-outcome scatter with the range slider applied
- [x] Commit the notebook and `spacex_dash_app.py`; confirm URLs resolve

## Issue 4 — Predictive modeling
Train and evaluate the classification models.

- [x] Run `7-SpaceX-Machine-Learning-Prediction-Part-5.ipynb`
- [x] Record the accuracy of all four models (Logistic Regression, SVM, Decision Tree, KNN)
- [x] Identify the best-performing model and note why
- [x] Capture the confusion matrix of the best model
- [x] Commit the notebook; confirm URL resolves

## Issue 5 — Repo hygiene
Make the repository grader-ready.

- [x] Write `README.md` with project overview, file structure, and links to every notebook
- [x] Set the repository to public
- [x] Click every notebook/file URL to confirm it resolves for an external viewer
- [x] Verify all CSVs and the Dash app are pushed

## Issue 6 — Build the presentation (15-point deliverable)
Assemble the final slide deck and submit.

- [ ] Title + outline slides
- [ ] Executive Summary — methods + key results (1.3)
- [ ] Introduction — background + problem statement (1.4)
- [ ] Methodology slides with flowcharts + GitHub URLs: API (1.5), scraping (1.6), wrangling (1.7), EDA-viz (1.8), EDA-SQL (1.9), interactive (1.10)
- [ ] Results slides with images/screenshots: EDA-viz (1.11), EDA-SQL (1.12), Folium (1.13), Dash (1.14)
- [ ] Predictive Analysis slides: model comparison, confusion matrix, best-model explanation, conclusion with original insights (1.15)
- [ ] Export to PDF named exactly `Data Science Capstone Project Report.pdf`
- [ ] Submit GitHub URL (1.1) + PDF (1.2)
