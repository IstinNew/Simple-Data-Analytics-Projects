# Simple-Data-Analytics-Projects
1-2-3 Go


**Simple-Data-Analytics-Projects** involves analyzing a dataset of sales transactions to identify trends and patterns : clean the data, perform exploratory data analysis (EDA), and visualize the results.

# My Performed Steps

# Steps to Analyze `sales_data_sample.csv`

# 1. **Detect File Encoding** (optional):
import chardet

# Detect the encoding of the file (optional step)
with open('sales_data_sample.csv', 'rb') as f:
    result = chardet.detect(f.read())
print(result)

# 2. **Load the Data**:
import pandas as pd

# Try specifying a different encoding manually
try:
    data = pd.read_csv('sales_data_sample.csv', encoding='latin1')
except UnicodeDecodeError:
    data = pd.read_csv('sales_data_sample.csv', encoding='ISO-8859-1')

# 3. **Explore the Data**:
print(data.head())  # Display the first few rows
print(data.info())  # Get information about data types and missing values
print(data.describe())  # Get summary statistics

# 4. **Clean the Data**:
data.dropna(inplace=True)  # Remove missing values
data.drop_duplicates(inplace=True)  # Remove duplicate rows

# 5. **Data Transformation**:
# Convert to datetime
data['Date'] = pd.to_datetime(data['Date'])

# Extract year from date
data['Year'] = data['Date'].dt.year

# 6. **Data Visualization**:
import matplotlib.pyplot as plt
import seaborn as sns

# Plot a histogram of sales
sns.histplot(data['Sales'], bins=30)
plt.show()

# 7. **Perform Analysis**:
# Group by year and sum sales
sales_by_year = data.groupby('Year')['Sales'].sum()
print(sales_by_year)

# 8. **Generate Report**:
# Group by year and product, then sum sales
report = data.groupby(['Year', 'Product'])['Sales'].sum().reset_index()
print(report)

# 9. **Save Results**:
# Save the cleaned data to a new CSV file
data.to_csv('cleaned_sales_data.csv', index=False)
