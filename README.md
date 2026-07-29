# Stroke Prediction R Project
## Data Science Project



An end-to-end data science and machine learning project developed in **R** to explore a real-world healthcare dataset and predict whether a person is likely to experience a stroke based on demographic, lifestyle, and medical information.

The project covers the complete workflow: data collection, data cleaning, exploratory data analysis, visualization, preprocessing, feature engineering, model building, evaluation, comparison, and interpretation.

## Live Project Website

View the complete rendered report with code, outputs, tables, and graphs:

**https://fuad7181.github.io/Stroke-Prediction-R-Project/**

## Project Information

| Item | Description |
|---|---|
| Project Title | Stroke Prediction R Project |
| Group | Group-3 |
| Task Type | Binary Classification |
| Target Variable | `stroke` |
| Programming Language | R |
| Report Format | R Markdown, HTML, and Jupyter Notebook |
| Original Report Date | April 20, 2026 |
| Random Seed | 123 |

## Project Objectives

The main objectives of this project are to:

- Explore the demographic, medical, and lifestyle features in the stroke dataset.
- identify missing values, duplicate records, skewness, correlations, and outliers.
- Visualize the distributions and relationships among important variables.
- Prepare the data for machine learning through cleaning, encoding, scaling, and feature engineering.
- Build Logistic Regression and Decision Tree classification models.
- Compare model performance using accuracy, precision, recall, and F1-score.
- Examine the effect of lowering the Logistic Regression classification threshold from `0.50` to `0.30`.
- Understand why accuracy alone can be misleading for an imbalanced dataset.

## Dataset

The project uses a real-world stroke prediction dataset containing medical history, lifestyle, and demographic information.

**Dataset link:**  
https://drive.google.com/uc?id=1PsCqVI9lfaZyrsc8JOhMzq5vzesBtDkh

### Dataset Summary

| Property | Value |
|---|---:|
| Total observations | 5,110 |
| Original variables | 12 |
| Missing BMI values | 201 |
| Duplicate rows | 0 |
| Non-stroke records | 4,861 |
| Stroke records | 249 |
| Non-stroke percentage | 95.13% |
| Stroke percentage | 4.87% |

The target distribution shows a strong **class imbalance**, because stroke cases represent only about 4.87% of the dataset.

## Dataset Features

| Feature | Description |
|---|---|
| `id` | Unique patient identifier; removed before model training |
| `gender` | Patient gender |
| `age` | Patient age |
| `hypertension` | Whether the patient has hypertension |
| `heart_disease` | Whether the patient has heart disease |
| `ever_married` | Whether the patient has ever been married |
| `work_type` | Type of employment |
| `Residence_type` | Urban or rural residence |
| `avg_glucose_level` | Average blood glucose level |
| `bmi` | Body mass index |
| `smoking_status` | Smoking history or status |
| `stroke` | Target variable: stroke or no stroke |

## Tools and R Packages

The following R packages are used:

| Package | Purpose |
|---|---|
| `readr` | Loading the dataset |
| `ggplot2` | Data visualization |
| `corrplot` | Correlation heatmaps |
| `moments` | Skewness calculation |
| `caret` | Data splitting, preprocessing, and model evaluation |
| `GGally` | Pair plots |
| `rpart` | Decision Tree classification |

## Project Workflow

### 1. Data Collection and Loading

The dataset is loaded directly from a Google Drive URL using `read_csv()`. Different missing-value formats, including `NA`, `N/A`, empty strings, and `NULL`, are treated as missing values.

### 2. Data Inspection

The project examines:

- Dataset dimensions
- Variable types
- Numerical and categorical features
- Missing values
- Duplicate rows
- Descriptive statistics
- Mean, median, standard deviation, variance, minimum, maximum, and quartiles

### 3. Exploratory Data Analysis

Exploratory analysis includes:

- Numerical feature distributions
- Categorical frequency tables
- Correlation analysis
- Pair plots
- Univariate analysis
- Bivariate analysis
- Categorical analysis
- Stroke-class distribution analysis

### 4. Data Visualizations

The rendered report and graph-enabled notebook contain **25 graphs**, including:

- Correlation heatmaps
- Age histogram
- Average glucose histogram
- BMI histogram
- Gender distribution
- Work-type distribution
- Smoking-status distribution
- Stroke-class distribution
- Pair plots
- Age versus glucose scatter plot
- Age-by-stroke boxplot
- BMI-by-stroke boxplot
- Glucose-by-stroke boxplot
- Stroke cases by gender
- Stroke cases by work type
- Stroke cases by smoking status
- Gender pie chart
- Stroke pie chart
- Decision Tree plot
- Model comparison charts
- Confusion-matrix heatmaps

## Important Exploratory Findings

The average values of important numerical variables differ between the stroke and non-stroke groups:

| Group | Average Age | Average BMI | Average Glucose |
|---|---:|---:|---:|
| No Stroke | 41.76 | 28.82 | 104.00 |
| Stroke | 67.71 | 30.47 | 134.57 |

The analysis indicates that:

- Stroke cases are more common among older patients.
- The stroke group has a higher average glucose level.
- The stroke group also has a slightly higher average BMI.
- Age has an important positive relationship with stroke.
- The severe class imbalance must be considered when evaluating the models.

## Data Preprocessing

The following preprocessing steps are applied:

1. Convert `age`, `avg_glucose_level`, `bmi`, and `stroke` to numerical formats.
2. Convert different missing-value representations into proper `NA` values.
3. Replace 201 missing BMI values using median imputation.
4. Detect BMI outliers using the IQR method.
5. Cap values below and above the IQR boundaries.
6. Encode categorical variables into numerical codes.
7. Remove the `id` column because it does not contribute to prediction.
8. Split the data into training and testing sets.
9. Scale numerical predictors after splitting to avoid data leakage.

## Feature Engineering

Two additional features are created:

### Age Group

| Category | Age Range |
|---|---|
| Young | Up to 30 |
| Middle-Aged | Above 30 to 40 |
| Older | Above 40 to 50 |
| Senior | Above 50 to 60 |
| Elder | Above 60 |

### BMI Category

| Category | BMI Range |
|---|---|
| Underweight | Below 18.5 |
| Normal | 18.5–24.9 |
| Overweight | 25.0–29.9 |
| Obese | 30.0 or above |

## Train-Test Split

The dataset is divided using a stratified 80–20 split:

| Dataset | Rows | Columns after feature engineering |
|---|---:|---:|
| Training set | 4,089 | 13 |
| Testing set | 1,021 | 13 |

Scaling parameters are calculated only from the training data and then applied to both training and testing data.

## Machine Learning Models

### Logistic Regression

Logistic Regression is used as the baseline model because the target variable contains two classes:

- `No_Stroke`
- `Stroke`

Two probability thresholds are evaluated:

- Standard threshold: `0.50`
- Lower threshold: `0.30`

The lower threshold is tested to increase the model's sensitivity to the minority stroke class.

### Decision Tree

A Decision Tree classifier is also trained to capture rule-based and non-linear relationships.

Pre-pruning settings include:

- Complexity parameter: `0.001`
- Minimum split size: `10`
- Minimum terminal-node size: `5`
- Maximum tree depth: `5`

## Evaluation Metrics

The models are evaluated using:

- **Accuracy:** Overall percentage of correct predictions
- **Precision:** Proportion of predicted stroke cases that are correct
- **Recall:** Proportion of actual stroke cases correctly detected
- **F1-score:** Harmonic mean of precision and recall
- **Confusion matrix:** Counts of correct and incorrect classifications

For stroke prediction, recall and F1-score are especially important because missing an actual stroke case is more meaningful than correctly identifying the already dominant non-stroke class.

## Model Results

| Model | Accuracy | Precision | Recall | F1-score |
|---|---:|---:|---:|---:|
| Logistic Regression — 0.50 threshold | 0.9520 | 0.0000 | 0.0000 | 0.0000 |
| Logistic Regression — 0.30 threshold | 0.9491 | 0.2857 | 0.0408 | 0.0714 |
| Decision Tree | 0.9520 | 0.0000 | 0.0000 | 0.0000 |

## Result Interpretation

The Logistic Regression model with a `0.50` threshold and the Decision Tree both produce high accuracy, but they fail to detect the minority stroke class in the test data.

The Logistic Regression model with a `0.30` threshold produces slightly lower accuracy but identifies some stroke cases:

- Precision increases to approximately 28.57%.
- Recall increases to approximately 4.08%.
- F1-score increases to approximately 7.14%.

These results demonstrate that high accuracy can be misleading when the target classes are highly imbalanced. The lower threshold improves minority-class detection, but the recall remains low.

In the Logistic Regression coefficient analysis, age and average glucose level show statistically important positive associations with the stroke outcome in the fitted model.

## Key Conclusion

The project successfully follows the complete data science lifecycle:

1. Data collection
2. Data inspection
3. Data cleaning
4. Exploratory data analysis
5. Visualization
6. Missing-value handling
7. Outlier treatment
8. Feature engineering
9. Categorical encoding
10. Feature selection
11. Train-test splitting
12. Data scaling
13. Model building
14. Model evaluation
15. Model comparison
16. Result interpretation

The project shows that model selection and evaluation must consider the class distribution. In this dataset, accuracy alone does not represent the model's ability to detect stroke cases. Precision, recall, F1-score, and the confusion matrix provide a more meaningful interpretation.

## Limitations

- The stroke class represents only about 4.87% of the dataset.
- The evaluated models have very low recall for stroke cases.
- Categorical variables are encoded as numeric factor codes rather than one-hot encoded variables.
- Only Logistic Regression and Decision Tree are compared.
- The standard models do not use class weights, oversampling, undersampling, or SMOTE.
- The current model should be considered an academic demonstration rather than a clinical diagnostic system.

## Possible Future Improvements

Future work may include:

- Applying class-weighted models
- Using SMOTE or other resampling methods
- Trying Random Forest, XGBoost, Support Vector Machine, or other classifiers
- Performing cross-validation and hyperparameter tuning
- Evaluating ROC-AUC and Precision-Recall AUC
- Selecting a classification threshold based on validation data
- Using one-hot encoding for nominal categorical variables
- Deploying an interactive prediction application

## Repository Files

```text
Stroke-Prediction-R-Project/
├── README.md
├── H-G03-FINAL-PROJECT.rmd
├── index.html
└── Stroke Prediction R Project.ipynb
```

| File | Description |
|---|---|
| `README.md` | Complete project overview and documentation |
| `H-G03-FINAL-PROJECT.rmd` | Original R Markdown source code |
| `index.html` | Rendered report used by GitHub Pages |
| `Stroke Prediction R Project.ipynb` | R Jupyter Notebook with code and 25 embedded graphs |

## How to View the Project

### Website

Open:

https://fuad7181.github.io/Stroke-Prediction-R-Project/

### HTML File

The `index.html` file is the website entry page. Inside the GitHub repository, clicking it directly displays its source code. Use the GitHub Pages link to view it as a rendered website.

### Jupyter Notebook

Open `Stroke Prediction R Project.ipynb` in GitHub to view the code and embedded graphs.

To execute the notebook locally, Jupyter Notebook and an R kernel such as IRkernel are required.

## How to Run the R Markdown File

1. Install R and RStudio.
2. Download or clone this repository.
3. Open `H-G03-FINAL-PROJECT.rmd` in RStudio.
4. Make sure the computer has an internet connection because the dataset is loaded from Google Drive.
5. Click **Knit** to generate the HTML report.

The script automatically installs missing R packages before loading them.

## Clone the Repository

```bash
git clone https://github.com/fuad7181/Stroke-Prediction-R-Project.git
cd Stroke-Prediction-R-Project
```

## Author

**Md. Fuad Abdullah, Mashfika Tabassum Tisha, Nazat E Rose, Sumaiya Habiba**

## Disclaimer

This project was created for academic and educational purposes. Its results should not be used as a substitute for professional medical diagnosis or clinical decision-making.

