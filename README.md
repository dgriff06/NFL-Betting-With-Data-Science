# NFL Betting with Data Science

## *Project Overview*
Package Requirements and Versions
pip install x ; where 'x' is the package listed below:


`python == 3.7.13+`

`numpy == 1.21.5`

`pandas == 1.3.5+`

`hvplot == 0.7.3`

`matplotlib == 3.5.1`

`json == 2.0.9`

`sportsreference == 0.5.2`

`sklearn


## *Files Navigation*

*Resources:* 
Directory containing all images of plots created in Jupyter Notebook, and original csv data files.

*Team_Stats_Game_Stats_Combined_DF.ipynb* :
Creating a CSV file to build our Dataframe from, using the sports reference API

*RF_XGB_Sequential_Models.ipynb* :  Data exploration investigating csv files and API connections, cleanup of dataframes, and final dataframes and all graphs.

## *Project Overview*

The general purpose of this project was to pose as professional sports betters and see if we could use data science to algorthimically place bets. Ultimately, our team decided to create a data science model to predict who would win based on any match-up of two teams in the NFL. 

The initial challenge was identifying data that would be suffienct to train and test our model. Sports data is expensive and some of the sources we explored cost thousands of dollars. Ultimately, we settled on using the `sportsreference` library, a free python API that pulls the stats from www.sports-reference.com and allows them to be easily be used in python-based applications. The `sportsreference` library contains multiple dataframes, but we focused on `boxscores` (game stats) and `teams` (team stats). 

To create our dataframe we pulled all of the game data from the `boxscores` dataframe for the past 10 years. Then we pulled all of the team stats from the `teams` dataframe. To combine the 2 dataframes, for each game played we identified the home team (team 1) and the away team (team 2). We then appended the statistics from the `teams` data frame on to each game line item. The combined data frame contained the team stats for both teams playing eachother in every game for the past 10 years. 

Unfortunately it was a limitation of the `sportsreference` library that the `teams` dataframe only contains statistics for the current season. In a future iteration of the project if there was money to invest in data, our team would recomend using team statistcs that are representative of the time period the games are taking place in.  

After creating our combined dataframe we then created a column that indicated if the home team won or lost each match up. This became our 'y' column, or the target we are trying to predict. We removed any columns from the dataframe that were not numeric and this became our 'X' data frame, of the data frame of known values we will use to train our model. 

We then applied a `standard scaler` to our data frame to make sure that all values are relative. After that we applied a `train test split` where random 80% of our data frame was selected to train our model and 20% was reserved to test our model. We then fit the model to our data. The models we used were `Random Forrest` and `xgBoost`. 

## *Visuals and Explanations*

All graphs not included here can be found in the Resources folder or in *RF_XGB_Sequential_Models.ipynb*.

**Random Forest**

Our first model, Random Forest, considered is a meta estimator. It fits decision tree classifiers on various sub-samples of a given dataset and uses averaging to improve the predictive accuracy and control over-fitting. 

Our Random Forest Model initially made predictions with 57% accuracy, so we started with a result that was better than random.
Scalers - For the first iteration of this model, we applied sklearn's Standard Scaler. For the following iterations, we applied the Min Max and Robust Scalers. 
Train Test Split adjustments - For the first iteration of our model applied Train Test Split with the default settings, and for subsequent tests we  tweaked the ratio to account for 70/30 and 75/25 splits.

 **Feature Importance**

By using using the random forest feature importance function we can determine what inputs allow our model to give the best output
We dropped the unimportant features and re-ran the model to see if this would change our model score. 
The model score remained roughly the same. Dropping features is more important when you have a model with lots of rows, as dropping features that don't matter will speed up model efficiency. 

**xgBoost**

Our second model, XGBoost, is an optimized distributed gradient boosting library. It's designed to be highly efficient, flexible, portabl and implements machine learning algorithms under the Gradient Boosting framework.

“Boosting” - improving a single weak model by combining it with a number of other weak models in order to generate a collectively strong model. xgBoos is east to use, accounts for missing data, and prevents overfitting. The accuracy of this model was 54%. 

**TensorFlow Sequential**

Our final model, Tensorflow Sequential, can be implemented by using Sequential API and follows a step-by-step methedology while building the model and working on a single layer at a particular time. Sequential models are appropriate for a plain stack of layers where each layer has exactly one input tensor and one output tensor. 

Using this model allowed us to take a lot at how our predictions bare out when we take a Deep Learning approach, rather than relying strictly on machine learning. Ater some tuning, we were able to produce a 56.8 percent accuracy score using this model. 


## *Conclusion*

Each of our models gave us roughly the same result, as we saw our winner being correctly predicted with anywhere between 54 and 57 percent accuracy. While this result is better than random, it does not give us the confidence to risk our money as as proffessional sports betters, and has to be improved before it can be used in that way. 

The key to improving our results is improving our data. We recognize this because we obsevered minimal changes to the accuracy of our models while tuning them for better results. The data that would have been most effective for us is very popular for commercial applications and thus hard to find without getting behind a significant paywall. We also recognize that the major flaw with our data, is that we are relying on cumulative season stats, rather than the individual stats of the games that were used to create our binary target of win or loss.

Had we not faced challenges with the accessibility of our data, we would have like to focus on play-by-play data that tells the full story of what happened during each game. With this information, we would have many more features to feed into our models, and something like feature importance could be used more effectively to fine tune our results. We would ideally account for statics like: number of plays, yards per play, 3rd down efficiency, and average points per drive. There has also been extensive research done on metrics that account for the value of an individual player, or a particular unit for a given team. One such metric called, Expected Points Added (EPA), is very popular for measuring the effectiveness of a given team's offensive unit. If a metric like this was avaibable to include in our dataset, we could weigh it against our other features and use it as a multiplier to account for the predicted outcome of a given game. 

As proffesional betters, another path forward would be to shift our focus away from expensive data that helps us predict a winning team, and more towards data that helps us identify a winning bet. With the recent legalization of sports betting for NFL games, there is fresh and lively market of betters that sportsbooks are trying to service. This suggests that there is data available on what makes for a good bet, so we could theoretically shift our focus to idenfiying betting lines that have the best chance of hitting for the highest returns at the lowest levels of risk. Building our models this way would allows us to focus on our bottom line, while pivoting within our desired domain.

We plan to continue improving this project by taking such measures, and finding the best available data to make predictions with. 

## *References*
- https://pypi.org/project/sportsreference/
- https://www.sports-reference.com/
- https://medium.com/clarktech-sports/python-sports-analytics-made-simple-part-2-40e591a7f3db


## *Team Members:*
- Darius Griffin (Project Manager)
- Yohan Hwang
- Drew Haggerty
- Beck Davranov
- Cynthia Davis

!!!