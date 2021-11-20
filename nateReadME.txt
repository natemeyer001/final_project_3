1) Pre-processsing: We loaded the data into a Jupyter notebook with Pandas' read_csv, and the displayed the head and the tail. We noticed some blanks in the columns "Genre", and "Popularity", so we droped those rows. After that we looked at the data types and saw they were mostly objects. For the analysis we need them to be numbers, so we used pd.to_numeric() to do the conversion. Lastly, we tackled the "Genre" column, which started as a list of all genres that the song belonged to. Our goal was to reduce each list to a single item, and then generalize categories to reduce the number of genres. We accomplished this by checking the list of genres for each song to see if any of the elements contained a certain sub-string, and if they did we replaced the list of genres with a single genre that best described the song. We ended up with 9 categories for the 1,470 songs in our cleaned DataFrame.


2) Features used: To start we are going to run Mutiple Linear Regression with Number of Times Charted as the target. Our features will be: Highest Charting Position, Streams, Artist Followers, Genre, Popularity, Danceability, Energy, Loudness, Speechiness, Acousticness, Liveness, Tempo, Duration (ms), Valence, Chord.

We will likely also run MLR with Streams as the target with the same features as above, except with Number of Times Charted as a feature instead of target, and Streams as only a target.


3) How data was split: We used the scikit-learn function train_test_split() to separate the data for training and testing. We did not alter the default split percentage of 75% for training.

