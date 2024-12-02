# Home Sales Analysis

This project uses **Apache Spark** to analyze home sales data. The dataset includes details about properties such as number of bedrooms, bathrooms, price, and view rating. Key tasks involve querying and transforming the data using Spark SQL, caching tables, and working with Parquet-formatted data.

## Project Objectives

1. Analyze home sales data using **PySpark** and **Spark SQL**.
2. Perform advanced queries to derive insights such as:
   - Average price of homes by year built and property features.
   - Average price per view rating for homes above a specific price threshold.
3. Cache and uncache tables to compare runtime performance.
4. Partition data using Parquet format for efficient storage and retrieval.

---

## Files in the Repository

- **`Home_Sales.ipynb`**: Jupyter Notebook containing the analysis code.
- **`home_sales_revised.csv`**: The raw dataset file used for analysis.
- **`home_sales_partitioned`**: Directory containing Parquet-formatted data partitioned by `date_built`.
- **`README.md`**: Documentation for the project.

---

## Tools and Technologies Used

- **Apache Spark (PySpark)**: For data processing and SQL queries.
- **Python**: Main programming language.
- **Jupyter Notebook**: For development and execution of the code.
- **Parquet**: File format for storing data.

---

## Analysis Steps

1. **Load and Explore the Dataset**:
   - The dataset was loaded into a Spark DataFrame with the following schema:
     ```
     root
     |-- id: string (nullable = true)
     |-- date: date (nullable = true)
     |-- date_built: integer (nullable = true)
     |-- price: integer (nullable = true)
     |-- bedrooms: integer (nullable = true)
     |-- bathrooms: integer (nullable = true)
     |-- sqft_living: integer (nullable = true)
     |-- sqft_lot: integer (nullable = true)
     |-- floors: integer (nullable = true)
     |-- waterfront: integer (nullable = true)
     |-- view: integer (nullable = true)
     ```

2. **Query Using Spark SQL**:
   - Various SQL queries were executed to analyze the data, as detailed below.

3. **Caching and Performance Optimization**:
   - Cached the `home_sales` table and compared query runtimes against uncached and Parquet-based data.

4. **Partition and Save Data**:
   - Partitioned the dataset by `date_built` and saved it in Parquet format for efficient storage and retrieval.

5. **Visualization and Insights**:
   - Results of queries are displayed directly.

---

## Results

### 1. Average Price for Four-Bedroom Homes by Year
| year | avg_price  |
|------|------------|
| 2019 | 300263.7   |
| 2020 | 298353.78  |
| 2021 | 301819.44  |
| 2022 | 296363.88  |

---

### 2. Average Price for Homes with 3 Bedrooms and 3 Bathrooms by Year Built
| date_built | avg_price  |
|------------|------------|
| 2010       | 292859.62  |
| 2011       | 291117.47  |
| 2012       | 293683.19  |
| 2013       | 295962.27  |
| 2014       | 290852.27  |
| 2015       | 288770.3   |
| 2016       | 290555.07  |
| 2017       | 292676.79  |

---

### 3. Average Price for Homes (3 Bedrooms, 3 Bathrooms, 2 Floors, ≥2000 Sqft) by Year Built
| date_built | avg_price  |
|------------|------------|
| 2010       | 285010.22  |
| 2011       | 276553.81  |
| 2012       | 307539.97  |
| 2013       | 303676.79  |
| 2014       | 298264.72  |
| 2015       | 297609.97  |
| 2016       | 293965.1   |
| 2017       | 280317.58  |

---

### 4. Average Price per View Rating for Homes (Average Price ≥ $350,000)
#### Parquet Data Results
| view | avg_price   |
|------|-------------|
| 91   | 1137372.73  |
| 97   | 1129040.15  |
| 84   | 1117233.13  |
| 75   | 1114042.94  |
| 89   | 1107839.15  |
| 78   | 1080649.37  |
| 77   | 1076205.56  |
| 87   | 1072285.2   |
| 86   | 1070444.25  |
| 82   | 1063498.0   |
| 90   | 1062654.16  |
| 99   | 1061201.42  |
| 76   | 1058802.78  |
| 85   | 1056336.74  |
| 95   | 1054325.6   |
| 98   | 1053739.33  |
| 81   | 1053472.79  |
| 83   | 1033965.93  |
| 94   | 1033536.2   |
| 88   | 1031719.35  |

### Performance Comparison

- **Cached Query Runtime**: ~0.33 seconds
- **Parquet Query Runtime**: ~0.23 seconds
