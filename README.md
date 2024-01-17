
Used yahoo finance api to see sp500 data throughout the years


Got rid of dividends and stock splits columns because those are more for individual stocks


Created a target column to see if the tomorrow price is greater than today


Got rid of sp500 stock pre price pre 1990 because if you go too far back into the market data you might not have an accurate amount of information when creating a machine learning model because the market could fundamentally shift and change



Random Forest algorithm work by training a bunch of individual decision trees with randomized parameters and then averaging those results from those decision trees
Because of this process random forest are resistant to overfitting, they can over fit but it’s    harder for them to overfit than other models 
Overfitting: In mathematical modeling, overfitting is "the production of an analysis that corresponds too closely or exactly to a particular set of data, and may therefore fail to fit to additional data or predict future observations reliably".

They run relatively quickly 
They can pick up non linear tendencies in the data
For example the open price is not linearly correlated with the target (If the open price is 4000 vs 3000, there is no linear relationship with the open price and target. If the open price is higher that doesn’t mean the target will also be higher)


N_estimators is the number of individual decision trees you want to train (the higher the better your accuracy up to a limit)
min_samples_split protects against overfitting because decision trees tend to overfit (The higher the less accurate the model will be but the less it will over fit, play around with the number)
Random_state means if we run the same model twice the random numbers generated will be in a predictable sequence using the random seed of 1 (Helps with updating and improving model)


We want the model to actually learn how to predict the stock price not just randomly happen to have some knowledge about the future which we won’t have in the real world


Our predictors are 


This is going to train the model using the predictors "Close", "Volume", "Open", "High", "Low"


Precision score is saying what percentage of the time when we said the market would go up did it actually go up 
Very good error/accuracy metric for this particular case because in this case we want to buy stock, hold that stock, and sell it and when we buy the stock the value will increase


Plot predictions by combining actual values vs predicted values




The graph plotted with orange and blue. Orange is what we predicted, blue is what actually happened





Simply created a function of everything that was done prior to making a prediction model by simply putting it into a function





We’re going to take the first 10 years of data and predict values for the 11th year, then after we will take the first 11 years of data and predict the 12th year and so on (We will get a lot of different predictions for a lot of years)
When you back test you want to have a certain amount of data to train your first model, and every trading year has 250, so start is saying to take 10 years of data and train your first model with 10 years of data
Step is 250 which means we will be training a model for about a year and then the next and so on 



Will predict the probability of a row being either a 0 or 1 (Will stock price go up or down)


Setting a threshold to 60 percent, meaning the model has to be confident the price will go up, to show that the price will go up (Will reduce number of trading days)


