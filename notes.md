Airbnb Dataset Analysis

📌 Project Overview

This project analyzes an Airbnb dataset using Python, Pandas, NumPy, and Matplotlib.

The analysis focuses on listings, prices, room types, neighbourhoods, reviews, availability, property types, guest capacity, and estimated revenue.

🛠️ Libraries Used

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

📂 Dataset Loading

df = pd.read_csv("archive.zip")
print(df.head())

Note: If df is not defined, make sure you run the dataset-loading cell before running the analysis cells.

🔍 Basic Dataset Exploration

1. View First 10 Rows

print(df.head(10))

2. View Last Rows

df.tail()

3. Check Rows and Columns

df.shape

4. Check Column Names

df.columns

5. Understand Dataset Information

df.info()

6. Statistical Summary

df.describe()

7. Check Missing Values

df.isnull().sum()

8. Check Duplicate Rows

df.duplicated().sum()

9. Check Data Types

df.dtypes

🧹 Data Cleaning

Clean the Price Column

df['price'] = (
    df['price']
    .replace('[\$,]', '', regex=True)
    .astype(float)
)

df['price'].describe()

Check Unique Values

df['neighbourhood_group_cleansed'].unique()
df['property_type'].unique()

Count Categories

df['room_type'].value_counts()
df['neighbourhood_group_cleansed'].value_counts()
df['property_type'].value_counts().head(10)

📊 Data Analysis Questions

Question 1: Which neighbourhood has the most Airbnb listings?

Chart: Bar chart

data = df['neighbourhood_group_cleansed'].value_counts()

data.plot(kind='bar')

plt.title('Airbnb Listings by Neighbourhood')
plt.xlabel('Neighbourhood')
plt.ylabel('Number of Listings')

plt.show()

Question 2: What percentage of listings belong to each room type?

Chart: Pie chart

data = df['room_type'].value_counts()

data.plot(
    kind='pie',
    autopct='%1.1f%%'
)

plt.title('Room Type Distribution')
plt.ylabel('')

plt.show()

Question 3: What is the average price in each neighbourhood?

Chart: Bar chart

data = df.groupby(
    'neighbourhood_group_cleansed'
)['price'].mean()

data = data.sort_values(ascending=False)

data.plot(kind='bar')

plt.title('Average Airbnb Price by Neighbourhood')
plt.xlabel('Neighbourhood')
plt.ylabel('Average Price')

plt.show()

Question 4: Which room type is the most expensive?

Chart: Bar chart

data = df.groupby('room_type')['price'].mean()

data = data.sort_values(ascending=False)

data.plot(kind='bar')

plt.title('Average Price by Room Type')
plt.xlabel('Room Type')
plt.ylabel('Average Price')

plt.show()

Question 5: Is there a relationship between price and number of reviews?

Chart: Scatter plot

plt.scatter(
    df['price'],
    df['number_of_reviews'],
    alpha=1.0
)

plt.title('Price vs Number of Reviews')
plt.xlabel('Price')
plt.ylabel('Number of Reviews')

plt.show()

Question 6: Which neighbourhood has the most reviews?

Chart: Bar chart

data = df.groupby(
    'neighbourhood_group_cleansed'
)['number_of_reviews'].sum()

data = data.sort_values(ascending=False)

data.plot(kind='bar')

plt.title('Total Reviews by Neighbourhood')
plt.xlabel('Neighbourhood')
plt.ylabel('Total Reviews')

plt.show()

Question 7: Which neighbourhood has the highest availability?

Chart: Bar chart

data = df.groupby(
    'neighbourhood_group_cleansed'
)['availability_365'].mean()

data = data.sort_values(ascending=False)

data.plot(kind='bar')

plt.title('Average Availability by Neighbourhood')
plt.xlabel('Neighbourhood')
plt.ylabel('Available Days')

plt.show()

Question 8: What are the top 10 property types?

Chart: Horizontal bar chart

data = df['property_type'].value_counts().head(10)

data.sort_values().plot(kind='barh')

plt.title('Top 10 Property Types')
plt.xlabel('Number of Listings')
plt.ylabel('Property Type')

plt.show()

Question 9: Does the number of guests affect the price?

Chart: Line chart

data = df.groupby('accommodates')['price'].mean()

data.plot(
    kind='line',
    marker='o'
)

plt.title('Average Price vs Number of Guests')
plt.xlabel('Number of Guests')
plt.ylabel('Average Price')

plt.show()

Question 10: Which neighbourhood generates the highest estimated revenue?

Chart: Bar chart

data = df.groupby(
    'neighbourhood_group_cleansed'
)['estimated_revenue_l365d'].sum()

data = data.sort_values(ascending=False)

data.plot(kind='bar')

plt.title('Estimated Revenue by Neighbourhood')
plt.xlabel('Neighbourhood')
plt.ylabel('Estimated Revenue')

plt.show()

📈 Chart Recommendations

Question

Analysis

Recommended Chart

1

Listings by neighbourhood

Bar chart

2

Room type percentage

Pie chart

3

Average price by neighbourhood

Bar chart

4

Average price by room type

Bar chart

5

Price vs reviews

Scatter plot

6

Reviews by neighbourhood

Bar chart

7

Availability by neighbourhood

Bar chart

8

Top property types

Horizontal bar chart

9

Guests vs price

Line chart

10

Revenue by neighbourhood

Bar chart

🎯 Skills Practiced

Loading CSV/ZIP datasets

Pandas DataFrame operations

Viewing and understanding data

Checking missing values

Checking duplicate values

Checking data types

Data cleaning

GroupBy operations

Value counts

Sorting data

Statistical analysis

Data visualization

Bar charts

Pie charts

Scatter plots

Line charts

✅ Project Conclusion

This Airbnb analysis demonstrates how Python can be used to explore a real-world dataset. The project examines important business questions related to Airbnb listings, pricing, room types, reviews, availability, property types, guest capacity, and revenue.

The charts help identify patterns and compare different neighbourhoods and listing characteristics.
