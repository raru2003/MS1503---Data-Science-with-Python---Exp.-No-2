# Experiment 2 : Customer Data Exploration Using Pandas

## Aim
To create a sample customer dataset and perform data exploration, filtering, sorting, grouping, and basic statistical analytics using Pandas functions in Python.

## Algorithm

1. **Start** the program.
2. **Import Library**: Import the `pandas` library as `pd` for tabular data manipulation and analysis.
3. **Initialize Dataset**: Create a Python dictionary `data` containing customer attributes (`Customer_ID`, `Customer_Name`, `Region`, `Age`, `Annual_Income`, `Spending_Score`, `Loyalty_Years`).
4. **Construct DataFrame**: Convert the dictionary into a structured Pandas DataFrame `df` using `pd.DataFrame(data)` and print the dataset.
5. **Inspect Structure & Summary**:
   * Display dataset dimensions (`df.shape`), column names (`df.columns`), data types and null counts (`df.info()`), and descriptive statistics (`df.describe()`).
   * Display the first 3 records (`df.head(3)`) and last 3 records (`df.tail(3)`).
6. **Sort & Filter Records**:
   * Sort customers in descending order of `Annual_Income` using `df.sort_values()`.
   * Filter high-income customers where `Annual_Income > 70000`.
7. **Perform Group-Wise & Frequency Analysis**:
   * Group customers by `Region` and calculate regional averages for `Annual_Income` and `Spending_Score` using `df.groupby().mean()`.
   * Count customer distribution across each region using `df["Region"].value_counts()`.
8. **Compute Overall Metrics & Top Performer**:
   * Identify the customer record with the highest `Spending_Score` using `df["Spending_Score"].idxmax()` and `df.loc[]`.
   * Calculate overall mean `Annual_Income` and mean `Spending_Score`.
9. **Stop** the program.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation** | `pd.DataFrame()` | Converts a Python dictionary into a 2D labeled tabular DataFrame |
| **Structural Inspection** | `df.shape`, `df.columns` | Retrieves dimensions `(rows, columns)` and column labels |
| | `df.info()`, `df.describe()` | Summarizes column data types, memory usage, and descriptive statistics |
| | `df.head(n)`, `df.tail(n)` | Views the first `n` and last `n` rows of the dataset |
| **Sorting & Filtering** | `df.sort_values()` | Orders records by `Annual_Income` in descending order |
| | Boolean Indexing (`df[...]`) | Filters customers with `Annual_Income > 70000` |
| **Grouping & Aggregation** | `df.groupby().mean()` | Aggregates mean income and spending score per `Region` |
| | `df["Region"].value_counts()` | Counts occurrences of customers in each region |
| | `idxmax()`, `df.loc[]`, `.mean()` | Locates the top spender row and computes dataset-wide averages |

## Program

#Customer Data Exploration using Pandas

#Step 1: Create a sample customer dataset
import pandas as pd

data = {
    'Customer_ID': [101, 102, 103, 104, 105, 106],
    'Customer_Name': ['Arun', 'Bala', 'Charan', 'Divya', 'Ezhil', 'Farah'],
    'Region': ['South', 'North', 'East', 'South', 'West', 'North'],
    'Age': [25, 32, 28, 35, 40, 29],
    'Annual_Income': [50000, 75000, 60000, 90000, 85000, 70000],
    'Spending_Score': [75, 60, 85, 90, 65, 80],
    'Loyalty_Years': [2, 5, 3, 7, 6, 4]
}

#Step 2: Convert to a Pandas DataFrame
df = pd.DataFrame(data)
print("Customer Dataset:\n", df)

#Step 3: Basic exploration
print("\nDataset Shape:", df.shape)
print("\nColumn Names:", df.columns)
print("\nDataset Information:")
df.info()

print("\nDescriptive Statistics:")
print(df.describe())

#Step 4: Display first and last few records
print("\nFirst 3 Records:\n", df.head(3))
print("\nLast 3 Records:\n", df.tail(3))

#Step 5: Sort customers by Annual Income (descending)
sorted_df = df.sort_values(
    by='Annual_Income', ascending=False
)
print("\nSorted Customers:\n", sorted_df)

#Step 6: Filter high-income customers (Income > 70000)
high_income = df[df['Annual_Income'] > 70000]
print("\nHigh-Income Customers:\n", high_income)

#Step 7: Group customers by Region and find average Income and Spending Score
regional_avg = df.groupby('Region')[
    ['Annual_Income', 'Spending_Score']
].mean()

print("\nRegional Average:\n", regional_avg)

#Step 8: Count number of customers in each Region
print("\nCustomers by Region:\n",
      df['Region'].value_counts())
      
#Step 9: Identify customer with maximum Spending Score
top_customer = df.loc[df['Spending_Score'].idxmax()]
print("\nTop Spending Customer:\n", top_customer)

#Step 10: Compute overall averages
print("\nOverall Average Income:",
      df['Annual_Income'].mean())

print("Overall Average Spending Score:",
      df['Spending_Score'].mean())

## Output
Dataset Shape: (6, 7)

First 3 Records:
   Customer_ID Customer_Name Region  Age  Annual_Income  Spending_Score
0          101          Arun  South   25          50000              75
1          102          Bala  North   32          75000              60
2          103        Charan   East   28          60000              85

High-Income Customers:
   Customer_ID Customer_Name Region  Annual_Income
3          104         Divya  South          90000
4          105         Ezhil   West          85000

Customers by Region:
North    2
South    2
East     1
West     1

Top Spending Customer:
Customer_Name     Divya
Spending_Score       90

Overall Average Income: 71666.67
Overall Average Spending Score: 75.83

## Result
The program successfully creates a customer dataset using Pandas and performs exploratory analysis, sorting, filtering, regional grouping, and summary statistics.
