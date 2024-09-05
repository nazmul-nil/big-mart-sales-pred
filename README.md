# Big Mart Sales Prediction

## Overview

This project involves building a machine learning model to predict the sales of various products across different outlets of Big Mart. The dataset contains information about products, their attributes, and details about the outlets. The goal is to predict the `Item_Outlet_Sales` for each product-outlet combination.

## Table of Contents
- [Project Structure](#project-structure)
- [Dataset](#dataset)
- [Features](#features)
  - [Feature Engineering](#feature-engineering)
  - [Encoding Techniques](#encoding-techniques)
- [Modeling](#modeling)
- [Evaluation](#evaluation)
- [Results](#results)
- [Conclusion](#conclusion)

## Project Structure

- `data/`: Contains the dataset files.
- `notebooks/`: Jupyter notebooks used for data exploration, preprocessing, feature engineering, and modeling.
- `models/`: Saved models and serialized objects.
- `README.md`: Project overview and documentation (this file).

## Dataset

The dataset includes various features related to products and outlets. The key columns in the dataset are:

- `Item_Identifier`: Unique product identifier.
- `Item_Weight`: Weight of the product.
- `Item_Fat_Content`: Whether the product is low fat or regular.
- `Item_Visibility`: Percentage of total display area allocated to this product in a store.
- `Item_Type`: Category of the product.
- `Item_MRP`: Maximum retail price (cost to the customer).
- `Outlet_Identifier`: Unique store identifier.
- `Outlet_Establishment_Year`: The year in which the store was established.
- `Outlet_Size`: Size of the store (small, medium, large).
- `Outlet_Location_Type`: Type of city in which the outlet is located.
- `Outlet_Type`: Whether the outlet is a grocery store or a supermarket.
- `Item_Outlet_Sales`: The target variable, which is the sales of the product in the particular store.

## Features

### Feature Engineering

Feature engineering played a crucial role in improving the model's predictive power. Below are the key engineered features:

- **Price Per Visibility**: Created a new feature by dividing `Item_MRP` by `Item_Visibility` to capture the price to visibility ratio.
- **Outlet Age**: Derived the age of each outlet by subtracting `Outlet_Establishment_Year` from the current year.
- **Log Transformations**: Applied log transformations to skewed features such as `Item_Visibility` and `Item_Outlet_Sales` to stabilize variance and reduce the impact of outliers.
- **Polynomial Features**: Created new polynomial features, such as the square of `Item_Visibility`, to capture non-linear relationships.
- **Interaction Features**: Introduced interaction features like `Weight_MRP_Interaction` to understand the combined effect of product weight and price on sales.

### Encoding Techniques

To handle categorical variables, the following encoding techniques were applied:

- **Label Encoding**: Converted categorical variables with an ordinal relationship into numerical format, such as `Outlet_Size`.
- **One-Hot Encoding**: Applied one-hot encoding to categorical variables like `Outlet_Type` and `Outlet_Location_Type` to convert them into binary features.
- **Target Encoding**: Used target encoding for categorical variables like `Item_Type`, where categories were replaced by the mean target value for each category.

## Modeling

The model was built using `XGBRegressor`, a powerful gradient boosting algorithm from the XGBoost library. The following steps were involved:

1. **Data Splitting**: The data was split into training and testing sets.
2. **Model Training**: The XGBoost model was trained using the training set.
3. **Hyperparameter Tuning**: Although the model performed well with default parameters, further tuning was conducted to optimize performance.

## Evaluation

The model's performance was evaluated using the R² metric. The results were as follows:

- **Training R²**: `0.9999894831776037`
- **Testing R²**: `0.9999894831776037`

## Results

The high R² values on both training and testing sets indicate that the model fits the data extremely well, likely capturing most of the variability in `Item_Outlet_Sales`.

## Conclusion

This project demonstrates the importance of feature engineering and encoding techniques in improving model performance. By carefully crafting new features and transforming existing ones, the model's accuracy was significantly enhanced. The `XGBRegressor` proved to be an effective algorithm for this regression task, providing excellent predictive performance.

For further improvements, consider testing the model on a validation set or experimenting with other machine learning algorithms to compare performance.
