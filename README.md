# IBM Data Science Capstone: SpaceX Falcon 9 Analysis
This repository holds my capstone Project for the **IBM Data Science Professional Certificate** on Coursera. The project examines **SpaceX Falcon 9** launch data to predict first-stage landing success. My involvement with the **Columbia Space Initiative Rockets Team** provide general rocketry experience that shaped my perspective on reusability and launch dynamics.


## Project Overview
The analysis covers 90 Falcon 9 launches from 2010 to 2021. Data comes from SpaceX API for launch details and Wikipedia scraping for outcomes. The aim is to forecast landing success, allowing cost estimates for booster reuse and informed bidding by a fictional competitor, SpaceY. Core findings: success rates reached 100% by 2020, with peaks in 2000-4000 kg payloads and SSO orbits.


## Methodology
The pipeline spans data acquisition, preparation, exploration, visualization, and modeling.

- **Data Collection:** Pulled JSON via requests from SpaceX v4/launches for flight numbers, sites, payload masses, and orbits. Parsed Wikipedia's Falcon 9 table with BeautifulSoup for booster versions and outcomes. Merged datasets on flight number to get 90 records. 

  [API Notebook](https://github.com/faansing/IBM-Data-Science/blob/main/1.1_SpaceX_Data_Collection_API.ipynb).
  [Scraping Notebook](https://github.com/faansing/IBM-Data-Science/blob/main/1.2_Web_Scraping.ipynb).

- **Data Wrangling:** Replaced payload NaNs with mean of 3,066 kg, one-hot encoded sites (4 unique) and orbits (11 unique), and set binary success labels. Removed extraneous columns and normalized for modeling.

  [Wrangling Notebook](https://github.com/faansing/IBM-Data-Science/blob/main/1.3_SpaceX_Data_Wrangling.ipynb).

- **EDA:** Seaborn plots tracked success growth from 0% in 2013 to 100% in 2020, linking low payloads to better outcomes. SQL queries on SQLite tallied NASA payloads at 45,596 kg, noted the first ground landing on 2015-12-22, and recorded 98 successes against 1 failure.

  [SQL EDA Notebook](https://github.com/faansing/IBM-Data-Science/blob/main/2.1_EDA_SQL.ipynb).
  [Visual EDA Notebook](https://github.com/faansing/IBM-Data-Science/blob/main/2.2_EDA_Data_Visualization.ipynb).

- **Interactive Analytics:** Folium maps plotted sites with success markers and distance lines (e.g., 0.86 km to coast), underscoring coastal benefits for drone recoveries. Plotly Dash created interactive pies and scatters with filters, exposing KSC LC-39A's 76.9% rate and FT boosters' mid-payload performance.

  [Folium Notebook](https://github.com/faansing/IBM-Data-Science/blob/main/3.1_Launch_Site_Location.ipynb).
  [Dash App](https://github.com/faansing/IBM-Data-Science/blob/main/3.2_SpaceX_Dash_App.py).

- **Predictive Modeling:** Applied feature scaling, 80/20 train-test split, and GridSearchCV tuning to Logistic Regression, SVM, Decision Tree, and KNN. Models averaged 83% test accuracy; Decision Tree stood out with even precision/recall and zero false negatives. Leading features: orbit (0.35 importance), payload (0.25).

  [ML Notebook](https://github.com/faansing/IBM-Data-Science/blob/main/4.1_SpaceX_Machine_Learning_Prediction.ipynb).


## Key Results
Success patterns emphasize low payloads and SSO/GTO orbits; initial failures like 2015 drone attempts resolved over time. Spatial analysis verifies U.S. coastal sites (CCAFS, VAFB, KSC) with 1-2 km access to rail/highway and 14 km city buffers for risk control. Dashboards flag success drops beyond 6000 kg. Models provide 83% accuracy, prioritizing conservative risk assessment.


## Implications for SpaceY
Reusability offers the main advantage; focus bids on sub-4000 kg missions at coastal sites like KSC. Predictions enable solid reuse forecasting. For operational use, incorporate weather inputs and ensembles to exceed 90% accuracy.


## Presentation
Complete slides available in PDF, spanning summary to appendix with charts, code examples, and extras like booster progression links.


#### Last updated: September 18, 2025. Contact via issues for details.
