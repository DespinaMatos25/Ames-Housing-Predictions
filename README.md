# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Ames Housing Data and Kaggle Challenge

### Table of Contents:

- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Insights and Evaluations](#Insights-and-Evaluations)
- [Sources](#Sources)

---
### Problem Statement

Everyday, there are individuals who are buying or selling a home. This can be exciting but also nerve-racking for these individuals because this progress is a *huge* financial investment. Potential buyers will need to budget the costs they are expecting to incur, while potential sellers will need to understand the costs to estimate a price for their home. In the United States, there is a city called Ames in the state of Iowa. Individuals from this city are dealing with the same concerns as a potential buyer or seller across the world. **How could an individual in Ames be able to budget for buying or selling a home?**

This potential buyer or seller will have to predict the price of a home given that they know the separate features of that particular home.

*How do we investigate this problem?* We have to explore a large data set of over 2,050 homes in the Ames housing market. Then we use that insight to build a linear regression model to predict the future price of an individual home. 


---

### Executive Summary

We began by importing the two data sets, training and testing, of the Ames Housing Market. We have two data sets because our training data set needed to be fitted on our testing data set to be able to evaluate our model. Both data sets have eighty feature columns of a particular home. However, the training data set had an additional column called sale price which was our target variable. 

After importing in both data sets, we decided to clean the data. We were looking for key features. Are the data sets complete? Are any of them missing any values? Does the minimum and maximum numbers make sense logically in each feature? Are the data types in the correct format? And finally, if not, do we have to create dummy variables for any of the qualitative data? 

After exploring our data sets, we used the training data set to examine the correlation of each nominal and numerical feature with respect to our target variable. We used visualizations to see these particular correlations. We used histograms, a heat map, box plots, and scatter plots.

After observing our correlations, we inspected that our observations were not complete for our linear regression model. We need to completely change our datasets into numerical data. We used one-hot encoding for the nominal data. However, for the ordinal data, we had a different approach, we used a numerical rating structure to replace with the categorical data. We wanted to have all of our features available for our modeling. 

After creating all of our features in both data sets into numerical data, we were able to come back to our outliers problem. We decided that we will take outliers out of our training data set that seemed irrational and not related to our problem statement.  

Finally, we were ready to model. We used train/test spilt to fit both data sets with one another. Then we modeled our linear regression model with our selected features. We also calculated the linear regression metrics to determine how well our model was to the problem statement.

Then to standardize our linear regression model, we used Ridge and Lasso regressions. We first grid searched for our hyper parameters for Ridge and Lasso by using RidgeCV and LassoCV. After getting our alphas for Ridge and Lasso we model each and determined the regression metrics for each, similarly to the linear regression model. We focused on the bias-variance tradeoff for each regression model to determined which model was the best to answer our problem statement. 

---

### Insights and Evaluations

|Regression Model|Training $R^2$ Score|Training RMSE Score|
|---|---|---|
|Linear Model|.931|20866|
|Ridge Model|.925|21656|
|Lasso Model|.928|21298|

|Regression Model|Testing $R^2$ Score|Testing RMSE Score|
|---|---|---|
|Linear Model|.916|23103|
|Ridge Model|.918|22834|
|Lasso Model|.919|22621|


The **Lasso Regression Model** was the best model to test our training data because it was able to well manage unknown data according to the $R^2$ score.

However, the model was still slightly underfit because it had high bias and low variance. 

Despite the slightly underfitting, this model can be use to predict the price of a home given that they know the separate features of that particular home. The six best features were Gr Liv Area, Overall Qual, BsmtFin SF 1, Year Built, and Total Bsmt SF. The worse features were MS Zoning_RH, 3Ssn Porch, Misc Feature_NA, Lot Config_FR2, Heating_GasW, and Exterior 2nd_Wd Shng. The two neighborhoods that might be a good investment are in Neighborhood_NridgHt and Neighborhood_StoneBr. 

Given this position, this model can be generalized to other cities because most of the top features in this model is used in other cities as well. For instance, Gr Liv Area and Overall Qual is used to determine a price of a house basically every where. Yet, the only particular feature that can not be generalized is the particular neighborhoods in Ames, Iowa. 

Finally, we will not be able to determine if our model is well manage model if the unknown data includes time. We do not know when a particular home was sold in the Housing Market data. Therefore, this could be another limitation on our model.   

So we still have some recommend questions we need to ask: 
1. Will our model be able to predict the price of a home at a given future time if we had the date of each home in our data?
2. How will our model differ if we had include a log feature fitted on our training data set? 
3. How will our model differ if we created interaction terms? 
4. How will we be able to have consistent data to compare our model with other cities? (i.e. scaling and selected features)
5. How will our model take in count how many homes are actually being build every year to commentate the citizens of Ames? 

---

### Sources

“How to show the title for the diagram of Seaborn pairplot() or PridGrid()?” Stackoverflow, https://stackoverflow.com/questions/36813396/how-to-show-the-title-for-the-diagram-of-seaborn-pairplot-or-pridgrid. Accessed 8 January 2020. 

“Stacked Bar Graph.” Matplotlib, https://matplotlib.org/3.1.1/gallery/lines_bars_and_markers/bar_stacked.html#sphx-glr-gallery-lines-bars-and-markers-bar-stacked-py. Accessed 8 January 2020. 

“pandas.DataFrame.reindex.” Pandas, https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.reindex.html. Accessed 10 January 2020. 

Galarnyk, Michael. “Understanding Boxplots.” Towards data science, https://towardsdatascience.com/understanding-boxplots-5e2df7bcbd51. Accessed 12 January 2020.  

“Ames, IA Livability.” AreaVibes, https://www.areavibes.com/ames-ia/livability/. Accessed 16 January 2020. 

“Building Ames: where the housing market stands today.” Ames Tribune, https://www.amestrib.com/article/20160521/News/305219982. Accessed 16 January 2020. 

“Ames highly ranked as top college town in two rankings.” Ames Tribune, https://www.amestrib.com/news/20191009/ames-highly-ranked-as-top-college-town-in-two-rankings. Accessed 16 January 2020. 
