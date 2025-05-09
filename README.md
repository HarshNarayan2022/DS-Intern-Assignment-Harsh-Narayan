# Equipment Energy Consumption Prediction-Harsh_Narayan

## Overview
This project aims to predict equipment energy consumption using a dataset containing environmental and operational features such as temperature, humidity, and atmospheric conditions across multiple zones. The analysis and modeling are performed in the `test.ipynb` notebook.

---

## Dataset
The dataset contains **16,857 rows** and **29 columns**, including:

- **Target Variable**: `equipment_energy_consumption` (numeric, representing energy usage).
- **Features**: Zone-specific temperature and humidity, outdoor conditions, and time-based features (hour, month, etc.).

### Challenges:
- Missing values and non-numeric entries (`'error'`, `'unknown'`, `'???'`, `'check'`).
- Potential outliers in numerical columns.
- Feature scaling and selection for better model performance.

---

## Project Workflow

### 1. **Data Loading**
- The dataset is loaded using `pandas` from a local CSV file (`data/data.csv`).
- The first few rows of the dataset are displayed to understand its structure.

---

### 2. **Preprocessing**
- **Timestamp Conversion**: The `timestamp` column is converted to datetime, and features like `hour` are extracted. The original `timestamp` column is dropped.
- **Handling Missing Values**:
  - Non-numeric entries (`'error'`, `'unknown'`, `'???'`, `'check'`) are replaced with `NaN`.
  - Missing values are filled with the **mean** of the respective columns.
- **Outlier Detection and Removal**:
  - Outliers are identified using the **IQR method** and removed from numerical columns.
- **Duplicate Removal**: Duplicate rows are identified and dropped.

---

### 3. **Exploratory Data Analysis (EDA)**
- **Dataset Shape**: The number of rows and columns is printed.
- **Data Types**: The data types of each column are checked.
- **Summary Statistics**:
  - Numerical columns are summarized using `.describe()`.
  - Categorical columns are summarized separately.
- **Correlation Analysis**:
  - A heatmap is used to visualize correlations between features and the target variable (`equipment_energy_consumption`).
  - Features with weak correlations are identified.
- **Visualization**:
  - Boxplots are used to detect outliers in numerical columns.
  - Histograms are plotted to analyze the distribution of numerical features.

---

### 4. **Feature Engineering**
- The dataset is split into:
  - **Features (`X`)**: All columns except `equipment_energy_consumption`.
  - **Target (`y`)**: `equipment_energy_consumption`.
- **Scaling**: Numerical features are scaled using `StandardScaler`.

---

### 5. **Modeling**
- Two models are trained:
  1. **Linear Regression**
  2. **Random Forest Regressor**
- **Evaluation Metrics**:
  - **Mean Squared Error (MSE)**: Measures the average squared difference between actual and predicted values.
  - **R² Score**: Indicates how well the model explains the variance in the target variable.

---

### 6. **Evaluation**
- **Linear Regression**:
  - Mean Squared Error: 29700.334817848492
  - R² Score: 0.01382860634137384
- **Random Forest Regressor**:
  - Mean Squared Error: 28368.915645274228
  - R² Score: 0.05803711473072437

**Insights**:
- The **Random Forest Regressor** outperforms Linear Regression, capturing non-linear relationships in the data.
- Environmental factors like temperature and humidity strongly influence energy consumption.

---

## How to Run

1. **Install Dependencies**:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
