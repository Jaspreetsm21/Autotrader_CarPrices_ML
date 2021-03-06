# Car Price Estimator: Data Science Project Overview

- Created a tool that estimates car prices (MAE ~ £1539) to help car owners/buyers to negotiate the deal. 
- Scraped over 8000 car listings from Autotrader using python and Beautifulsoup
- Optimized Linear, Lasso, Decision Tree and Random Forest Regressors using GridsearchCV to reach the best model.

# Code and Resources Used

**Python Version**: 3.7

**Packages**: pandas, numpy, sklearn, matplotlib, seaborn,json, pickle

**Scraper Resource**: https://stackoverflow.com/questions/60012952/how-to-code-a-for-loop-in-python-for-a-web-scraper

# [Web Scraping](https://github.com/Jaspreetsm21/Autotrader_CarPrices_ML/blob/master/AutoTrader%20-%20Web%20Scraper%20.ipynb)
Autotrader only allows to scraper top 1000 listing per search. To extract large amounts of data, I created a list of postcodes around the UK and used for loop to scraper car data around postcodes and pages.


1. I decided to pick 10 postcodes around the UK to extract a large amount of data as 1000 listing per Search and each page has roughly 10 car listings

2. I'm extracting information like car title, prices, mileage, engine size ,gearbox and etc.

![](map.PNG)

I scraped over 8000 Car listing from autotrader.co.uk. With each listing, we got the following:

- Title
- Price
- Mileage
- Make
- BHP
- Engine Size
- Type of Vehicle
- Type of Gearbox
- Type of Fuel (Petrol,Diesel or Hybrid)
- Year 


# Data Cleaning
After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

- Dealing with Missing Values

- It looks like we have scraped some data that imported into the wrong columns. So I'm going to filter the data for Petrol, Diesel and Hybrid cars only.

- creating a new column called Car_Make - that we extracted from Car_Title Column

- Converting Car_Price and Car_Mileage into Numeric Values - before that, I'm going to remove £ sign and comma from each of the columns

# [EDA](https://github.com/Jaspreetsm21/Autotrader_CarPrices_ML/blob/master/AutoTrader%20-%20EDA.ipynb)

![](Images/Car1.PNG)![](Images/Car2.PNG)

![](Images/carpricevsmileage.PNG)

![](corr.PNG) ![](Images/type%20of%20vehicle.PNG)

![](Images/make.PNG)

![](Images/moving%20avg.PNG)

**Insight**

Average Car Prices are around £12,000 

75% of cars have mileage less than 53,000 miles.

28,000 is the average car mileage

Negative Correlation makes sense as car mileage goes up the car prices come down.

Hybrid cars are clearly more expensive than petrol and diesel cars.

On Average Hybrid Cars are £1,500 more expensive than petrol cars. The reason could be Hybrid cars were introduced in the early 2000s and it's still growing in its popularity as an environmental crisis is widely discussed.

On Average Automatic cars are £1,500 more expensive than Manual.

Ford is the most listed car on AutoTrader and also it is the most common car sold in the UK.

It is interesting to see most cars listed on Auto traders show that 2.0L producing more Automatic Cars compare to any other engine size which is mainly dominated by manual cars.



# [Model](https://github.com/Jaspreetsm21/Autotrader_CarPrices_ML/blob/master/Autotrader%20-%20Model%20.ipynb) 
First, I transformed the categorical variables into dummy variables. I also split the data into train and test sets with a test size of 25%.

I tried four different models and evaluated them using Mean Absolute Error.  I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

I tried four different models:

Lasso  – Baseline for the model

Decision Tree and Kneighborsregressor

Random Forest – Again, with the sparsity associated with the data, I thought that this would be a good fit.

![](Images/Feature_Eng.PNG)

# Evalution

The Random Forest model far outperformed the other approaches on the test and validation sets.

**Random Forest:** MAE = 1539

**Decision Tree:**  MAE = 2119

**Lasso Regression:** MAE = 1964
