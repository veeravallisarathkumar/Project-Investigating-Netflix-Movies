# README

## Overview

This Jupyter Notebook analyzes Netflix movie data to explore the hypothesis that the average duration of movies has been declining over time. The analysis focuses on movies available on Netflix and examines the relationship between movie release year and duration.

## Dataset

The dataset used in this analysis is `netflix_data.csv`, which contains information about various shows available on Netflix. The dataset includes the following columns:

| Column        | Description                     |
|---------------|---------------------------------|
| `show_id`     | The ID of the show              |
| `type`        | Type of show                    |
| `title`       | Title of the show               |
| `director`    | Director of the show            |
| `cast`        | Cast of the show                |
| `country`     | Country of origin               |
| `date_added`  | Date added to Netflix           |
| `release_year`| Year of Netflix release         |
| `duration`    | Duration of the show in minutes |
| `description` | Description of the show         |
| `genre`       | Show genre                      |

## Analysis Steps

1. **Importing Libraries**:
    - Import the necessary libraries: pandas for data manipulation and matplotlib for data visualization.
    
    ```python
    import pandas as pd
    import matplotlib.pyplot as plt
    ```

2. **Loading the Dataset**:
    - Load the `netflix_data.csv` file into a pandas DataFrame.
    
    ```python
    netflix_df = pd.read_csv('netflix_data.csv')
    ```

3. **Filtering for Movies**:
    - Create a subset of the data containing only movies.
    
    ```python
    netflix_subset = netflix_df[netflix_df['type'] == 'Movie']
    netflix_movies = netflix_subset[["title", "country", "genre", "release_year", "duration"]]
    ```

4. **Identifying Short Movies**:
    - Identify movies with a duration of less than 60 minutes.
    
    ```python
    short_movies = netflix_movies[netflix_movies.duration < 60]
    ```

5. **Color Coding by Genre**:
    - Assign colors to different genres for visualization.
    
    ```python
    colors = []

    for labels, row in netflix_movies.iterrows():
        if row['genre'] == "children":
            colors.append("red")
        elif row['genre'] == "Documentaries":
            colors.append("blue")
        elif row['genre'] == "Stand-Up":
            colors.append("green")
        else:
            colors.append("black")
    
    colors[:10]
    ```

6. **Plotting the Data**:
    - Create a scatter plot to visualize the relationship between movie release year and duration.
    
    ```python
    fig = plt.figure(figsize=(12, 8))
    plt.scatter(netflix_movies.release_year, netflix_movies.duration, c=colors)
    plt.title("Movie Duration by Year of Release")
    plt.xlabel("Release year")
    plt.ylabel("Duration (min)")
    plt.show()
    ```

7. **Conclusion**:
    - Determine if movie durations are declining over time.
    
    ```python
    answer = "no"
    ```

## Usage Instructions

1. **Open the Notebook**:
    - Use Jupyter Notebook or JupyterLab to open the `.ipynb` file.

2. **Run the Cells**:
    - Execute the cells in the notebook sequentially to load the data, filter for movies, assign colors, and create visualizations.

3. **Review the Results**:
    - Analyze the scatter plot to observe any trends in movie durations over time.

## Requirements

- Python 3
- Jupyter Notebook or JupyterLab
- pandas library
- matplotlib library

