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

1) Pre-processsing: We loaded the data into a Jupyter notebook with Pandas' read_csv, and the displayed the head and the tail. We noticed some blanks in the columns "Genre", and "Popularity", so we droped those rows. After that we looked at the data types and saw they were mostly objects. For the analysis we need them to be numbers, so we used pd.to_numeric() to do the conversion. Lastly, we tackled the "Genre" column, which started as a list of all genres that the song belonged to. Our goal was to reduce each list to a single item, and then generalize categories to reduce the number of genres. We accomplished this by checking the list of genres for each song to see if any of the elements contained a certain sub-string, and if they did we replaced the list of genres with a single genre that best described the song. We ended up with 9 categories for the 1,470 songs in our cleaned DataFrame.


2) Features used: To start we are going to run Mutiple Linear Regression with Number of Times Charted as the target. Our features will be: Highest Charting Position, Streams, Artist Followers, Genre, Popularity, Danceability, Energy, Loudness, Speechiness, Acousticness, Liveness, Tempo, Duration (ms), Valence, Chord.

We will likely also run MLR with Streams as the target with the same features as above, except with Number of Times Charted as a feature instead of target, and Streams as only a target.


3) How data was split: We used the scikit-learn function train_test_split() to separate the data for training and testing. We did not alter the default split percentage of 75% for training.

BLUEPRINT:

1. As of now, the interactive elements that will be used are menu buttons that will take the audience to different sections of the webpage. Sections that will be included are: about, which explains the data used, why it was used, and some information on the data as well as where it was obtained from, section/button for machine learning model, contact us section for information about the group members, and if live prediction is attempted then there will be a section/page for it as well. The dashboard which will be created using Tableau will be incorporated in the webpage as well.
