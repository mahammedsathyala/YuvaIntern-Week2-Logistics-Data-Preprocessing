# YuvaIntern Week 2 – Logistics Data Collection, Cleaning and Preprocessing

## Internship Details

**Internship Organization:** YuvaIntern  
**Internship Role:** Logistics Data Analyst Intern  
**Internship Duration:** 30 July 2026 – 27 August 2026  
**Work Mode:** Remote  
**Name:** SATHYALA MAHAMMED  
**College:** Bhimavaram Institute of Engineering and Technology  
**Branch:** Electronics and Communication Engineering (ECE)

---

## Week 2 Task

### Data Collection, Cleaning, and Preprocessing for Logistics Analysis

Week 2 of the Logistics Data Analyst Internship focused on data collection, data cleaning, and preprocessing of logistics-related data.

For this task, the Brazilian E-Commerce Public Dataset by Olist was used as the reference dataset. The dataset contains information related to orders, customers, sellers, products, payments, reviews, order items, and geolocation.

The main objective was to prepare the raw logistics data for further analysis by identifying and handling common data-quality issues.

---

## Objectives

The main objectives of Week 2 were:

- Collect and inspect logistics-related datasets.
- Understand the structure and characteristics of the data.
- Identify missing values.
- Check for duplicate records.
- Convert date and time columns into suitable formats.
- Calculate delivery duration.
- Identify invalid data values.
- Detect outliers using the IQR method.
- Create a late-delivery indicator.
- Apply normalization techniques.
- Apply standardization techniques.
- Perform final data-quality checks.
- Prepare a cleaned dataset for further analysis.

---

## Dataset Used

### Brazilian E-Commerce Public Dataset by Olist

The Olist dataset contains multiple datasets related to Brazilian e-commerce and logistics operations.

The datasets used include:

- Orders
- Order Items
- Customers
- Sellers
- Products
- Payments
- Reviews
- Geolocation
- Product Category Translation

The datasets were loaded and processed using Python and Pandas.

---

## Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Visual Studio Code
- GitHub

---

## Data Preprocessing Methodology

### 1. Data Collection

The Brazilian E-Commerce Public Dataset by Olist was selected as the reference dataset for the logistics preprocessing task.

The datasets were loaded into Python using Pandas.

### 2. Data Inspection

The dataset was inspected to understand:

- Number of rows and columns
- Column names
- Data types
- Missing values
- Duplicate records

### 3. Missing Value Analysis

Missing values were identified using Pandas.

```python
df.isnull().sum()
```

Missing delivery dates were handled before calculating delivery duration.

### 4. Date Conversion

Date and time columns were converted into datetime format using Pandas. This makes it easier to perform delivery-time calculations and other time-based analysis.

```python
for column in date_columns:
    orders[column] = pd.to_datetime(
        orders[column],
        errors="coerce"
    )
```

This step ensures that the date columns are in the correct format for further analysis.

### 5. Delivery Time Calculation

Delivery duration was calculated using the difference between the order purchase timestamp and the customer delivery timestamp.

```python
orders["delivery_days"] = (
    orders["order_delivered_customer_date"]
    - orders["order_purchase_timestamp"]
).dt.total_seconds() / (24 * 60 * 60)
```

### 6. Invalid Value Handling

Negative delivery durations were identified because they represent invalid delivery records.

```python
invalid_delivery = orders_clean[
    orders_clean["delivery_days"] < 0
]
```

Invalid records were removed before further analysis.

### 7. Outlier Detection

The Interquartile Range (IQR) method was used to identify extreme delivery-time values.

```python
Q1 = orders_clean["delivery_days"].quantile(0.25)
Q3 = orders_clean["delivery_days"].quantile(0.75)

IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
```

A box plot was also used to visually identify potential outliers.

### 8. Late Delivery Identification

A new `is_late` feature was created by comparing the actual delivery date with the estimated delivery date.

```python
orders_processed["is_late"] = (
    orders_processed["order_delivered_customer_date"]
    > orders_processed["order_estimated_delivery_date"]
).astype(int)
```

A value of `1` represents a late delivery, while `0` represents an on-time delivery.

### 9. Normalization

Min-Max normalization was applied to the delivery-time feature using `MinMaxScaler`.

```python
scaler = MinMaxScaler()

orders_processed["delivery_days_normalized"] = (
    scaler.fit_transform(
        orders_processed[["delivery_days"]]
    )
)
```

Normalization scales numerical values into a common range and can be useful for further analytical and machine-learning tasks.

### 10. Standardization

Standardization was applied using `StandardScaler`.

```python
standard_scaler = StandardScaler()

orders_processed["delivery_days_standardized"] = (
    standard_scaler.fit_transform(
        orders_processed[["delivery_days"]]
    )
)
```

Standardization transforms values based on their mean and standard deviation.

### 11. Final Data Quality Check

After completing the preprocessing steps, the processed dataset was checked for:

- Missing values
- Duplicate records
- Invalid delivery times
- Dataset size
- Data consistency
- Processed numerical features

```python
print("Dataset shape:", orders_processed.shape)
print("Duplicate rows:", orders_processed.duplicated().sum())
print(orders_processed.isnull().sum())
```

---

## Visualizations

The notebook contains visualizations to understand the data before and after preprocessing.

The main visualizations include:

1. Delivery Time Outlier Detection
2. Delivery Time Distribution Before Outlier Removal
3. Delivery Time Distribution After Outlier Removal

These visualizations help understand delivery-time variation and the effect of preprocessing.

---

## Processed Dataset

After preprocessing, the cleaned dataset was saved as:

`week2_cleaned_orders.csv`

The processed dataset contains important features such as:

- `delivery_days`
- `is_late`
- `delivery_days_normalized`
- `delivery_days_standardized`

---

## Project Files

| File | Description |
|---|---|
| `Week2_Logistics_Data_Preprocessing.ipynb` | Complete Python preprocessing notebook |
| `YuvaIntern_Week2_Report.docx` | Week 2 internship report |
| `week2_cleaned_orders.csv` | Cleaned and processed orders dataset |
| `README.md` | Project documentation |
| `requirements.txt` | Required Python libraries |
| `.gitignore` | Git ignore configuration |

---

## Outcome

The Week 2 preprocessing pipeline successfully prepared the Olist order data for further logistics analysis.

The workflow included data inspection, missing-value analysis, date conversion, delivery-time calculation, invalid-value handling, outlier detection, late-delivery identification, normalization, standardization, and final data-quality validation.

The cleaned dataset can now be used for further logistics analysis, visualization, and predictive modeling.

---

## Reflection

Data quality has an important impact on logistics analytics and decision-making. Missing values, invalid records, duplicate records, and extreme values can affect the reliability of analytical results.

This task provided practical experience in identifying and handling common data-quality issues using Python, Pandas, NumPy, Matplotlib, and Scikit-learn.

---

## Conclusion

The Week 2 task provided practical experience in collecting, cleaning, and preprocessing logistics data using Python.

The Olist dataset was inspected and processed to improve data quality and prepare it for further analysis. The completed notebook and cleaned dataset provide a useful foundation for upcoming logistics analytics tasks.
