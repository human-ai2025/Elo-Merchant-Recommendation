# Observation 
This file shows all the observation I made from the EDA ipynb Notebook

## Train and Test CSV file 
The train dataframe contrains 6 columns which are namely 'first_active_month', 'card_id', 'feature_1', 'feature_2', 'feature_3','target'.
The test dataframe contains 5 columns same as train except the target column.
The train_dict loaded from data dict have the definations of the columns 
The shape of train and test are (201917, 6)
(123623, 5) respectively 
The train and test contains the information about the cards and card id 
The target column is the loyality score which is needed to be predicted 
The first month active column shows us that when did the custumer made its first purchase 
The feature 1,2,3 columns contain card featured which are not given any good explaination of. 
When we plot the histogram plot of the target variable(loyality score) then we find that some of the points are far apart (less than -30) and when we find the percentage of points which are less than -30 it comes out to be 1.093% 
We can see that the distribution of target variiable is like a normal distribution so any point beyond (3 X std) of mean i.e any point out of 99.73 percent of the distribution so 0.3 percent of data could be said as outliners but as it is 1 percent so it might be some kind of rare data. As there is no description given of the feature 1,2,3 so there cannot be any concreat reasoning that why it may be that but one of the hypotheses is that those card holders didnt buy any stuff so their loyality score is very low.
As the metric is RMSE we need to be very carefull of the affect of outlinears. Lets try the experimentation with and without outlinears when we do feature engineering and model prediction.
The distribution of first month active for both train and test is nerly the same to the naked eye. As the distribution is tbhe same the means of splitting need not be time specific cause the distribution is kind of same but if the distribution wouldn't have been the same we would have needed to look at the datasets more to find ut the patterns or maybe join the train and test and split the train ad test based on time.

I ploted the violin distribution of feature 1,2,3.
The IQR and the median looks the same to me and this isnt much difference between the features for the loyality score .The probability density of  distribution looks the same to me,I have no idea how will these features be useful in for the prediction of consumer loyality score but lets see if our linear and non linear based models figure something out. Some feature engineering based on the feature 1,2,3 might help but we will look more into it in the feature engineering part  

## Historical Transactions CSV files 
The historical transaction datafame has 14 columns which are namely
'authorized_flag', 'card_id', 'city_id', 'category_1', 'installments','category_3', 'merchant_category_id', 'merchant_id', 'month_lag','purchase_amount', 'purchase_date', 'category_2', 'state_id','subsector_id' with 29112361 data samples 
The historical transactions have the historical transactions for each card id 
The hist dict loaded from data dict contain the definations of the colmns 
The card id have the card identifier code type thing.
The month lag refers to month lag to reference date
The purchase date shows th purchase date 
The authorized flag saying which all tranactions were approved and which all were denied 
Category 1,2,3 is the anonmized category 
installments says the number of insttallments for the given purchase
The purchased amount is normalized 
Rest all are some kind of identifiers for id for ciity, merchands,etc.
When we try to see the percent of approval rate we find that 91.35 percent of transactions were approved and if we furthur try to see the approval rate based on card id, we find that for some card id most of the transactions were denied. So that got me curious to find out how many percent od card users had an approval rate of less than 10 percent, and it came out t be less than 0.007 percent of users. So what I think is those users were mainly using the card for fradulent transactions and hence the card was not accepted majority of the times and 60 percent of the users have an approval rate more than 90 percent
After seeing the approval rate, we went over to see the installments columns and what we found there was a bit confusing, threre were -1 and 999 type of installments too. I highly doubt that it was installments rather it must be used to handle missing values. but when we grouped the installments and authorized part and found the approval rate based on installlments, we think that 999 must be a label for fradulent transaction installment and -1 is still and big question mark.
After the installments colums we went on to the purchase amount, but has the purchase amount as heavily standardized, we couldnt draw much of information, but what we found was the 99th percentile and 100th percentile of purchase value was a bit fishy more specifically the 100th one it was way too much off the charts 
The category 1,2,3 are anonymized categories. 
The category 1 has N and Y
The category 2 has 1., nan,  3.,  5.,  2.,  4.
The category 3 has 'A', 'B', 'C', nan
There are 308 unique values in city_id.
There are 327 unique values in merchant_category_id.
There are 326311 unique values in merchant_id.
There are 25 unique values in state_id.
There are 41 unique values in subsector_id.

## New Merchant Transactions 
The new merchant transactions dataframe have 14 columns namely
'authorized_flag', 'card_id', 'city_id', 'category_1', 'installments','category_3', 'merchant_category_id', 'merchant_id', 'month_lag','purchase_amount', 'purchase_date', 'category_2', 'state_id','subsector_id' and the definations of the columns are the same as the historical transactions dataframe with 1963031 data samples 
There are 308 unique values in city_id.
There are 314 unique values in merchant_category_id.
There are 226129 unique values in merchant_id.
There are 25 unique values in state_id.
There are 41 unique values in subsector_id.
These are same as the historical transaction one
The category 1,2,3 are anonymized categories. 
The category 1 has N and Y
The category 2 has 1., nan,  3.,  5.,  2.,  4.
The category 3 has 'A', 'B', 'C', nan
The historicl transactions and the new merchant transactions are kind of the same 

