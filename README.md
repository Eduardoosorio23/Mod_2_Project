# King County Realty Prediction Model
By: Eduardo Osorio

## The Project
Today were taking a look at King county's Housing data. The goal is to use the data provided to create a model that will help us predict the price of homes based on certain features.

## Sources Used
- King County Housing Data
- https://machinelearningmastery.com/rfe-feature-selection-in-python/
- scikit-learn.org

## Summery Of The Results
The final conclusions for this model are:
- For every unit of **sq ft living area** the price increases by **$1.56**
- If a house is a **waterfront property** you can expect the price to go up by **80 percent**.
- **2 bedroom** homes make the price go up by **12%** while **4 bedroom** homes make the price go **down** by **7%**
- For total floors, houses with both **1.5 and 2.5 floors**, **increase** the value by **3%**. Houses with **3 floors increase** the value by **25%**


## The Data
The data used took property information from King County. The Data Frame contained the following:
- 21,597 Houses .
- Using 70 different Zip Codes in the King county area.
- Grades ranging from 3 - 13 (overall grade given to the housing unit, based on King County grading system. Assuming 13 is the highest.)
- Conditions ranging from 1 - 5 ( How good the condition of the house  is. Assuming 5 is the highest.)
- If the house is a waterfront or non-waterfront property.
- Houses built from 1900 to  2015

##EDA
- Removed Null values in the ‘waterfront’ column
- Replaced the Null values in the **yr_renovated** column so that I could use it to engineer another column that counted how many years since the last renovation.
- Dropped the **view** column since it showed no purpose.
- Dropped **sqft_lot15**, and **sqft_above** since they showed collinearity to other columns.
-Created a **month_sold** column to show us the month the house was last sold.

## Baseline model
This model used most of the features to get a general idea of which features affect the data the most. There was some **multicollinearity** between **sqft_living**, **sqft_living15**, and **bathrooms**. The only feature taken out here was **bathrooms** because **sqft_living15** could still be useful to the model. Heres a table of how the rest of the data correlated.
![alt text](https://github.com/Eduardoosorio23/Mod_2_Project/blob/main/data_files/Images/kcc%20correlation.png?raw=true "Data correlation")

After running the OLS, This model had an **R^2 of 1.0** which tells us that its **overfitting** the data. The biggest contributor to this was the zip codes features since there was 70 different zip codes the model was using.
## Final Model
The features selected in this model were: **price**, **sqft_living**, **sqft_lot**, **sqft_living15**, **yr_built**, **bedrooms, floors**, **waterfront**, **condition**, **grade**, **yrs_renovated**, **sale_month**. **Zip Codes** was removed to avoid **overfitting**. This model also used a **Stepwise Function** to eliminate **p-values over 0.5** and **Recursive Feature Elimination** to select the most relevant features. The **R^2** is lower then what was hoped for at **.66** but overall much better fitting then before. Both the **train and test data** had an **standard error of 1.4**.
![alt text](https://github.com/Eduardoosorio23/Mod_2_Project/blob/main/data_files/Images/OLS.png?raw=true "homoscedasticity")


![alt text](https://github.com/Eduardoosorio23/Mod_2_Project/blob/main/data_files/Images/Mod_2%20Homoscadacity.png?raw=true "homoscedasticity")
- The data is mostly evenly scattered.

![alt text](https://github.com/Eduardoosorio23/Mod_2_Project/blob/main/data_files/Images/mod_2%20QQplot.png?raw=true "QQ Plot")
- The **QQ plot** shows us that the data came from common distributions

## Recomendations

- If you're building a house, 3 story water front homes will get you the best return on investment.
- Houses with bigger rooms and less then 4 will be the most profitable.

##  Next Steps
Investigating into which zip codes have more profitable homes on average could help us optimize the model and pick locations that would also increase the price of a home.
