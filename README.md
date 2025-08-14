# DATA-PIPELINE-DEVELOPMENT

COMPANY        :   CODTECH IT SOLUTIONS

NAME           :   RAMACHANDRAN K

INTERN ID      :   CT04DH2787

DOMAIN         :   DATA SCIENCE

DURATION       :   4 WEEEKS

MENTOR         :   NEELA SANTOSH

# Titanic Dataset ETL Pipeline

## 📌 Overview
This project demonstrates how to create an **end-to-end ETL (Extract, Transform, Load) pipeline** for the Titanic dataset using:
- **Seaborn** – to load the built-in Titanic dataset.
- **Pandas** – for data handling and cleaning.
- **Scikit-Learn** – for building preprocessing pipelines to automate encoding, scaling, and missing value handling.

The ETL pipeline takes raw Titanic passenger data, cleans and transforms it, and produces a version of the dataset that is consistent, fully numeric, and ready for **machine learning models**.

This workflow is entirely **automated** and **Google Colab friendly** — no need to download datasets manually.

---

## 📂 Dataset Details
- **Source**: Built into Seaborn (`sns.load_dataset('titanic')`).
- **Description**:
  - Represents passengers aboard the RMS Titanic.
  - Includes demographic, ticket, and survival details.
  - Features both **numerical** (e.g., `age`, `fare`) and **categorical** (e.g., `sex`, `embarked`) variables.
  - Contains missing values in several columns.
- **Target Variable**: `survived`
  - `0` → Did not survive  
  - `1` → Survived

---

## 🔄 ETL Process
# Titanic Dataset ETL Pipeline

## 📌 Overview
This project demonstrates how to create an **end-to-end ETL (Extract, Transform, Load) pipeline** for the Titanic dataset using:
- **Seaborn** – to load the built-in Titanic dataset.
- **Pandas** – for data handling and cleaning.
- **Scikit-Learn** – for building preprocessing pipelines to automate encoding, scaling, and missing value handling.

The ETL pipeline takes raw Titanic passenger data, cleans and transforms it, and produces a version of the dataset that is consistent, fully numeric, and ready for **machine learning models**.

This workflow is entirely **automated** and **Google Colab friendly** — no need to download datasets manually.

---

## 📂 Dataset Details
- **Source**: Built into Seaborn (`sns.load_dataset('titanic')`).
- **Description**:
  - Represents passengers aboard the RMS Titanic.
  - Includes demographic, ticket, and survival details.
  - Features both **numerical** (e.g., `age`, `fare`) and **categorical** (e.g., `sex`, `embarked`) variables.
  - Contains missing values in several columns.
- **Target Variable**: `survived`
  - `0` → Did not survive  
  - `1` → Survived

---

## 🔄 ETL Process

### **1️⃣ Extract**
- Load Titanic dataset directly from Seaborn:
df = sns.load_dataset('titanic')

- Print initial shape and view the first few rows for inspection.

---

### **2️⃣ Transform**
The transformation step prepares the dataset for modeling by handling:

#### **Data Cleaning**
- Remove rows where `survived` (target) is missing.
- Drop irrelevant or high-missing-value columns: `deck`, `embark_town`, `alive`.

#### **Feature Separation**
- `X` – Features (independent variables).  
- `y` – Target (`survived`).

#### **Column Type Identification**
- Automatically detect **numeric** columns (`int`, `float`, `bool`).
- Automatically detect **categorical** columns (`object`, `category`).

#### **Preprocessing Steps**
- **Numeric pipeline**:
1. Median imputation (replace missing numbers with median).
2. Standard scaling (mean=0, variance=1).
- **Categorical pipeline**:
1. Most frequent imputation (replace missing categories with most common value).
2. One-Hot Encoding (create binary columns for categories).

These transformations are applied using:
- `Pipeline` → Sequences multiple processing steps.
- `ColumnTransformer` → Applies different transformations to numeric and categorical features in parallel.

---

### **3️⃣ Load**
- Split data into **80% training** and **20% testing** with:
train_test_split(X, y, test_size=0.2, random_state=42)
- Fit preprocessing pipeline on **training set** only.
- Transform both training and test sets.

**Final Output Shapes** after preprocessing:  
- Training set: **(712, 18)**  
- Test set: **(179, 18)**

The number of columns increases because **categorical variables expand into multiple binary columns** after one-hot encoding.

---

## 💡 Key Insights
1. **Automation ensures consistency** between training and test preprocessing.
2. **Handling missing data systematically** prevents errors during modeling.
3. **One pipeline works for different datasets** without rewriting transformation code.
4. **Automatic column detection** removes the need to hardcode feature lists.
5. Google Colab compatibility means no dataset download/setup required.

---

## ▶ How to Run

### **On Google Colab**
1. Open [Google Colab](https://colab.research.google.com/).
2. Install dependencies (if needed):
pip install pandas seaborn scikit-learn
3. Copy-paste the pipeline code into a notebook cell.
4. Run all cells to view:
- Original dataset shape
- Train/test shapes after transformation
- Sample processed feature table

### **Locally**
1. Install Python 3.8+  
2. Install dependencies:
pip install pandas seaborn scikit-learn
3. Save code as `titanic_etl_pipeline.py`
4. Run:
python titanic_etl_pipeline.py

---

## 📦 Requirements
- Python >= 3.8  
- Pandas >= 1.2  
- Seaborn >= 0.11  
- Scikit-Learn >= 1.0  

---

## 🚀 Possible Extensions
- Add machine learning models (e.g., Logistic Regression, Random Forest) after preprocessing.
- Save processed data to CSV or Parquet for reuse.
- Add feature engineering (e.g., age categories, fare bins).
- Integrate into a full ML Ops workflow with automated retraining.

---

## 📜 License
For educational use. Can be reused for personal or academic projects.
