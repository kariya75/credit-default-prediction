# Credit Default Prediction

Machine Learning project focused on predicting customer credit default using a large-scale credit history dataset.

---

## Project Goal

The objective of this project is to predict whether a customer will default on a loan based on information about their credit products and payment history.

The target variable is binary (default / non-default).

---

## Data

The original dataset consists of:

* 12 Parquet files
* 26 million records
* 61 original features

Each record represents a credit product belonging to a customer. Customers may have multiple credit products with different life cycles and payment histories.

The dataset contains information about:

* credit product timelines and durations
* credit limits and outstanding balances
* current and historical overdue payments
* payment behavior
* credit statuses and product types
* utilization and overdue ratios
* account and currency information

### Dataset Characteristics

The dataset was heavily preprocessed before the project:

* numerical features were aggressively binarized into discrete buckets
* categorical features were encoded into numerical categories with limited semantic interpretability
* many original feature values and meanings were no longer directly accessible
* missing values and major outliers had already been handled
* features were generally safe from data leakage

As a result, traditional feature analysis became significantly more difficult. For many variables, values represented encoded categories rather than meaningful business entities. For example, credit types were stored as numerical codes instead of interpretable labels such as mortgage, consumer loan, or insurance product.

The main challenge of the project was extracting predictive signal from highly transformed data while having limited access to the original business meaning of many features.

---

## Work Performed

* Built a large-scale data processing pipeline
* Merged 12 source files into a unified dataset
* Aggregated multiple credit products at the customer level
* Generated custom engineered features
* Constructed a final dataset of approximately:

  * 3 million customers
  * 160 features
* Performed dozens of experiments with CatBoost
* Built an ensemble based on:

  * CatBoost
  * LightGBM
  * XGBoost
* Applied class weighting and cross-validation
* Conducted extensive model error analysis
* Generated new hypotheses and features based on observed prediction errors
* Repeated the feature engineering and evaluation cycle through multiple project iterations

---

## Technologies Used

* Python
* pandas
* numpy
* dask
* matplotlib
* seaborn
* scikit-learn
* CatBoost
* LightGBM
* XGBoost
* joblib

---

## Results

Final ensemble:

* CatBoost
* XGBoost

**Final ROC-AUC: ~0.742**

After numerous feature engineering iterations and model improvements, the project reached a performance plateau where additional experiments produced only marginal gains.

---

## What I Learned

This project taught me how to work with data that is difficult to interpret and analyze directly.

Because feature values had already been heavily transformed, improving model quality required focusing on:

* model error analysis
* iterative hypothesis testing
* feature engineering driven by observed model behavior

The project also provided extensive experience working with large datasets, long experimentation cycles, and ensemble methods.

---

## Project Structure

Files:

* README.md
* credit_scoring.ipynb — main notebook containing data aggregation, feature engineering, experiments, and results
* original_features.pdf — detailed description of original dataset features

