# Spotify Top 200

## Project Goal
Can we predict the total number of weeks a song charted based on the songs metrics? Can we predict the total number of streams based on the song metrics?

### Song metrics 
    - Highest Charting Position
    - Number of Times Charted
    - Artist Followers
    - Genre
    - Popularity
    - Danceability
    - Energy
    - Loudness
    - Speechiness
    - Acousticness
    - Liveness
    - Tempo
    - Duration
    - Valence


## Data Description
The data contains a list of the songs that have reached the Spotify Top 200 Weekly (Global) Chart in 2020 and 2021. Included in the data are metrics regarding how popular, danceable, loud, etc the songs are as well as the artist and genre. We retreived the data from Kaggle, [here.](https://www.kaggle.com/sashankpillai/spotify-top-200-charts-20202021)

### Cleaning of the data
We used Jupyter Notebooks and
    - Deleted unnecessary date columns
    - Deleted null value rows
    - Changed the datatype from 'object' to int64 or float64
    - Changed Streams column to number (this eliminated the commas in data)
    - Changed the Genre column to only contain 1 genre category - there was originally a list of genres in this column


## Model Evaluation

### Linear Regression
Earlier we determined that the Linear Regression Model would most likely not work.  We were not able to find any linear relationship between Streams and any of the Features.  Therefore we weren't surprised when the Linear Regression Model showed such a poor outsome. The R2 score for the Linear Regression Model was .17

### Random Forest Regression
This model was clearly the best performing model.  The n_estimators value was set at 50, after processing at 50, 100, 150, etc...  It was determined that there was not a significant difference in performance based on changing the value. Our output shows that the Predicted Streams and Actual Streams are quite close.  We were able to predict the number of Streams based off of the features with a pretty High accuracy. Our R2 value was .83 showing that the regression model fit well. The closer to 1, the better.

### Random Forest Classifier
This model showed that it was not a good model.  It's R2 score was 0.0, showing that it did not fit well.  The output indicates better results, but since the score was bad, we did not use this model.

### Deep Neural Network
This model used an Input Layer with relu activation (150 neurons) and 3 hidden layers, also using relu activation (250 neurons). Checkpoints were created for callback and the model was compiled and trained. Finally, we evaluated the model for accuracy.  The accuracy was also at 0.0 indicating that this model does not work at all on this dataset.


## Results
The best model in this analysis is the Random Forest Regression model.  It showed the best fit at an R2 score of .82.  It also predicted a fairly accurate Streaming values, indicating that we can predict the number of streams from the features in the dataset.


## Dashboard Overview
The dashboard can be found [here](https://natemeyer001.github.io/final_project_3/)

It includes a tab for .....
