# Simple-Data-Analytics-Projects
1-2-3 Go


**Simple-Data-Analytics-Projects** involves analyzing a dataset of sales transactions to identify trends and patterns : clean the data, perform exploratory data analysis (EDA), and visualize the results.

# My Performed Steps

## Steps to Analyze `sales_data_sample.csv`

1. **Load the Data**:
   ```python
   import pandas as pd
   data = pd.read_csv('sales_data_sample.csv')
2. **Explore the Data**:
   print(data.head())  # Display the first few rows
   print(data.info())  # Get information about data types and missing values
   print(data.describe())  # Get summary statistics
3. **Clean the Data**:
   data.dropna(inplace=True)
   data.drop_duplicates(inplace=True)
4. **Data Transformation**:
   import matplotlib.pyplot as plt
   import seaborn as sns
   sns.histplot(data['Sales'], bins=30)
   plt.show()
5. **Perform Analysis**:
   sales_by_year = data.groupby('Year')['Sales'].sum()
   print(sales_by_year)
6. **Generate Report**:
   report = data.groupby(['Year', 'Product'])['Sales'].sum().reset_index()
   print(report)
7. **Save Results**:
   data.to_csv('cleaned_sales_data.csv', index=False)

# Commit and Push Changes
   git add README.md
   git commit -m "Added steps for analyzing sales_data_sample.csv"
   git push origin main
