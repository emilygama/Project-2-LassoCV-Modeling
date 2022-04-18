# Best Listings: Evaluation of House Features vs. Predicted Price
### Emily Gama - Data Scientist for Realty Group Insights Team

### Problem Statement and Background: 

I work for the analytics department at a realty group in Iowa that is gearing up for our annual insights meeting. I have been tasked with giving some predictions of sale prices to our realtors based on features of and around homes. These predictions are to be used to aid the realtors in setting an offer price for their clients that are selling their homes. The goal here is to provide guidance on listings based on the heatures that the home has or does not have. 

Explicitly, the problem is that our realty group wants more accurate listing prices based on the value of the home: What kind of features would best predict a higher or lower sale price of a home? I will examine housing sales in Ames, Iowa from 2006 to 2010 in an attempt to explore these relationships using regressions and transformations to make predictions. 

For some background, Ames is located nearly in the center of Iowa. It is a college town, home to Iowa State University. It has been named one of the top places for STEM grads and millenials as well as one of the healthiest cities in America. It boasts top ranking public schools, access to great healthcare services, varied parks and outdoor acitvities, and a population of 66,191. All of this means that there is much potential for a good housing market in Ames! [*Source*](https://www.cityofames.org/about-ames/about-ames).

### Description of Data

The dataset used in this project was collected from 2006 to 2010 from individual residential sales in Ames, Iowa. The sale information is from the Ames Assessor's Office and includes 82 different features. I use majority of these features in my project. 

The data description and dictionary can be found below, as well as a paper discussing the data and its characteristics. 

[*Paper*](http://jse.amstat.org/v19n3/decock.pdf)

[*Descriptions*](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)


### Strategy and Analysis

I modeled the data with a multiple linear regression. The transformations I used are SimpleImputer for replacing NAs with 0, OneHotEncoder for replacing categorical variables with numeric columns, and StandardScaler to get everything on the same scale to move through a LassoCV for regularization and cross validation. After running this dataframe through the LassoCV, I used TransformedTargetRegressor to log transform the target variable, saleprice, due to its distribution lacking normality. 

I replaced the NAs with 0 because that is what lined up with the data dictionary ordinal values. 

### Insights 

To qualify my insights, I review two examples drawn from our test set. Our first example is house sale ID 1579. This home has a lot area of 12018, is in the Timber neighborhood, is a single family home, overall quality of 7, built in 2008, finished basement square footage of 796, total above ground square footage of 1612, and sold in 2008 as a new home. It's predicted sale price would be $\$200,483.14$.

Our second example is house sale ID 1303. This home has a lot area of 7311, is in the Old Town neighborhood, a single family home, overall quality of a 2, built in 1946, total finished basement square footage of 407, total above ground square footage of 407, and was sold in 2008 as a normal sale. It has a predicted price of $\$59,801.65$.

Based on the analysis of our model above, we can look at both of these examples with clarity. The price on the first home makes sense according to our model. The large lot area of the home and the total above ground square footage are the big sellers here according to our coefficients. Further, it was built in 2008 making it brand new when this data was collected. Finally, the finished basement square footage of 796 is high and very valuable. We could predict the house would sell for over two hundred thousand. For the second example, we see a significant decrease in predicted price. The kickers here are that the home is old, has a very low overall quality, a smaller above ground square footage and total finished basement square footage. All of these factors together, we can confidently predict a price of only around fifty thousand.

Even if our clients fall into the category of the second home, we can use this information to give our clients both an encouraging look at their potential sell value, and a realistic view of what may happen once their home is on the market.

### Recommendations

According to this model and data, I have several recommendations. To answer our problem statement, we should use our insights to inform our decisions and clients to choose the best listing price for their home. 

If we have a client that lives in the Northbridge Heights or Stone Brook neighborhoods and have a large square footage home, we can predict their house will sell for more money than a client whose house is in another neighborhood or is of a much smaller size. We can use these insights to inform our listing prices for our clients. Our problem was that we wanted to provide more accurate listing prices for our clients trying to sell their homes. I believe the insights learned here can help us get our clients more return for their house sale, and ultimately, more return for our realtor percentage. Other important insights we can help our clients with is that if, for example, they are in a neighborhood that is not Northbridge Heights or Stone Brook, their house may not be currently priced for as much money even if it is of similar quality. However, if they were to finish their basement or screen their porch, their house could potentially sell for much more. These are the ways we can use this data to help our clients. 

Further, if we look inwards, we can direct our marketing strategies to the neighborhoods, or home sizes, or features that sell for higher prices.

### Future Modeling

In a future model, I would like to build several models based on a smaller range of features. I would target categories of data. For example, I would put all square footage related features in one model, all exterior related features in another. I believe this may give us a more pinpointed look at specific features or features that are related to other features. 

### Kaggle Submission

In Notebook #5, you can find my complete Kaggle submission, including formation of my submission dataset.