# Phase 2 Project

## The King County House Project

### Author : Nahum Odemba
link to tableu: https://public.tableau.com/app/profile/nahum.odemba/viz/KingsCountyHouseSales/Dashboard1?publish=yes

## Overview 

For this project, I use multiple linear regression modeling to analyze house sales in King County.

## Business Understanding

* King County is located in the U.S state of Washington.
* King is the most populous county in Washington state.
* Like many Americans, real estate represents a huge portion of the residents’ wealth.
* House prices in the county are determined by different features such as the floor size, number of bedrooms, bathrooms, view, and waterfront.
* It can be challenging for a home buyer or seller to decide on or predict the price for the house.
* The project's objective, therefore, is to conduct linear regression to predict the prices of houses sold in King County based on such factors as the size of the house, number of bedrooms and bathrooms, view, and waterfront.
* Price will be the dependent variable or the target.
* Ultimately, the project aims to develop a model that can best predict the prices at which a house should be sold in the county to maximize the profit.
* Stakeholders for the project include home sellers and builders.
* The project is important because it is vital to understand the factors that hugely affect the prices of houses in the county.
* We are lucky that some of the resources have already been provided for these project:
* They include dataset kc_house_data.csv from where we will do data understanding and prepartion.

## Data Understanding

#### The Data

This project uses the King County House Sales dataset, which can be found in  `kc_house_data.csv` in the data folder in this assignment's GitHub repository. The description of the column names can be found in `column_names.md` in the same folder. As with most real world data sets, the column names are not perfectly described, so you'll have to do some research or use your best judgment if you have questions about what the data means.

It is up to you to decide what data from this dataset to use and how to use it. If you are feeling overwhelmed or behind, we recommend you **ignore** some or all of the following features:

* `date`
* `view`
* `sqft_above`
* `sqft_basement`
* `yr_renovated`
* `zipcode`
* `lat`
* `long`
* `sqft_living15`
* `sqft_lot15`

## Modeling

Three models were used. The baseline model used the following as variables:
* `price` as the dependent variable
* `sqft_living` as the independent

The second model used `price` as the dependent variable and the following as the independent:
* `sqft_living` 
* `floors`
* `bathrooms`
* `sqft_above`
* `sqft_living15`
* `bedrooms`

The second multiple linear regression model included categorical variables. These variables were transformed using one-hot encoding using Pandas. The added categorical variables included:
* `condition`
* `grade`

## Regression Results Summary

#### Rationale

First, I would start by saying that this project chose to use simple linear regression and multiple linear regression for price prediction because these two approaches provide a simpler and quicker way to understand the relationship between the target and the predictor.
Second, instead of using graphs to explain these relationships, I chose regression coeffiecients because unlike simple correlation graphs, for example, regression coefficients are able to show both cause and effect.
Remember the law of correlation which says that correlation is not causation.
A strong positive correlation between the price and sqft_living, for example, should not be interprated that a larger sqft_living causes higher house prices in King County. This is an assumption that could only be proved or disproved using regression and not correlation graph.
Third, I chose to use StatsModels because it allows for estimation by ordinary least squares (OLS) which minimizes residuals
This means that our line of best fit will have the least model loss and hence the best suited to predict the price
Importantly, this project chose not to solely rely on 𝑅2 to determine the quality of our model because of its limitations. These limiations will be discussed under the limitations (see below).
Instead I chose to use additional metric, the mean absolute error of the model. This metric was chosen because it is more useful in that it directly measures the mean average error.
The mean average error value, therefore, is a better metric to use in this case compared to 𝑅2 which will always increase with the increase in variables.

#### Results

First, all the three models had a p-value of 0.00 indicating that they were all statistically signficant compared to the 𝛼=0.05
Results show that the 𝑅2 value increased with the increase in variables from 0.387 in baseline model to 0.424 in model two and to 0.500 in model three.
Model Three that included the two categorical variables alongside independent variables used in model two had the highest 𝑅2 value of 0.500.
The mean average error kept on reducing with an increase in the variables. The third model had the lowest mean average error of 115359.81.
This means that, using the third model, our model is off by 115359.81 dollars in a given prediction.
This is slightly lower than using the first model which had an MAE of 47425106.21 dollars and second with 125750.67.
These results indicate that if our stakeholders had to use our third model to predict the price of the houses in King County, they will have to take into account the possibility of going off the mark by 115359.81 dollars.
Of course this means that our model has plenty of room for improvement to reduce this error to the minimum.

#### Limitations

One of the obvious limitations of linear regression modeling approach is that it assumes linearity.
We assume that our variables have near linear relationship, which from the correlation coefficients, we saw it was not perfect.
Second, because of how sensitive linear regression is to outliers, we dropped outliers in price which I cannot predict how much effect this was in developing a model to predict price.
Finally, we assume that the patterns in the relationship between the target and the predictors will remain the same over some period of time. In other words, our model is not trained to adjust to changes in this relationship.

#### Recommendations

The results of this project are very interesting and uselful in predicting house prices in King County.
First, it is important to know that the prices of houses in King County are affected by many variables.
Some of the variables that I found to affect the prices of the house most include the grade of the house:
Houses that are graded Poor lower the prices of houses in King County by 398715.51 dollars.
On the positive side, however, houses with condition--Very Good lead to an increase in the price of houses in King County by 99229.36 dollars.
Also, though sqft_living has the strongest positive correlation with our target price, an increase in this variable by one foot leads to an increase in the house price by only 129.33 dollars.
This means that it is true that correlation is not causation.
Therefore, when predicting the price of houses in King County, you should give more emphasis on the grade and condition of the house because they are the ones with the largest impacts on the price.
Houses that should sell higher are those with conditions very good and above, have two floors and above, and with big sqft_living.

