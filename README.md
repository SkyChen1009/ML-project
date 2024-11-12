# ML-project

### The repo contains scripts that implement the ML technique.

---
# Sales Prediction Pipeline

This project uses machine learning models to predict sales figures based on various features like store data, oil prices, holidays/events, and transactions. The pipeline consists of data preprocessing, feature engineering, and model training.

## Requirements

- Python 3.x
- Libraries: pandas, numpy, scikit-learn, xgboost

## Files

- `train.csv`: Training data with sales and related features.
- `test.csv`: Test data for predictions.
- `stores.csv`: Metadata about stores.
- `sample_submission.csv`: Template for submission format.
- `transactions.csv`: Data on store transactions.
- `oil.csv`: Daily oil prices.
- `holidays_events.csv`: Information on holidays and events.

## Data Processing Steps

1. **Data Loading**: Load datasets for training and testing.
2. **Data Merging**:
   - Merge `oil.csv` data on date for both training and testing sets, with missing values filled using the mean.
   - Merge `stores.csv` on store number, renaming `type` column to `store_type`.
   - Merge `holidays_events.csv` on date, filling missing values with defaults.
3. **Label Encoding**:
   - Encode categorical features like `date`, `family`, `city`, and `locale` using `LabelEncoder`.
4. **Feature Dropping**:
   - Remove unnecessary columns (`id`, `description`, `locale_name`) to reduce feature space.

## Model Training

1. **Train-Test Split**:
   - Split the training data into 80% train and 20% test for validation.

2. **Models**:
   - **Linear Regression**: Baseline model for initial predictions.
   - **Histogram-Based Gradient Boosting Regressor**: Enhanced model with 3000 iterations.
   - **XGBoost Regressor**: Final model with 400 estimators and max depth of 12, optimized for accuracy.

3. **Predictions**:
   - Predictions are made on the test set and stored in the `sample_submission.csv` format.

## Running the Pipeline

To run the code, load the datasets into the specified paths and execute each step in sequence.

## Output

- The final sales predictions are saved in `/content/sub.csv`, formatted for submission.
