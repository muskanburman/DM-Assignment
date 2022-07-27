# Data-Management-for-Data-Science

hw3.zip:

Problem 1: EU Cities Temperatures Dataset 
Given a CSV data file as represented by the sample file EuCitiesTemperatures.csv  Download EuCitiesTemperatures.csv (213 records), load it into a Pandas DataFrame and perform the following tasks on it.

Important: Your code should be applicable to any extension of this sample, so make sure you don't hardcode anything that applies only to the values in this dataset.

Preprocessing/Analysis 
Fill in the missing latitude and longitude values by calculating the average for that country. Round the average to 2 decimal places.
Find out the subset of cities that lie between latitudes 40 to 60 (both inclusive) and longitudes 15 to 30 (both inclusive). Find out which countries have the maximum number of cities in this geographical band. (More than one country could have the maximum number of values.)
Fill in the missing temperature values by the average temperature value of the similar region type. A region type would be a combinaton of whether it is in EU (yes/no) and whether it has a coastline (yes/no).
For example, if we have a missing temperature value for Bergen, Norway, which is not in the EU but lies on the coast, we will fill it with the average temperature of cities with EU='no' and coastline='yes')

Visualization 
For all plots, make sure to label the axes, and set appropriate tick labels.

Plot a bar chart for the number of cities belonging to each of the regions described in Preprocessing/Analysis #3 above.
Plot a scatter plot of latitude (y-axis) v/s longitude (x-axis) values to get a map-like visual of the cities under consideration. All the cities in the same country should have the same color.
The population column contains values unique to each country. So two cities of the same country will show the same population value. Plot a histogram of the number of countries belonging to each population group: split the population values into 5 bins (groups).
Plot subplots (2, 2), with proper titles, one each for the region types described in Preprocessing/Analysis #3 above.
Each subplot should be a scatter plot of Latitude (y-axis) vs. City (x-axis), where the color of the plot points should be based on the temperature values: ‘red’ for temperatures above 10, ‘blue’ for temperatures below 6 and ‘orange for temperatures between 6 and 10 (both inclusive). For each subplot, set xticks to an array of numbers from 0 to n-1 (both inclusive), where n is the total number of cities in each region type. This represents each city as a number between 0 and n-1.

Problem 2: German Credit Dataset 
Given a CSV data file as represented by the sample file GermanCredit.csv  Download GermanCredit.csv (1000 records), load it into a Pandas DataFrame, and perform the following tasks on it.

Important: Your code should be applicable to any extension of this sample, so make sure you don't hardcode anything that applies only to the values in this sample.

Preprocessing 
Drop the 3 columns that contribute the least to the dataset. These would be the columns with the highest number of non-zero 'none' values. Break ties by going left to right in columns. (Your code should be generalizable to drop n columns, but for the rest of the analysis, you can call your code for n=3.)
Certain values in some of the columns contain unnecessary apostrophes (‘). Remove the apostrophes.
The checking_status column has values in 4 categories: 'no checking', '<0', '0<=X<200', and '>=200'. Change these to 'No Checking', 'Low', 'Medium', and 'High' respectively.
The savings_status column has values in 4 categories: 'no known savings', '<100', '100<=X<500', '500<=X<1000', and '>=1000'. Change these to 'No Savings', 'Low', 'Medium', 'High', and 'High' respectively. (Yes, the last two are both 'High').
Change class column values from 'good' to '1' and 'bad' to '0'
Change the employment column value 'unemployed' to 'Unemployed', and for the others, change to 'Amateur', 'Professional', 'Experienced' and 'Expert', depending on year range.

Analysis
For the following tasks, do preprocessing or changing of data types in the data frame as required.

Often we need to find correlations between categorical attributes, i.e. attributes that have values that fall in one of several categories, such as "yes"/"no" for attr1, or "low","medium","high" for attr2.
One such correlation is to find counts in combinations of categorial values across attributes, as in how many instances are "yes" for attr1 and "low" for attr2. A good way to find such counts is to use the Pandas crosstab (Links to an external site.) function. Do this for the following two counts.

Get the count of each category of foreign workers (yes and no) for each class of credit (good and bad).
Similarly, get the count of each category of employment for each category of saving_status.
 

Find the average credit_amount of single males that have 4<=X<7 years of employment. You can leave the raw result as is, no need for rounding.
Find the average credit duration for each of the job types. You can leave the raw result as is, no need for rounding.
For the purpose 'education', what is the most common checking_status and savings_status? Your code should print:
    Most common checking status: ...
    Most common savings status: ...

Visualization
 

Plot subplots of two histograms: one with savings_status on the x-axis and personal_status as different colors, and another with checking_status on the x-axis and personal_status as different colors.
For people having credit_amount more than 4000, plot a bar graph which maps property_magnitude (x-axis) to the average customer age for that magnitude (y-axis).
For people with a "High" savings_status and age above 40, use subplots to plot the following pie charts:
Personal status
Credit history
Job
Problem 3: Google Playstore Apps Dataset 
Given an Excel data file as represented by the sample file GooglePlaystore.xlsx  Download GooglePlaystore.xlsx (10K records), load it into a Pandas DataFrame (use the Pandas read_excel method), and perform the following tasks on it.

Important: Your code should be applicable to any extension of this sample, so make sure you don't hardcode anything that applies only to the values in this sample.

Preprocessing 
 

Often there are outliers which do not match the overall data type. There is one record in this data where the "Reviews" has value "3.0M" which does not match the rest of the data. Remove that record.
Remove rows where any of the columns has the value "Varies with device".
The values in the Android version column should be floats. Strip the trailing non-numeric characters from all values (ie. the words " and up"), so the result is a number. If there are multiple decimal places (eg. "x.y.z"), keep only the first two parts (eg "x.y"). For example, the value "4.1 and up" should be changed to "4.1". The value "4.5.6 and up" should be changed to "4.5". The value "5.6.7" should be changed to "5.6". If there is a range (eg. 5.0 - 8.0), only consider the first number. For example, the value "5.0 - 8.0" should be changed to "5.0". The value "4.0.3 - 7.1.1" should be changed to "4.0".
The "Installs" column must have integer values. For values that have commas, remove the commas. For values that have a '+' at the end, remove the '+'. Keep only those rows that have an integer value after these edits.
For missing rating values, if the number of reviews is less than 100 and installations is less than 50000, remove the row. Else, fill the missing value with the average value (rounded to 2 decimal places) for the Category of that row.
reprocess the Size column to convert the "M" (millions) and "K" (thousands) values into integers. For instance, 8.7M should be converted to 8700000 and 2.4K should be converted to 2400.
Analysis 
For the following tasks, do preprocessing or changing of data types in the data frame as required.

Describe (use DataFrame describe method) the category wise rating statistics. In other words, for each category, describe the statistics (count, mean, etc.) for ratings in that category.
Extract all "Free" apps from the master data frame. Then write a function that, given a numeric column e.g 'Rating'), will create and return a dataframe for the top 3 free applications in each category based on that column. Call the function on each of these columns:
Rating (gives top 3 most highly rated applications in each category)
Installs (gives top 3 most installed applications in each category)
Reviews (gives top 3 most reviewed applications in each category)
You don't need to do anything explicit to break ties.

Each of the returned dataframes have Category and App for the first two columns, and one of Rating (for a.), Installs (for b.), and Reviews (for c.) as the third column.

Find the average, maximum and minimum price of the paid applications.
 

Visualization 
In the genre column, break the string of genres into a list. For example, ‘Art & Design; Creativity’ should be [‘Art & Design’, Creativity’].
Count the number of applications per genre and display it using a pie chart.
Hint: Read about DataFrame.explode()

Display a box plot of ratings for "Business" and "Education" categories. The boxplots should be in the same plot.


music_db.pdf:

Implement a Music relational (SQL) database, of the kind that might be used by Spotify or Amazon Music. The database has artists, albums, songs, users, playlists, and ratings.

Type up all the required work specified in the following sections in any word processor, then convert to a PDF file named music_db.pdf. (Handwritten work is NOT acceptable.) Submit this file to Canvas - only one submission per group, please.

You are allowed up to 3 submissions, only the last submission will be graded.

NOTE: You may populate the tables with data for your own testing, but we do not want you to turn in any of the data, or the results of any of your queries. We are only asking for the document with the required SQL statements for table creation and queries.

Database Schema
You are given the following description of the entities that need to be stored in the database. Your task is to design a database schema (set of tables) to store these entities.

Your schema must be minimally redundant in storing data. In other words, you should build a set of tables that minimize the repetition of data, by using foreign keys - credit will be in accordance with this.

Artist: An individual or a group/band, uniquely identified by their name. An artist might release albums, as well as songs that are not in albums (singles).
Song: A song has a title and is performed by an artist, either as a part of an album, or as a single that's not part of an album. Every song in an album has the release date of the album, but a single song has its own release date. A song title is unique to an artist (the same artist records a song exactly once), but the title may be shared by multiple artists (i.e. covers).
A song belongs to one or more genres. For example, a song could be in a single genre, such as R & B, or could be in multiple genres such as Pop and Rock. Genres are pre-defined, and every song must be in at least one genre. Also, songs in an album need not all be in the same genre.

Album: An album is a collection of songs released by an artist, on a certain date. For example, the album Achtung Baby was made by the artist (band) U2, released on November 19, 1991. An album name is not unique, but the combination of album name and artist name is unique.

User: A user is uniquely identified by their username. A user can optionally have one or more playlists, and optionally have ratings for songs, albums, or playlists. In other words, it's possible that a user has no playlists, and hasn't given any ratings.

Playlist: A user can make any number of playlists of songs. Note: A playlist may not include an entire album, only individual songs. Each song is either from some album, or a single that's not in any album.
Every playlist has a title, and a date+time when it was created. A playlist may be modified any number of times after creation by adding or removing songs, but the title and date+time will not change.

The title of a playlist is not unique since different users might create playlists with the same title. However, a user's playlists will have unique titles.

Rating: A user could rate an album, a song (even if it's in an album), or a playlist. A rating is limited to 1,2,3,4, or 5 (numeric), and is made on a specific date.
Your database structure should have the most appropriate data type and size for each column in each table.

For size of data, think of a realistic online music service and imagine how many songs/artists/albums/playlists/users/ratings it might have to support. The idea is to use the least amount of storage space for each column that will be able to store the entire range of foreseeable values.

Make sure you define and specify all primary keys, foreign keys, unique valued columns or unique valued combination of columns, and null/non-null properties for columns.

In the document you will submit, type in the create table statement for each of the tables you create in the database. If you don't have the full create statement for a table, you will not get credit for it.

Note: When you test your design in MySQL, you might use alter table statements after the initial create. However, for the submission, you are required to rewrite the whole sequence as a single create table statement per table.

Queries 
Every query must be written in a single SQL statement, meaning that if you were to write it in a MySQL client session on a terminal, there would be a single terminating semicolon. So, for example, you can have nested or multiple SQLs for a query, provided you can write it all up with a single terminating semicolon in a MySQL client session. No Python code!

For any of the queries:

If the result might require breaking ties, then unless otherwise specified in the query, let the MySQL engine deal with it (you need not do anything explicit)
If the result has fewer than the required number of entities, report all of them.
For all queries that ask for 'top n' or 'most', the result must appear from highest ranked to lowest ranked.
Type the SQL queries in the document you will submit, and make sure to write the query number against each query. (If you want to play it extra safe, copy the query statement from this list, then write your answer SQL query.)

Write queries for the following.

Which 3 genres are most represented in terms of number of songs in that genre?
The result must have two columns, named genre and number_of_songs.

Find names of artists who have songs that are in albums as well as outside of albums (singles).
The result must have one column, named artist_name

What were the top 10 most highly rated albums (highest average user rating) in the period 1990-1999?. Break ties using alphabetical order of album names. (Period refers to the rating date, NOT the date of release)
The result must have two columns, named album_name and average_user_rating.

Which were the top 3 most rated genres (this is the number of ratings of songs in genres, not the actual rating scores) in the years 1991-1995? (Years refers to rating date, NOT date of release)
The result must have two columns, named genre_name and number_of_song_ratings.

Which users have a playlist that has an average song rating of 4.0 or more? (This is the average of the average song rating for each song in the playlist.) A user may appear multiple times in the result if more than one of their playlists make the cut.
The result must 3 columns named username, playlist_title, average_song_rating

Who are the top 5 most engaged users in terms of number of ratings that they have given to songs or albums? (In other words, they have given the most number of ratings to songs or albums combined.)
The result must have 2 columns, named username and number_of_ratings.

Find the top 10 most prolific artists (most number of songs) in the years 1990-2010? Count each song in an album individually.
The result must have 2 columns, named artist_name and number_of_songs.

Find the top 10 songs that are in most number of playlists. Break ties in alphabetical order of song titles.
The result must have a 2 columns, named song_title and number_of_playlists.

Find the top 20 most rated singles (songs that are not part of an album).
Most rated meaning number of ratings, not actual rating scores. 
The result must have 3 columns, named song_title, artist_name, number_of_ratings.

Find all artists who discontinued making music after 1993.
The result should be a single column named artist_title
