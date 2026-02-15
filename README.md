# SpaceX Falcon 9 First Stage Landing Prediction

## Project Overview
This project is part of the **IBM Applied Data Science Capstone** on Coursera. The goal is to predict whether the first stage of the SpaceX Falcon 9 rocket will land successfully. SpaceX advertises Falcon 9 rocket launches on its website with a cost of 62 million dollars; other providers cost upward of 165 million dollars each, much of the savings is because SpaceX can reuse the first stage. Therefore, if we can determine if the first stage will land, we can determine the cost of a launch. This information can be used if an alternate company wants to bid against SpaceX for a rocket launch.

## Methodology

The project follows a standard Data Science methodology:

1.  **Data Collection:**
    *   Collected data using the SpaceX REST API.
    *   Scraped additional data from Wikipedia.
2.  **Data Wrangling:**
    *   Cleaned and filtered the dataset.
    *   Handled missing values.
    *   Created a binary classification target (1 for success, 0 for failure).
3.  **Exploratory Data Analysis (EDA):**
    *   Used SQL to query the dataset and gain initial insights.
    *   Visualized relationships using Matplotlib and Seaborn to understand factors affecting landing success (e.g., Payload Mass, Orbit type, Launch Site).
4.  **Interactive Visual Analytics:**
    *   Built an interactive map using Folium to visualize launch sites and their proximity to potential hazards/success factors.
    *   Created a Plotly Dash dashboard for dynamic exploration of the data.
5.  **Predictive Analysis (Machine Learning):**
    *   Trained and evaluated multiple classification models:
        *   Logistic Regression
        *   Support Vector Machine (SVM)
        *   Decision Tree
        *   K-Nearest Neighbors (KNN)
    *   Used GridSearchCV for hyperparameter tuning.
    *   Assessed performance using accuracy scores and confusion matrices.

## Files in this Repository

*   **`jupyter-labs-spacex-data-collection-api.ipynb`**: Data collection from SpaceX API.
*   **`jupyter-labs-webscraping.ipynb`**: Web scraping Falcon 9 launch data from Wikipedia.
*   **`labs-jupyter-spacex-Data wrangling.ipynb`**: Data cleaning and feature engineering.
*   **`jupyter-labs-eda-sql-coursera_sqllite.ipynb`**: EDA using SQL.
*   **`edadataviz.ipynb`**: EDA using visualization libraries (Matplotlib/Seaborn).
*   **`SpaceX_Machine Learning Prediction_Part_5.ipynb`**: Machine Learning model building and evaluation.
*   **`spacex_launch_dash.csv`** & **`spacex_dash_app.py`**: (If present) Dash application files.
*   **`dataset_part_2.csv`**, **`Spacex.csv`**: Computed datasets used for analysis.
*   **`ds-capstone-template-coursera.pptx`**: Final project presentation.

## Results
All classification models performed similarly with an accuracy of approximately **83.33%** on the test set. Exploratory analysis revealed that launch success rates have improved significantly over time and that certain orbits and launch sites have higher success probabilities.

## Technologies Used
*   **Python**: Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn
*   **APIs**: SpaceX REST API
*   **Web Scraping**: BeautifulSoup
*   **Visualization**: Folium, Plotly Dash
*   **Machine Learning**: Classification Algorithms

## Author
Adithya S M
