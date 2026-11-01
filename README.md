# Student Performance Prediction Using Regression

## 1. Project Overview

This project explores the use of regression techniques to predict students' examination scores based on different academic and personal factors.

The main objective is to understand how selected features influence students' exam performance and compare the performance of Linear Regression and Polynomial Regression models.

The project also explores how changing the feature set affects model performance.

## 2. Dataset Description

The project uses the **Student Performance Factors** dataset, containing 6,607 student records and 20 columns.

The dataset includes information such as:

- Hours studied
- Attendance
- Sleep hours
- Previous examination scores
- Tutoring sessions
- Access to learning resources
- Parental involvement
- Family income
- Teacher quality
- Physical activity

**Target variable:** `Exam_Score`

The target variable represents the examination score the models aim to predict.

## 3. Tools and Libraries

The following Python libraries were used:

| Library | Purpose |
|---|---|
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Correlation heatmap |
| Scikit-learn | Model training, preprocessing and evaluation |

## 4. Data Exploration and Analysis

The initial exploration involved:

- Inspecting the first ten records.
- Checking the dataset's structure and data types.
- Identifying missing values.
- Examining unique values in each column.
- Generating descriptive statistics.
- Visualizing correlations between numerical features using a heatmap.

The dataset contained missing values in `Teacher_Quality`, `Parental_Education_Level` and `Distance_from_Home`.

These columns were not included in the original model, so no imputation was performed for them.

The correlation heatmap helped identify numerical features with relationships to the target variable.

## 5. Data Preprocessing and Feature Selection

### Original Linear Regression

Five initial features were selected:

1. `Hours_Studied`
2. `Access_to_Resources`
3. `Attendance`
4. `Tutoring_Sessions`
5. `Previous_Scores`

The selection was guided by the correlation analysis and the intention to investigate the influence of both numerical and categorical factors on examination scores.

### Encoding Categorical Features

Since Linear Regression requires numerical inputs, `Access_to_Resources` was converted into numerical features using One-Hot Encoding.

The original categories were:

- Low
- Medium
- High

The encoder used `drop='first'`, making High the reference category.

This produced two new columns:

- `Access_to_Resources_Low`
- `Access_to_Resources_Medium`

The original categorical column was then removed.

The resulting feature set contained six numerical columns.

### Train-Test Split

The dataset was divided into training and testing sets using an 80:20 ratio.

- Training samples: 5,285
- Testing samples: 1,322
- Random state: 42

## 6. Linear Regression Model

The first model was trained using Scikit-learn's `LinearRegression()` algorithm.

The model learned relationships between the selected features and students' examination scores.

After training, predictions were generated using the testing dataset.

Actual and predicted examination scores were compared using a comparison table. A scatter plot was also created to visualize the relationship between actual and predicted scores.

### Linear Regression Evaluation

| Evaluation Metric | Result |
|---|---:|
| Mean Squared Error (MSE) | 4.590 |
| Root Mean Squared Error (RMSE) | 2.142 |
| Mean Absolute Error (MAE) | 1.119 |
| R² Score | 0.6753 |

**Interpretation:**

- The MAE of approximately 1.12 indicates that the model's predictions differed from actual examination scores by about 1.12 marks on average.
- The RMSE of approximately 2.14 indicates the typical prediction error, with greater penalties for larger errors.
- The R² score of 0.6753 indicates that approximately 67.53% of the variation in examination scores was explained by the model on the test set.

## 7. Polynomial Regression

The second experiment involved Polynomial Regression.

The purpose was to investigate whether introducing polynomial features could improve the model's ability to capture relationships between the selected features and examination scores.

### Feature Selection

A different set of six numerical features was selected:

1. `Hours_Studied`
2. `Attendance`
3. `Sleep_Hours`
4. `Previous_Scores`
5. `Tutoring_Sessions`
6. `Physical_Activity`

Unlike the original model, this experiment focused on numerical features, including some that were not part of the initial feature set.

### Creating Polynomial Features

Scikit-learn's `PolynomialFeatures` was used with:

- Degree: 2
- Include bias: False

This generated additional features representing squared terms and interactions between the original features.

The transformed training data was used to train another Linear Regression estimator.

The trained model then generated predictions on the transformed testing data.

### Polynomial Regression Evaluation

| Evaluation Metric | Result |
|---|---:|
| MSE | 5.101 |
| RMSE | 2.258 |
| MAE | 1.273 |
| R² Score | 0.6392 |

**Interpretation:**

The Polynomial Regression model produced an R² score of approximately 0.6392, meaning it explained about 63.92% of the variation in examination scores on the test set.

Its error metrics were also slightly higher than those of the original Linear Regression model.

## 8. Model Comparison

The results from both experiments are presented below.

| Metric | Linear Regression | Polynomial Regression |
|---|---:|---:|
| MSE | 4.590 | 5.101 |
| RMSE | 2.142 | 2.258 |
| MAE | 1.119 | 1.273 |
| R² | 0.6753 | 0.6392 |

The original Linear Regression model performed better across all four evaluation metrics.

It recorded lower error values and a higher R² score.

This suggests that introducing polynomial features did not improve the results in this experiment.

However, the two models used different feature sets, so the comparison does not isolate the effect of polynomial transformation alone.

## 9. Conclusion

This project explored how different student-related factors could be used to predict examination scores through regression techniques.

The original Linear Regression model achieved an R² score of 0.6753, an MAE of 1.119 and an RMSE of 2.142.

The Polynomial Regression experiment achieved an R² score of 0.6392, an MAE of 1.273 and an RMSE of 2.258.

Based on these results, the original Linear Regression model performed better in this experiment.

The following questions guided the feature selection and experimentation process:

**1. Which features were retained in the original model?**

Hours_Studied, Access_to_Resources, Attendance, Tutoring_Sessions and Previous_Scores were selected. The selection was guided by the correlation analysis and the intention to investigate both numerical and categorical factors.

**2. Why was Access_to_Resources included?**

Access_to_Resources was included to investigate how a categorical factor relating to students' learning environment could contribute to predicting examination scores. It was converted into numerical features through One-Hot Encoding.

**3. Why was the feature set changed for the second experiment?**

The feature set was changed to investigate how a different combination of numerical features, including less strongly correlated features, would affect model performance.

Overall, the experiment demonstrated that increasing model complexity through polynomial feature generation does not necessarily guarantee better predictive performance.

## 10. Future Improvements

Some possible improvements to explore include:

- Comparing both regression models using the same feature set.
- Experimenting with different polynomial degrees.
- Investigating additional feature selection techniques.
- Exploring other regression algorithms.
- Using cross-validation to evaluate model consistency.
- Investigating the effect of individual features on prediction performance.

## 11. Installation and Requirements

To run this project locally, Python and the following libraries are required:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- jupyter

Install the required libraries using pip:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

## 12. How to Run the Project

1. Clone this repository:

```bash
git clone YOUR_REPOSITORY_URL
```

2. Navigate into the project directory:

```bash
cd Student-Performance-Prediction
```

3. Install the required libraries using the installation command above.

4. Launch Jupyter Notebook:

```bash
jupyter notebook
```

5. Open `Student_performance_model.ipynb` and run the cells sequentially.

Ensure that the dataset CSV file is in the same directory as the notebook.

## 13. Project Structure

```text
Student-Performance-Prediction/
│
├── README.md
├── Student_performance_model.ipynb
└── StudentPerformanceFactors.csv
```

| File | Description |
|---|---|
| README.md | Project documentation |
| Student_performance_model.ipynb | Notebook containing data analysis, preprocessing, model training and evaluation |
| StudentPerformanceFactors.csv | Dataset used for the project |
