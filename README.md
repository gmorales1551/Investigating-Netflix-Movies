# Investigating-Netflix-Movies

An exploratory data analysis in Python using Pandas to investigate 1990s movie duration trends and short action movie frequencies on Netflix.

## Project Overview

A DataCamp Python project performing exploratory data analysis on Netflix streaming data (`netflix_data.csv`) using Pandas to analyze movie characteristics and duration patterns from the 1990s.

## Dataset & Schema

The dataset `netflix_data.csv` contains records on Netflix content and metadata:

- `show_id`: The ID of the show
- `type`: Type of show (Movie, TV Show)
- `title`: Title of the show
- `director`: Director of the show
- `cast`: Cast of the show
- `country`: Country of origin
- `date_added`: Date added to Netflix
- `release_year`: Year of release
- `duration`: Duration of the show in minutes
- `description`: Description of the show
- `genre`: Show genre

## Project Questions & Python Analysis

### 1. Most Frequent Movie Duration in the 1990s
Analyzed movies released between 1990 and 1999 to calculate the most frequent movie duration (mode).

```python
import pandas as pd

netflix_df = pd.read_csv("netflix_data.csv")

# Filter for 1990s movies and calculate mode duration
duration = netflix_df[
    (netflix_df["release_year"] >= 1990)
    & (netflix_df["release_year"] <= 1999)
    & (netflix_df["type"] == "Movie")
]["duration"].mode()[0]
```

### 2. Short 1990s Action Movie Count
Filtered for 1990s Action movies with a runtime under 90 minutes to determine the total count.

```python
# Count short action movies (<90 mins) from the 1990s
short_movie_count = netflix_df[
    (netflix_df["genre"] == "Action")
    & (netflix_df["duration"] < 90)
    & (netflix_df["release_year"] >= 1990)
    & (netflix_df["release_year"] <= 1999)
]["genre"].count()
```
