# Spaceship Titanic - Machine Learning Classification Project

This repository contains a comprehensive machine learning project focused on predicting passenger transport status using the **Spaceship Titanic** dataset. The project involves extensive data preprocessing, feature engineering, and a performance comparison across multiple classification algorithms.

## Project Implementation
The goal was to build a predictive model to determine which passengers were transported to an alternate dimension during the voyage of the Spaceship Titanic.

The implementation follows a standard machine learning pipeline:
* **Data Preparation**: Splitting the raw dataset into training (80%) and test (20%) sets using randomized shuffling.
* **Preprocessing**: Handling missing values, encoding categorical variables, and engineering new features.
* **Model Selection**: Testing and optimizing nine different classification algorithms.
* **Hyperparameter Tuning**: Utilizing Cross-Validation to identify optimal settings for each model.
* **Feature Importance Analysis**: Analyzing which passenger attributes most significantly impacted the prediction results for each model.

## Data
The original dataset consisted of 8,693 entries with 14 features. Each row represents an individual passenger with the following key attributes:
* **PassengerId**: A unique ID for each traveler.
* **HomePlanet & Destination**: The planet of origin and the planned destination.
* **CryoSleep**: Indicates if the passenger was in suspended animation.
* **Cabin**: The cabin location (Deck/Number/Side).
* **Age**: Passenger age.
* **Luxury Amenities**: Spending records for Room Service, Food Court, Shopping Mall, Spa, and VR Deck.
* **Transported**: The target label (True/False).

### Improve DATA
To ensure high model performance, the data underwent significant refinement:
* **Cleaning & Filtering**: Unique identifiers like names and IDs were dropped as they do not affect prediction.
* **Imputing Missing Values**:
    * **Age**: Missing values were filled with the mean age of all passengers.
    * **Cabin & Destination**: Missing entries were filled based on group associations. If no group data was available, the row was removed.
* **Encoding**: Categorical strings and Boolean values were converted to integers to allow algorithm processing.
* **Feature Engineering**:
    * **Cabin Decomposition**: Split the single `Cabin` string into three distinct features: **Deck**, **Number**, and **Side**.
    * **Travel Groups**: Created a `TravelGroupType` feature to categorize passengers as solo travelers, group travelers, or family travelers.

## Model Performance
The following table summarizes the optimized accuracy scores and characteristics for the implemented classifiers:

| Model | Accuracy | Key Advantages |
| :--- | :---: | :--- |
| **Random Forest** | **80.3%** | Most stable, reduces overfitting, handles non-linear data. |
| **xgboost** | **79.9%** | Powerful performance through incremental improvements. |
| **KNN** | **78.6%** | Simple and effective for non-linear problems. |
| **Logistic Regression** | **78.3%** | Stable and probability-based. |
| **SVM** | **77.4%** | Effective for complex separations. |
| **Decision Tree** | **77.2%** | Fast and easy to interpret. |
| **LDA** | **76.9%** | Fast and stable for linear data. |
| **QDA** | **71.9%** | Good for specific Gaussian distributions. |
| **GNB** | **71.2%** | Extremely fast and simple. |

## Conclusion
The **Random Forest Classifier** emerged as the optimal model for this project with an accuracy of **80.3%**. This success is due to several factors:
1.  **Complexity Handling**: Its ability to handle large datasets and complex, non-linear relationships between variables.
2.  **Overfitting Mitigation**: By combining the results of multiple decision trees, the model remains stable and avoids over-relying on individual data quirks.
3.  **Feature Selection**: The model successfully prioritized significant features—specifically spending on **Spa**, **VRDeck**, and **RoomService**—while minimizing the impact of irrelevant data.
