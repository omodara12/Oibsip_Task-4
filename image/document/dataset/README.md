## PREDICTING HOUSE PRICES WITH LINEAR REGRESSION
### Introduction
##### In this project, I developed a predictive model to estimate housing prices using linear regression. The dataset includes various features such as area, location, number of bedrooms, and amenities. The primary goal was to apply the fundamental machine learning workflow—starting with data exploration and cleaning, proceeding through model training and evaluation, and finally offering actionable insights through meaningful visualizations.
##### Goals:
##### .Understanding of linear regression concepts
##### .Practical experience in implementing a predictive model
##### .Model evaluation and interpretation skill
## Loading Dataset
![dataset](https://github.com/omodara12/Oibsip_Task-4/blob/main/Task%204_1.png)
![dataset](https://github.com/omodara12/Oibsip_Task-4/blob/main/task4-2.png)
##### Dataset Overview
##### The dataset consists of multiple features describing a house, including:
##### •	Numerical: Area, bedrooms, bathrooms, stories, parking, price
##### •	Categorical: Furnishing status, main road access, guest room availability, etc.
## Data cleaning and Explorations
## I checked for missing values
![missing values](https://github.com/omodara12/Oibsip_Task-4/blob/main/task4-3.png)
##### There was no missing value
## I checked for Duplicate
![duplicate](https://github.com/omodara12/Oibsip_Task-4/blob/main/task4-4.png)
##### There was no duplicated value or row
## I checked for data types
![datatype](https://github.com/omodara12/Oibsip_Task-4/blob/main/task4-5.png)
## SELECTING NUMERICAL FEATURES/COLUMNS
##### numeric_cols = df.select_dtypes(include=["int64", "float64"]).columns
df[numeric_cols].describe()
## Selecting Numerical Columns/Features
![numerical features](https://github.com/omodara12/Oibsip_Task-4/blob/main/task4-6.png)
## HISTOGRAM FOR NUMERICAL FEATURES
![histogram](https://github.com/omodara12/Oibsip_Task-4/blob/main/histo.png)
![histogram](https://github.com/omodara12/Oibsip_Task-4/blob/main/task4-9.png)
## DETECTING OUTLIERS USING IQR
![iqr](https://github.com/omodara12/Oibsip_Task-4/blob/main/task4-10.png)
![code](https://github.com/omodara12/Oibsip_Task-4/blob/main/task4-11.png)
## Visualize with Boxplots
![code](https://github.com/omodara12/Oibsip_Task-4/blob/main/boxplot(v).png)
![visual](https://github.com/omodara12/Oibsip_Task-4/blob/main/boxplot%20visualpng.png)
## REMOVING OUTLIERS FOR HOUSE PRICE
![code](https://github.com/omodara12/Oibsip_Task-4/blob/main/price(out).png)
## Before and After Outliers
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/Before%26After(C).png)
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/visual.png)
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/visual2.png)
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/visual3.png)
## Outlier Detection and Removal Interpretation
##### I visualized and analyzed outliers in numerical features using boxplots. Significant outliers were identified in:
##### •	area
##### •	price
##### •	bedrooms
##### I applied an interquartile range (IQR)-based filter to remove extreme values.
## •	Before: Features like area and price had long tails, skewing the distribution and negatively impacting model performance.
## •	After: Distributions became more centered, cabable of improving model's ability to generalize.







