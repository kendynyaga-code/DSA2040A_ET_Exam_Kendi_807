# 🧠 DSA 2040A – ETL Pipeline Project  
---

## 1️⃣ Project Overview  

This project demonstrates the **ETL (Extract, Transform, Load)** process using a synthetic student exam dataset.  
The main goal was to design a working data pipeline that takes raw exam records and processes them into clean, validated, and enriched data ready for storage or analysis.  

The project is split into two main Jupyter notebooks:
- `etl_extract.ipynb` – Generates and validates raw data  
- `etl_transform.ipynb` – Cleans, enriches, and standardizes the data  

By the end of the workflow, two clean CSV files (`transformed_full.csv` and `transformed_incremental.csv`) are produced — representing ready-to-analyze student performance data.

---

## 2️⃣ Data Source  

**Dataset:** Synthetic student exam records generated using Python’s [`Faker`](https://faker.readthedocs.io/en/master/) library.  

**Description:**  
The dataset simulates real-world student exam data, containing details such as:
- Student demographics (ID, gender, age, region)  
- Academic info (subject, grade level, school)  
- Performance metrics (exam score, date, and pass/fail outcome)  

**Files generated:**  
| File | Description |
|------|--------------|
| `raw_data.csv` | Main dataset containing 8,000 records |
| `incremental_data.csv` | Additional 1,000 records simulating new incoming data |
| `validated_full.csv` | Cleaned + validated merged dataset |
| `validated_incremental.csv` | Cleaned incremental data for testing transformations |

📁 **Location:** `/data` folder inside the main project directory.  

---

## 3️⃣ ET Phases  

### **🔹 Extract Phase**
Notebook: `etl_extract.ipynb`  
**Goal:** Generate, validate, and prepare raw exam data for transformation.  

**Key Steps:**
1. Generated random but realistic data using the `Faker` library.  
2. Created separate `raw` and `incremental` datasets.  
3. Validated data structure — checked column data types, missing values, and duplicates.  
4. Saved validated data into the `/data` folder.  

**Outputs:**
- `validated_full.csv`  
- `validated_incremental.csv`

---

### **🔹 Transform Phase**
Notebook: `etl_transform.ipynb`  
**Goal:** Clean, standardize, and enrich the validated data for analytics.  

**Key Transformations:**
| Step | Transformation | Description |
|------|----------------|-------------|
| 1 | Handle Missing Values | Filled missing regions/schools with "Unknown". |
| 2 | Standardize Text | Converted text fields (gender, subject, region) to Title Case. |
| 3 | Data Type Conversion | Changed `exam_date` to a proper datetime format. |
| 4 | Derived Column | Added `score_status` = Pass/Fail based on score threshold (≥ 50). |
| 5 | Categorization | Binned `exam_score` into Low, Average, Good, Excellent. |
| 6 | Drop Irrelevant Columns | Removed `name` for privacy and minimalism. |

**Outputs:**
- `/transformed/transformed_full.csv`  
- `/transformed/transformed_incremental.csv`

---

## 4️⃣ Tools Used  

| Tool / Library | Purpose |
|----------------|----------|
| **Python 3.13** | Programming language used for data pipeline |
| **Pandas** | Data manipulation and cleaning |
| **NumPy** | Numerical operations |
| **Faker** | Synthetic data generation |
| **Jupyter Notebook** | Interactive environment for coding and documentation |


---

## 5️⃣ Steps to Run the Project  

### **Prerequisites**
Ensure you have the following installed:
- Python 3.10 or later  
- Jupyter Notebook or VS Code with Jupyter extension  
- Required libraries:
  ```bash
  pip install pandas numpy faker matplotlib
