# YuvaIntern Week 2 – Logistics Data Collection, Cleaning and Preprocessing

## Internship Details

**Organization:** YuvaIntern  
**Role:** Logistics Data Analyst Intern  
**Internship Duration:** 30 July 2026 – 27 August 2026  
**Work Mode:** Remote  

**Name:** SATHYALA MAHAMMED  
**College:** Bhimavaram Institute of Engineering and Technology  
**Branch:** Electronics and Communication Engineering (ECE)

---

## Week 2 Task

### Data Collection, Cleaning, and Preprocessing for Logistics Analysis

Week 2 of the Logistics Data Analyst Internship focused on preparing logistics data for further analysis. The project uses the Brazilian E-Commerce Public Dataset by Olist as the reference dataset.

The main objective was to understand data quality issues and develop a basic preprocessing pipeline using Python.

---

## Objectives

- Collect and inspect logistics-related datasets.
- Understand dataset structure and data types.
- Identify missing values.
- Check duplicate records.
- Convert date columns into appropriate datetime formats.
- Calculate delivery duration.
- Identify invalid delivery-time values.
- Detect outliers using the IQR method.
- Create a late-delivery indicator.
- Normalize numerical data.
- Standardize delivery-time features.
- Perform final data-quality validation.
- Save the processed dataset for further analysis.

---

## Dataset

The Olist dataset contains information related to:

- Orders
- Order Items
- Customers
- Sellers
- Products
- Payments
- Reviews
- Geolocation
- Product Categories

The dataset was loaded and processed using Python and Pandas.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- GitHub

---

## Data Preprocessing Steps

### 1. Data Collection

The Olist Brazilian E-Commerce Public Dataset was used as the reference dataset for the logistics preprocessing exercise.

### 2. Data Inspection

Dataset dimensions, column names, data types, missing values, and duplicate records were examined.

### 3. Missing Value Handling

Missing values were identified using Pandas functions such as:

```python
df.isnull().sum()
