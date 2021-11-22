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
    - The most accurate model was Random Forest Regression model.  This had a 97% accuracy rate
5. Preliminary model evaluation
    - Linear Regression Model - did not work well - 18%
    - Random Forest Regression Model - 98%
    - Random Forest Classifier - 100% but not sure if model correct
    - Deep Neural Network Model - 0% - did not work at all

**Database development** instructions on how to create the database
- We found that it was not necessary to use a database to clean this dataset.  It could be cleaned directly in Python


**A blueprint of the dashboard**, including:
1. Interactive elements
    - There will not be any interactive elements
2. Tools/technologies for the creating the dashboard
    - Website with model graphs
    - Tableau for graph creation

