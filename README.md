```markdown
# 🎬 Netflix Exploratory Data Analysis Case Study

> An in-depth exploratory data analysis of Netflix's global content catalog to uncover production patterns, regional trends, and strategic opportunities.


## 🏅 Badges
[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Jupyter/Colab](https://img.shields.io/badge/Jupyter-Colab-orange.svg)](https://colab.research.google.com/)
[![pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-3776AB.svg)](https://seaborn.pydata.org/)

## 📖 Project Overview
Netflix is one of the most popular global streaming platforms, boasting over 222 million subscribers and a vast library of movies and TV shows as of mid-2021. This case study explores Netflix's tabular dataset containing listings of available titles alongside attributes like cast, directors, ratings, release year, and duration. By examining catalog composition, content distribution, and temporal addition trends, this analysis provides actionable data-backed guidance on content strategy and regional growth.

## 🎯 Business Problem / Objectives
* Determine the ideal content mix between movies and TV shows to optimize platform engagement.
* Identify high-performing geographic markets to guide future content acquisition and production.
* Uncover optimal release timings, seasonal patterns, and target audience ratings for maximum viewership.
* Analyze runtime and season distributions across genres and countries.

## 📊 Dataset
* **Source:**  (Hosted via [Netflix Dataset on Cloudfront](https://d2beiqkhq929f0.cloudfront.net/public_assets/assets/000/000/940/original/netflix.csv))
* **Size:** 8,807 rows and 12 columns (cleaned to 8,794 rows)

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `show_id` | object | Unique identifier for each movie or TV show |
| `type` | object | Category of content (`Movie` or `TV Show`) |
| `title` | object | Title of the movie or TV show |
| `director` | object | Director(s) responsible for the title |
| `cast` | object | Key actors and cast members featured |
| `country` | object | Country or countries where production took place |
| `date_added` | object | Date the title was added to Netflix |
| `release_year` | int64 | Original release year of the content |
| `rating` | object | Content age-appropriateness rating |
| `duration` | object | Runtime for movies or season count for TV shows |
| `listed_in` (genre) | object | Genres and thematic classifications |
| `description` | object | Summary synopsis of the content |

## 🧰 Tools & Libraries
* **Python**: Core programming language for data manipulation and analysis.
* **pandas & NumPy**: Data cleaning, feature extraction, DataFrame un-nesting, and statistical summaries.
* **Matplotlib & Seaborn**: Univariate, bivariate, and multivariate data visualization (histograms, boxplots, countplots).

## ⚙️ Methodology
1. **Data Loading & Inspection**: Retrieved dataset via URL download, evaluated initial shape ($8,807 \times 12$), and examined data types.
2. **Missing Value Treatment**: Addressed missing values by filling categorical gaps (`director`, `cast`, `country`, `rating`) with explicit unknown tags and dropping negligible rows ($<0.2\%$) missing `date_added` or `duration`.
3. **Feature Engineering**: Extracted numerical durations, converted addition dates to `datetime`, derived `added_year`, `Month Name`, `week`, and calculated approximate `days_to_netflix` relative to release years.
4. **Data Un-nesting**: Created custom unnesting functions to explode comma-separated `country`, `genre`, `cast`, and `director` fields for granular, independent analysis of movies and TV shows.
5. **Exploratory Data Analysis**: Conducted non-graphical value counts alongside univariate, bivariate, and multivariate graphical visualizations (boxplots, countplots, histplots).

## 💡 Key Insights & Findings
* **Catalog Split**: Movies heavily outnumber TV shows, accounting for $69.68\%$ ($6,128$ titles) compared to TV shows at $30.32\%$ ($2,666$ titles).
* **Geographic Dominance**: The United States leads production volumes significantly ($2,748$ movies and $932$ TV shows), followed closely by India for movies ($962$ entries) and the UK, Japan, and South Korea for TV shows.
* **Audience Targeting**: Mature audiences are heavily prioritized, with `TV-MA` representing nearly $33\%$ of movies and $43\%$ of TV shows across the catalog.
* **Recent Library Focus**: Over $75\%$ of Netflix's catalog consists of modern content released after 2013, with platform additions peaking heavily between 2018 and 2020.
* **Duration Benchmarks**: Movie runtimes form a tight unimodal distribution clustered around a 90 to 105-minute baseline, while over two-thirds of TV shows ($1,793$ titles) consist of exactly 1 Season.
* **Release Timing**: Fridays experience a massive surge in content additions, strategically aligned to capture weekend binge-viewing traffic.
* **Regional Variances**: Indian movies exhibit a higher median duration ($115\text{--}120$ minutes) compared to Western titles ($90\text{--}100$ minutes), and East Asian TV shows are heavily concentrated in single-season formats.

## 🖼️ Visualizations
* ![Top 10 Countries by Movie Count](images/top-countries-movies.png)  
  *Compares production volume across the top 10 countries for feature films, highlighting US and Indian dominance.*
* ![Top 10 Ratings for Movies and TV Shows](images/ratings-distribution.png)  
  *Illustrates audience rating distributions, demonstrating the high prevalence of TV-MA and TV-14 content.*
* ![Movie Duration Distribution Across Top Genres](images/movie-duration-box.png)  
  *Shows runtime consistency across major movie genres, clustering tightly around 90-110 minutes.*
* ![Content Release Year by Country Boxplot](images/release-year-country.png)  
  *Highlights that TV shows feature much newer release dates (mostly 2017–2021) compared to historical movie archives.*
* ![Monthly Trend of Content Additions](images/monthly-trends.png)  
  *Tracks seasonal addition cadences highlighting mid-year and year-end ingestion spikes.*

## 📋 Recommendations
* Focus platform expansion on high-growth regional markets such as South Korea, Japan, and India to diversify away from domestic US saturation.
* Optimize release scheduling by timing major movie drops on Fridays and staggering TV show season debuts across mid-year and holiday windows (e.g., W27–W31 and W52–W02).
* Expand family and comedy content offerings, as they show steady multi-format engagement alongside mature adult programming.
* Boost international ROI by prioritizing multi-language dubbing and subtitling for breakout regional hits like K-Dramas, Anime, and Bollywood productions.

## ⚠️ Limitations & Future Work
* **Data Horizon**: The dataset concludes in mid-2021, meaning 2021 annual totals reflect partial-year data.
* **Missing Metadata**: Approximately $30\%$ of records lacked director data, requiring placeholder imputation (`Unknown_Director`).
* **Future Steps**: Integrate subscriber viewership ratings and retention metrics to evaluate actual content ROI against catalog volume.

## 💻 How to Run
1. Open the Jupyter Notebook in Google Colab using the repository link.
2. Ensure the dataset CSV is loaded via the automated download command in the notebook:
   ```python
   !gdown https://d2beiqkhq929f0.cloudfront.net/public_assets/assets/000/000/940/original/netflix.csv
