# final_project_3

## Segment 1 Deliverables
**Selected topic:** Spotify Top 200 Charted Songs

**Description of data source:** The data contains a list of the songs that have reached the Spotify Top 200 Weekly (Global) Chart in 2020 and 2021. Included in the data are metrics regarding how popular, danceable, loud, etc the songs are as well as the artist and genre. We retreived the data from Kaggle, [here.](https://www.kaggle.com/sashankpillai/spotify-top-200-charts-20202021)

**Question we hope to answer:** Can we predict the total number of weeks a song charted based on the songs metrics?

**Database engine:** PostgreSQL

**Initial list of tables and columns:** 

![ERD](https://user-images.githubusercontent.com/86527135/141697695-b8f34735-16cf-45ce-84f9-775b792850ca.PNG)

**Machine learning model:** Multiple linear regression.

**Live predictions:** No, but will maybe attempt for extra credit.

**Roles:**
- Square: Nate
- Triangle: Kathy
- Circle: Urte
- X: Sunisa

## Segment 2 Deliverables
**Initial ML model is developed** Must have a Jupyter notebook containing:
1. Description of preliminary data pre-processing: 
    - Data was cleaned using Python in Jupyter Notebook. 
    - This included deleting unnecessary date columns
    - Deleted null value rows
    - Changed the datatype from 'object' to int64 or float64
    - Changed column names to include underscores so no spaces
    - Changed Streams column to number (this eliminated the commas in data)
    - Changed the Genre column to only contain 1 genre category - there was originally a list of genres in this column
    - Pre-processsing: We loaded the data into a Jupyter notebook with Pandas' read_csv, and the displayed the head and the tail. We noticed some blanks in the columns "Genre", and "Popularity", so we droped those rows. After that we looked at the data types and saw they were mostly objects. For the analysis we need them to be numbers, so we used pd.to_numeric() to do the conversion. Lastly, we tackled the "Genre" column, which started as a list of all genres that the song belonged to. Our goal was to reduce each list to a single item, and then generalize categories to reduce the number of genres. We accomplished this by checking the list of genres for each song to see if any of the elements contained a certain sub-string, and if they did we replaced the list of genres with a single genre that best described the song. We ended up with 9 categories for the 1,470 songs in our cleaned DataFrame.
2. Description of features used in the model
    - Our Target was Streams
    - Features include: 
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
3. Description of how data was split for training/testing
    - Data was split using train_test_split
    - 25% of dataset was used for testing
    - 75% of dataset was used for training
4. Explanation of model choice, including benefits and limitations
    - Originally thought we would use Multiple Linear Regression, but there didn't seem to be any linear regression between Streams and the other features.  If we were only testing Danceability, or Popularity, we could possibly use Multiple Linear Regression.  But we were determining if we could predict the number of Streams based off of the features.
    - We found that linear regression was a terrible model for Streams
    - The most accurate model was Random Forest Regression model.  This had a R2 score of .82
5. Preliminary model evaluation
    - Linear Regression Model - did not work well - .18
    - Random Forest Regression Model - .82 -  best overall model evaluation
    - Random Forest Classifier - 0.0 but not sure if model correct
    - Deep Neural Network Model - 0.0 - did not work at all

**Database development** instructions on how to create the database
- We found that it was not necessary to use a database to clean this dataset.  It could be cleaned directly in Python


**A blueprint of the dashboard**, including:
1. Interactive elements
    - There will not be any interactive elements
2. Tools/technologies for the creating the dashboard
    - Website with model graphs
    - Tableau for graph creation
3. As of now, the interactive elements that will be used are menu buttons that will take the audience to different sections of the webpage. Sections that will be included are: about, which explains the data used, why it was used, and some information on the data as well as where it was obtained from, section/button for machine learning model, contact us section for information about the group members, and if live prediction is attempted then there will be a section/page for it as well. The dashboard which will be created using Tableau will be incorporated in the webpage as well.




## Segment 3 Deliverables
### Cleaning the Data
- Data was primarily cleaned prior to processing, using Python and Excel. Description is listed prior.  Our feature datatypes were verified to be int64 or float64 vs. object.

INSERT IMAGE clean_data

![clean_data](https://github.com/natemeyer001/final_project_3/blob/kathy/images/clean_data.png)


### Visualize the Data
- We will be using Tableau to show:

    - Top Streamed Artists

    INSERT image code artist_code
    ![artist_code](https://github.com/natemeyer001/final_project_3/blob/kathy/images/artist_code.png)
    
    
    INSERT image graph artist_graph
    ![artist_graph](https://github.com/natemeyer001/final_project_3/blob/kathy/images/artist_graph.png)
    
    - Top Streamed Genres

    INSERT image graph genre_graph
    ![genre_graph](https://github.com/natemeyer001/final_project_3/blob/kathy/images/genre_graph.png)

    - Top Charted Songs

    INSERT image code songs_code
    ![songs_code](https://github.com/natemeyer001/final_project_3/blob/kathy/images/songs_code.png)
    INSERT image graph songs_graph
    ![songs_graph](https://github.com/natemeyer001/final_project_3/blob/kathy/images/songs_graph.png)
    
### Preprocessing
- Additional cleaning - drop more columns
 INSERT image pre_clean
 ![pre_clean](https://github.com/natemeyer001/final_project_3/blob/kathy/images/pre_clean.png)

- Encode Genre using LabelEncoder() - this will change values from object to a number
INSERT image pre_encode
![pre_encode](https://github.com/natemeyer001/final_project_3/blob/kathy/images/pre_encode.png)

- Split data into Training and Testing Sets
INSERT image pre_split
![pre_split](https://github.com/natemeyer001/final_project_3/blob/kathy/images/pre_split.png)

- Our Target is the Stream column.  The Stream column needs to be dropped from the X_train and X_test, which contains the features.
INSERT image pre_drop
![pre_drop](https://github.com/natemeyer001/final_project_3/blob/kathy/images/pre_drop.png)

### Model Evaluation
#### Linear Regression
Earlier we determined that the Linear Regression Model would most likely not work.  We were not able to find any linear relationship between Streams and any of the Features.  Therefore we weren't surprised when the Linear Regression Model showed such a poor outsome.

The R2 score for the Linear Regression Model was .17

INSERT image liner_regression_model
![liner_regression_model](https://github.com/natemeyer001/final_project_3/blob/kathy/images/liner_regression_model.png)

#### Random Forest Regression
This model was clearly the best performing model.  The n_estimators value was set at 50, after processing at 50, 100, 150, etc...  It was determined that there was not a significant difference in performance based on changing the value. 

Our output shows that the Predicted Streams and Actual Streams are quite close.  We were able to predict the number of Streams based off of the features with a pretty High accuracy.  Our R2 value was .83 showing that the regression model fit well. The closer to 1, the better.

INSERT image random_forest_regression
![random_forest_regression](https://github.com/natemeyer001/final_project_3/blob/kathy/images/random_forest_regression.png)

#### Random Forest Classifier
This model showed that it was not a good model.  It's R2 score was 0.0, showing that it did not fit well.  The output indicates better results, but since the score was bad, we did not use this model.

INSERT image random_forest_class
![random_forest_class](https://github.com/natemeyer001/final_project_3/blob/kathy/images/random_forest_class.png)

#### Deep Neural Network
This model used an Input Layer with relu activation (150 neurons) and 3 hidden layers, also using relu activation (250 neurons). 

INSERT image nn_model
![nn_model](https://github.com/natemeyer001/final_project_3/blob/kathy/images/nn_model.png)


Checkpoints were created for callback and the model was compiled and trained.

INSERT image nn_model_compile
![nn_model_compile](https://github.com/natemeyer001/final_project_3/blob/kathy/images/nn_model_compile.png)

Finally, we evaluated the model for accuracy.  The accuracy was also at 0.0 indicating that this model does not work at all on this dataset.

INSERT image nn_model_evaluate
![nn_model_evaluate](https://github.com/natemeyer001/final_project_3/blob/kathy/images/nn_model_evaluate.png)

### Model Evaluation
The best model in this analysis is the Random Forest Regression model.  It showed the best fit at an R2 score of .82.  It also predicted a fairly accurate Streaming values, indicating that we can predict the number of streams from the features in the dataset.