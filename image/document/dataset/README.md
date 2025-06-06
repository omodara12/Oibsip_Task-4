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
## Features selection and Preprocessing
##### from sklearn.model_selection import train_test_split
##### from sklearn.preprocessing import OneHotEncoder
##### from sklearn.compose import ColumnTransformer

## Features and target

##### X = df.drop("price", axis=1)
##### y = df["price"]

## Identify categorical columns
##### categorical_cols = X.select_dtypes(include="object").columns
##### numeric_cols = X.select_dtypes(exclude="object").columns

## One-hot encoding for categorical columns
##### I used one-hot encoding for all categorical columns, transforming binary and nominal values into numeric format. Examples:
##### •	'yes'/'no' → 1/0
##### •	'furnished', 'semi-furnished', 'unfurnished' 

##### preprocessor = ColumnTransformer(
##### transformers=[("cat", OneHotEncoder(drop="first"), categorical_cols)],
    
##### remainder="passthrough"
##### )

## Train-test split
##### I split the dataset into training and testing sets (80/20) and trained a Linear Regression model using Scikit-Learn.
#### X_train, X_test, y_train, y_test = train_test_split(
##### X, y, test_size=0.2, random_state=42
##### )
## Model Training
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/model%20t.png)
## MODEL EVALUATION
##### I split the dataset into training and testing sets (80/20) and trained a Linear Regression model using Scikit-Learn.
 #### Evaluation Metrics
##### •	Mean Squared Error (MSE): Measures average squared difference between predicted and actual prices
##### •	R² Score: Measures how well the model explains variability in housing prices
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/mode(ev).png)
## Interpretation
##### • An R² of 0.65 means the model explains ~65% of the variance in housing prices, which is decent for a simple linear model.
##### • Removing outliers improved both metrics significantly, showing the importance of data cleaning.
## Visualization:Actual Prices vs Predicted House Prices
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/visual%20code.png)
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/actual.png)
##### What the Plot Shows
##### X-axis: Actual house prices (true values from the dataset)

##### Y-axis: Predicted house prices (values your model predicted)

##### Dots: Each dot represents one data point (a house)

##### Red dashed line: The ideal line where predicted price = actual price (a perfect prediction)
## Interpretation
##### Many dots lie close to the red line, especially in the middle range of house prices (around 3M–7M), indicating:
##### The model is relatively accurate in this price range.
##### Predicted values are aligned with actual values.
##### Dots below the red line mean the model underestimated the price.
##### Noticeably, there are several points well below the line, especially for higher actual prices.
##### Dots above the red line reflect overestimation.
##### There are fewer such cases, but they still show some predictions higher than they should be.
##### The model shows reasonable predictive strength, especially in the mid-range of values.
## Residual plot 
![](https://github.com/omodara12/Oibsip_Task-4/blob/main/residual%20plo.png)
##### The residuals are centered around zero, which is expected in a good model.
##### There are some randomness in the spread, indicating the model is not strongly biased in one direction.
## Conclusion
##### This project successfully demonstrated the application of linear regression to predict housing prices based on a real-world dataset. Through systematic data exploration, cleaning, feature engineering, and model evaluation, we built a predictive model that explains approximately 65% of the variance in house prices—a strong foundation for a first iteration.
##### The visualizations of actual versus predicted values and residuals clearly show that the model captures the underlying trends in the data, especially for mid-range properties. With further refinements—such as advanced feature engineering or alternative algorithms—this model has the potential to become a robust tool for accurate real estate price prediction.

















