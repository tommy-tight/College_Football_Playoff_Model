# College Football Playoff Predictive Model 

## Data
In order to make this model, I used college football data from the [College Football Data API](https://api.collegefootballdata.com/api/docs/?url=/api-docs.json). The Data that was prepared by Grant Exley [Github: @grantexley](https://github.com/grantexley) and can be found in [his college football model repository](https://github.com/grantexley/college_football_model). The data gathered was very large so the first thing I did was clean the data and perform variable selection. To perform variable selection, I wanted to remove variables that were highly correlated with each other to account for and eliminate the possibility of multicollinearity. However, after taking this approach there were still too many variables remaining in the data. To perform further variable selection, I ran a simple XGBoost model that returned the top 20 features to use in my model. 

## Model
To create the prediction model, I used an XGBoost model. The XGBoost model creates decision trees that are created sequentially where each one reduces the error from the last tree. Within the model, I performed hyperparameter tuning that optimizes the parameters of the decision trees within the XGBoost model. I trained the model on older data and then tested it on newer data to evaluate its performance. The model performed very well when tested on the validation data, with an accuracy of 79%, meaning it correctly predicted the outcome 79% of the time. Additionally, the model had weighted average precision, recall, and F1-scores of 0.79, further indicating that it is able to accurately and consistently predict the winners of college football games. This model was created in the file Tommy_Tight_cfp_xgboost.ipynb and was run in Google Collab.

 ## Results and Bracket
After creating and training the model, I then used it to make my predictions for the CFP. I wrote code to allow the user to input a home team and an away team and the model will return which team it predicts to win as well as the probability of winning. I used this function to create my playoff bracket. Since I had to choose a home team and an away team, but some of the games were played at neutral sites, I just made the home team the team with the higher seed. This shouldn’t affect the decisions too much as whether the team was home or away was not one of the top 20 model features, so home-field advantage was not included in the model. Overall, my model predicted Notre Dame would win the CFP. There are also power rankings for all the teams based on the XGBoost model. The entire bracket predicted by the model can be found in finished_bracket.pdf.
