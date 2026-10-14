# Practical 06 — Remembering Every Experiment

## 1. Aim

To understand and implement experiment tracking using MLflow. The practical
focuses on logging machine learning experiments, tracking parameters and
metrics, comparing model performance, filtering runs, and identifying the
best-performing model.

## 2. Objectives

- Understand the fundamentals of MLflow.
- Track machine learning experiments and runs.
- Log model parameters and evaluation metrics.
- Compare the performance of different models.
- Filter experiment runs using tags.
- Identify the best model based on Mean Absolute Error (MAE).
- Understand how experiment tracking improves reproducibility.

## 3. Tools and Technologies

- Python
- Jupyter Notebook
- MLflow
- Scikit-learn
- Pandas
- NumPy
- SQLite
- Matplotlib

## 4. Dataset

The practical uses a delivery-time dataset containing information for
predicting delivery time.

The dataset is generated or loaded by the provided notebook and is stored
at:

`../data/delivery_times.csv`

The dataset is divided into training and testing sets.

- Training data: Used to train machine learning models.
- Testing data: Used to evaluate model performance.

## 5. Implementation

### Task 1: Track a Different Kind of Model

A Linear Regression model was trained using the training dataset.

The experiment was logged in MLflow with the run name:

`linear-baseline`

The following information was recorded:

- Model type: LinearRegression
- Evaluation metric: mae_minutes
- Run ID: Stored in `T1_run_id`

The model's Mean Absolute Error (MAE) was calculated using the test dataset.

### Task 2: Find the Best Experiment

The `mlflow.search_runs()` function was used to retrieve experiment runs
from the `delivery-time` experiment.

The runs were sorted in ascending order of `mae_minutes`.

The run with the lowest MAE was selected as the best-performing experiment.

The following variables were recorded:

- `T2_best_name`: Name of the best run.
- `T2_best_mae`: MAE of the best run.

A lower MAE indicates a smaller average absolute prediction error.

### Task 3: Decision Tree Experiment Sweep

A small experiment sweep was performed using
`DecisionTreeRegressor`.

Three models were trained with different maximum depths:

- Depth = 2
- Depth = 4
- Depth = 6

Each run logged the following information:

- Parameter: `max_depth`
- Metric: `mae_minutes`
- Tag: `family=tree`

The `mlflow.search_runs()` function was then used with a tag filter
to retrieve the Decision Tree experiments.

The total number of matching runs was stored in:

`T3_tree_runs`

Expected count: 3, provided all three runs complete successfully.

## 6. MLflow Experiment Tracking

MLflow was used to maintain a record of machine learning experiments.

The recorded information includes:

- Run names
- Model parameters
- Evaluation metrics
- Experiment tags
- Run IDs

The experiment data was stored using an SQLite backend database.

The MLflow Tracking UI can be used to inspect runs, compare metrics,
and review experiment results.

## 7. Evaluation Metric

### Mean Absolute Error (MAE)

Mean Absolute Error measures the average absolute difference between
actual and predicted values.

Formula:

MAE = (1/n) * Σ |y_actual - y_predicted|

Where:

- n = Number of test samples
- y_actual = Actual delivery time
- y_predicted = Predicted delivery time

A lower MAE indicates better predictive performance on the evaluated
test dataset.

## 8. How to Run the Project

1. Open the project folder in VS Code.
2. Activate the Python virtual environment.
3. Open `P06.ipynb` in Jupyter Notebook or JupyterLab.
4. Execute the notebook's setup and training cells in order.
5. Complete and execute Tasks T1, T2, and T3.
6. Execute the self-check cell.
7. Review the recorded experiment results.

### Start the MLflow Tracking UI

Run the following command in PowerShell from the `P06-mlflow` directory:

```powershell
..\.venv\Scripts\python.exe -m mlflow ui --backend-store-uri "sqlite:///C:/MLOps/P06-mlflow/work/mlflow.db" --port 5000
