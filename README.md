# SpaceX Falcon 9 First Stage Landing Prediction

**GitHub Repository:** [https://github.com/AdithyaSM31/IBM-Applied-Data-Science-Capstone-Project](https://github.com/AdithyaSM31/IBM-Applied-Data-Science-Capstone-Project)

## 1. Executive Summary
The goal of this project is to predict the successful landing of the SpaceX Falcon 9 first stage rocket. By leveraging machine learning classification models, we can estimate whether a launch will result in a successful recovery, which is crucial for reducing launch costs significantly.
*   **Key Results:** The project successfully processed data from API and web scraping, performed extensive EDA, built interactive dashboards, and trained four predictive models. All models achieved an accuracy of ~83.33% on the test set.

## 2. Introduction
SpaceX advertises Falcon 9 rocket launches on its website with a cost of 62 million dollars; other providers cost upward of 165 million dollars each. Much of the savings is because SpaceX can reuse the first stage. Therefore, if we can determine if the first stage will land, we can determine the cost of a launch. This information can be used if an alternate company wants to bid against SpaceX for a rocket launch.
*   **Problem:** Predict the success of the first stage landing.
*   **Solution:** Build a binary classification model (Success/Failure) using historical launch data.

## 3. Data Collection

### 3.1 SpaceX API
*   **Source:** SpaceX REST API.
*   **Method:**
    *   Made `GET` requests to endpoints: `/launches`, `/payloads`, `/cores`, `/rockets`, `/launchpads`.
    *   Extracted key features such as Flight number, date, booster version, payload mass, orbit, launch site, and landing outcome.
    *   Filtered the data to include only Falcon 9 launches.

### 3.2 Web Scraping
*   **Source:** Wikipedia - "List of Falcon 9 and Falcon Heavy launches".
*   **Method:**
    *   Utilized the `BeautifulSoup` library to parse HTML content.
    *   Extracted data from the launch table to supplement API data, focusing on filling gaps in historical records.
    *   Verified and cleaned the data for consistency.

## 4. Data Wrangling Methodology
*   **Cleaning:** Identification and handling of missing values (e.g., imputing payload mass with the mean).
*   **Filtering:** Focused analysis strictly on Falcon 9 launches.
*   **Transformation:**
    *   Created a `Class` column as the target variable: `1` for successful landings (True Ocean, True RTLS, True ASDS), and `0` for unsuccessful ones.
    *   Applied One-Hot Encoding to categorical variables (Orbits, Launch Sites) to prepare the dataset for Machine Learning algorithms.

## 5. Exploratory Data Analysis (EDA)

### 5.1 Visualization (Pandas & Seaborn)
*   **Charts Used:** Scatter plots, Bar charts, Line charts.
*   **Key Findings:**
    *   **Flight Number vs. Launch Site:** Success rates generally improved as the number of flights (experience) increased.
    *   **Payload vs. Orbit:** Heavy payloads are predominantly launched to LEO/ISS with high success; GTO missions show mixed success rates.
    *   **Yearly Trend:** The success rate has shown a significant and steady increase since 2013.

### 5.2 SQL Analysis
*   **Database:** SQLite.
*   **Queries:** `SELECT`, `COUNT`, `DISTINCT`, `AVG`, `GROUP BY`, `ORDER BY`.
*   **Insights:**
    *   Identified the top launch sites by frequency (CCAFS SLC-40, KSC LC-39A, VAFB SLC-4E).
    *   Calculated the total payload mass carried by NASA (CRS) missions.
    *   Ranked landing outcomes, highlighting the frequency of successful drone ship landings.

## 6. Interactive Visual Analytics

### 6.1 Folium Maps
*   **Map 1:** Visualization of launch sites with markers.
*   **Map 2:** Utilization of Marker Clusters to display successful vs. failed launches at each site.
*   **Analysis:**
    *   All launch sites are strategically located near coastlines to facilitate water landings for safety.
    *   Proximity analysis conducted with distance markers to railways, highways, and cities.

### 6.2 Plotly Dash Dashboard
*   **Components:**
    *   **Pie Chart:** Dynamic visualization showing Total Success Launches vs. Failed Launches for all sites or a specific site.
    *   **Scatter Plot:** Interactive correlation between Payload Mass (kg) and Launch Outcome (Success/Failure), color-coded by Booster Version.
*   **Interactivity:** Features a Dropdown menu for selecting Launch Sites and a Range Slider for filtering by Payload Mass.

## 7. Predictive Analysis (Machine Learning)
*   **Task:** Binary Classification (Land vs. Not Land).
*   **Preprocessing:** Standard Scaler applied to the feature set `X`.
*   **Models Trained:**
    *   Logistic Regression
    *   Support Vector Machine (SVM)
    *   Decision Tree Classifier
    *   K-Nearest Neighbors (KNN)
*   **Evaluation:**
    *   Data Split: 80% Training, 20% Testing.
    *   Hyperparameter Tuning: `GridSearchCV` with Cross-Validation (cv=10).
    *   Metrics: Accuracy Score, Confusion Matrix, Jaccard Index, F1-Score.
*   **Results:**
    *   All models performed similarly well with an accuracy of **83.33%** on the test set.
    *   The Decision Tree model provides good interpretability, while SVM and KNN are competitive.
    *   **Confusion Matrix Analysis:** The main source of error is False Positives (predicting a successful landing when it actually failed).

## 8. Files in this Repository
*   **`jupyter-labs-spacex-data-collection-api.ipynb`**: Notebook for Data Collection from SpaceX API.
*   **`jupyter-labs-webscraping.ipynb`**: Notebook for Web Scraping from Wikipedia.
*   **`labs-jupyter-spacex-Data wrangling.ipynb`**: Notebook for Data Wrangling and cleaning.
*   **`jupyter-labs-eda-sql-coursera_sqllite.ipynb`**: Notebook for EDA using SQL queries.
*   **`edadataviz.ipynb`**: Notebook for EDA using operational visualization libraries (Matplotlib/Seaborn).
*   **`SpaceX_Machine Learning Prediction_Part_5.ipynb`**: Notebook for Machine Learning model building, tuning, and evaluation.
*   **`spacex_launch_dash.csv`**: CSV dataset used for the Plotly Dash application.
*   **`ds-capstone-template-coursera.pptx`**: The final PowerPoint presentation slide deck.

## Author
Adithya S M
