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
Directory containing all images of plots created in Jupyter Notebook, and original csv data files can be located at -

*XXXX.ipynb:* 
Data exploration investigating csv files and API connections, cleanup of dataframes, and final dataframes and all graphs.

## *Project Overview*

The general purpose of this project was to pose as professional sports betters and see if we could use data science to algorthimically place bets. Ultimately, our team decided to create a data science model to predict who would win based on any match-up of two teams in the NFL. 

The initial challenge was identifying data that would be suffienct to train and test our model. Sports data is expensive and some of the sources we explored cost thousands of dollars. Ultimately, we settled on using the `sportsreference` library, a free python API that pulls the stats from www.sports-reference.com and allows them to be easily be used in python-based applications. The `sportsreference` library contains multiple dataframes, but we focused on `boxscores` (game stats) and `teams` (team stats). 

To create our dataframe we pulled all of the game data from the `boxscores` dataframe for the past 10 years. Then we pulled all of the team stats from the `teams` dataframe. To combine the 2 dataframes, for each game played we identified the home team (team 1) and the away team (team 2). We then appended the statistics from the `teams` data frame on to each game line item. The combined data frame contained the team stats for both teams playing eachother in every game for the past 10 years. 

Unfortunately it was a limitation of the `sportsreference` library that the `teams` dataframe only contains statistics for the current season. In a future iteration of the project if there was money to invest in data, our team would recomend using team statistcs that are representative of the time period the games are taking place in.  

After creating our combined dataframe we then created a column that indicated if the home team won or lost each match up. This became our 'y' column, or the target we are trying to predict. We removed any columns from the dataframe that were not numeric and this became our 'X' data frame, of the data frame of known values we will use to train our model. 

We then applied a `standard scaler` to our data frame to make sure that all values are relative. After that we applied a `train test split` where random 80% of our data frame was selected to train our model and 20% was reserved to test our model. We then fit the model to our data. The models we used were `Random Forrest` and `xgBoost`. 

## *Visuals and Explanations*

All graphs not included here can be found in the Resources folder or XXXXX.ipynb.

**Random Forrest**

Our Random Forest Model initially made predictions with 57% accuracy, so we started with a result that was better than random.
Scalers - For the first iteration of this model, we applied sklearn's Standard Scaler. For the following iterations, we applied the Min Max and Robust Scalers. 
Train Test Split adjustments - For the first iteration of our model applied Train Test Split with the default settings, and for subsequent tests we  tweaked the ratio to account for 70/30 and 75/25 splits.

 **Feature Importance**

  By using using the random forest feature importance function we can determine what inputs allow our model to give the best output
We dropped the unimportant features and re-ran the model to see if this would change our model score. 
 The model score remained roughly the same. Dropping features is more important when you have a model with lots of rows, as dropping features that don't matter will speed up model efficiency. 

**xgBoost**

 Gradient boosted decision tree
“Boosting” - improving a single weak model by combining it with a number of other weak models in order to generate a collectively strong model. The accuracy of this model was 54%. 


## *Conclusion*


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