# Movies-ETL
# Backgorund
#### Amazing Prime loves the dataset and wants to keep it updated on a daily basis. Britta needs your help to create an automated pipeline that takes in new data, performs the appropriate transformations, and loads the data into existing tables. You’ll need to refactor the code from this module to create one function that takes in the three files—Wikipedia data, Kaggle metadata, and the MovieLens rating data—and performs the ETL process by adding the data to a PostgreSQL database.
# Project Overview
#### Wikipedia has a ton of information about movies, including budgets and box office returns, cast and crew, production and distribution, and so much more. Luckily, one of Britta's coworkers created a script to go through a list of movies on Wikipedia from 1990 to 2018 and extract the data from the sidebar into a JSON. Unfortunately, her coworker can't find the script anymore and just has the JSON file. We'll need to load in the JSON file into a Pandas DataFrame.The major purpose is to use the ETL process to clean up this data, and make the data accessible for the hackathon by moving tthe data into a PostgresSQL database.
# Deliverable
1. Deliverable 1: Write an ETL Function to Read Three Data Files
2. Deliverable 2: Extract and Transform the Wikipedia Data
3. Deliverable 3: Extract and Transform the Kaggle data
4. Deliverable 4: Create the Movie Database
# Resources
* Data Source: `movie-metadata.csv` `ratings.csv`
* Data Tool: Jupyter Notebook 6.1.4
* Database: PostgreSQL
* Software: pgAdmin 4.29, Python 3.7.9

## Deliverable 1: Write an ETL Function to Read Three Data Files
> Using your knowledge of Python, Pandas, the ETL process, and code refactoring, extract and transform the Wikipedia data so you can merge it with the Kaggle metadata. While extracting the IMDb IDs using a regular expression string and dropping duplicates, use a try-except block to catch errors.

1. An ETL function is written to read in the three data files.
![1](https://user-images.githubusercontent.com/76136277/108571542-618f0080-72de-11eb-8957-c7bb2de24afa.PNG)

2. The function converts the Wikipedia JSON file to a Pandas DataFrame, and the DataFrame is displayed in the `ETL_function_test.ipynb` file.
![2](https://user-images.githubusercontent.com/76136277/108571903-2214e400-72df-11eb-8751-fa40a07194f0.PNG)

3. The function converts the Kaggle metadata file to a Pandas DataFrame, and the DataFrame is displayed in the `ETL_function_test.ipynb` file.
4. The function converts the MovieLens ratings data file to a Pandas DataFrame, and the DataFrame is displayed in the `ETL_function_test.ipynb` file. 

![3](https://user-images.githubusercontent.com/76136277/108571993-52f51900-72df-11eb-8e7d-fd628ad36b05.PNG)

## Deliverable 2: Extract and Transform the Wikipedia Data
> Using your knowledge of Python, Pandas, the ETL process, and code refactoring, extract and transform the Wikipedia data so you can merge it with the Kaggle metadata. While extracting the IMDb IDs using a regular expression string and dropping duplicates, use a try-except block to catch errors.

1. The TV shows are filtered out, and the wiki_movies_df DataFrame is created.
![4](https://user-images.githubusercontent.com/76136277/108572481-5b018880-72e0-11eb-9508-58453f2595e5.PNG)

2. A `try-except` block is used to catch errors while extracting the IMDb IDs with a regular expression and dropping duplicate IDs.
![5](https://user-images.githubusercontent.com/76136277/108572528-7cfb0b00-72e0-11eb-9f82-a6baea3cd730.PNG)

3. The extraction and transformation of the Wikipedia data in the ETL function does the following:
    * A list comprehension is used to keep columns with non-null values.
    ![7](https://user-images.githubusercontent.com/76136277/108572754-fc88da00-72e0-11eb-9063-1fb12dc6de91.PNG)

    * The non-null box office data is converted to string values using the lambda and join functions.
     ![8](https://user-images.githubusercontent.com/76136277/108572952-6f925080-72e1-11eb-8a7d-16e34160c865.PNG)

    * A regular expression is used to match the six elements of "form_one" of the box office data.
    ![9](https://user-images.githubusercontent.com/76136277/108572984-8769d480-72e1-11eb-8994-3a2e9d6e9c38.PNG)

    * A regular expression is used to match the three elements of "form_two" of the box office data.
      ![10](https://user-images.githubusercontent.com/76136277/108573024-a4060c80-72e1-11eb-9577-5026410a3268.PNG)

    * The following columns are cleaned in the Wikipedia DataFrame:
        * The box office column
        ![11](https://user-images.githubusercontent.com/76136277/108573074-c435cb80-72e1-11eb-89ec-f5e6f80c4c38.PNG)

        * The budget column
           ![12](https://user-images.githubusercontent.com/76136277/108573113-dd3e7c80-72e1-11eb-8639-8c9c045cda1c.PNG)

        * The release date column
           ![13](https://user-images.githubusercontent.com/76136277/108573389-68b80d80-72e2-11eb-8d1a-07c11ed5a62d.PNG)

        * The running time column
        ![14](https://user-images.githubusercontent.com/76136277/108573425-838a8200-72e2-11eb-8766-d6d0fb1a11c5.PNG)

# Deliverable 3: Extract and Transform the Kaggle Data 
>Using your knowledge of Python, Pandas, the ETL process, and code refactoring, extract and transform the Kaggle metadata and MovieLens rating data, then convert the transformed data into separate DataFrames. Then, you’ll merge the Kaggle metadata DataFrame with the Wikipedia movies DataFrame to create the `movies_df` DataFrame. Finally, you’ll merge the MovieLens rating data DataFrame with the `movies_df` DataFrame to create the `movies_with_ratings_df`.

1. The extraction and transformation of the Kaggle metadata using the ETL function does the following:
     * The Kaggle metadata is cleaned.
     ![1](https://user-images.githubusercontent.com/76136277/108573755-6d30f600-72e3-11eb-9398-32f7ec4c8deb.PNG)

     * The Wikipedia and Kaggle DataFrames are merged.
        ![2](https://user-images.githubusercontent.com/76136277/108573783-8043c600-72e3-11eb-9b76-67426d87b8eb.PNG)

     *  The following is performed on the merged Wikipedia and Kaggle DataFrames to create the `movies_df`:
         * Unnecessary columns are dropped.
          ![1](https://user-images.githubusercontent.com/76136277/108577338-b0449680-72ee-11eb-9daa-34d7f2ce1cf6.PNG)

         * A function is used to fill in the missing Kaggle data.
         ![3](https://user-images.githubusercontent.com/76136277/108573814-9a7da400-72e3-11eb-88c8-a2f3be384697.PNG)

         * The `movies_df` DataFrame is filtered to keep specific columns.
         ![4](https://user-images.githubusercontent.com/76136277/108573855-af5a3780-72e3-11eb-83ee-138ee44e86b5.PNG)

         * The `movies_df` DataFrame columns are renamed.
          ![5](https://user-images.githubusercontent.com/76136277/108573889-cd279c80-72e3-11eb-8a54-4b9a8f4e3a34.PNG)

2. The extraction and transformation of the MovieLens ratings data using the ETL function does the following:
     * The ratings counts are cleaned. 
     ![6](https://user-images.githubusercontent.com/76136277/108573948-f5170000-72e3-11eb-9695-fdff463c3c8b.PNG)

     * The movies_df DataFrame is merged with the cleaned ratings DataFrame to create the `movies_with_ratings_df` DataFrame. 
       ![7](https://user-images.githubusercontent.com/76136277/108573989-14159200-72e4-11eb-8613-b67eb160fb08.PNG)

     * The empty values in the `movies_with_ratings_df` DataFrame are filled with “0”. 
     ![8](https://user-images.githubusercontent.com/76136277/108574019-298abc00-72e4-11eb-88e3-5bc1c4a5c23b.PNG)

3. The movies_with_ratings_df and the movies_df DataFrames are displayed in the ETL_clean_kaggle_data.ipynb file.
![9](https://user-images.githubusercontent.com/76136277/108574062-4b843e80-72e4-11eb-8cec-7a1a6d173fea.PNG)

## Deliverable 4: Create the Movie Database
> Use your knowledge of Python, Pandas, the ETL process, code refactoring, and PostgreSQL to add the `movies_df` DataFrame and MovieLens rating CSV data to a SQL database.

1. The data from the `movies_df` DataFrame replaces the current data in the movies table in the SQL database, as determined by the `movies_query.png`.
![1](https://user-images.githubusercontent.com/76136277/108574536-aff3cd80-72e5-11eb-88a1-45cb937fd849.PNG)
![2](https://user-images.githubusercontent.com/76136277/108574629-eb8e9780-72e5-11eb-9dbb-828c087113ad.PNG)

2. The data from the MovieLens rating CSV file is added to the `ratings` table in the SQL database, as determined by the `ratings_query.png`.
![4](https://user-images.githubusercontent.com/76136277/108579992-82178480-72f7-11eb-9342-1e8c559c1080.PNG)

3. The elapsed time to add the data to the database is displayed in the `ETL_create_database.ipynb file`. 
![3](https://user-images.githubusercontent.com/76136277/108575323-d9155d80-72e7-11eb-8a51-9c610bec0b7d.PNG)
