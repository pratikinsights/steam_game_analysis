# Steam Games — Market & Player Engagement Analysis

An exploratory data analysis project focused on understanding the Steam gaming marketplace through game pricing, genres, player engagement, reviews, recommendations, release trends, and game characteristics.

The project uses Python for data cleaning, validation, exploratory analysis, statistical analysis, and visualization, with Power BI used for interactive dashboard development.

---

## Project Overview

The Steam marketplace contains a large and diverse collection of games with information about pricing, discounts, player engagement, reviews, developers, publishers, genres, categories, and release dates.

This project analyzes Steam game data to identify patterns in:

- Game pricing and discounts
- Free vs paid games
- Game genres and categories
- Player engagement
- Reviews and recommendations
- Release trends
- Age restrictions
- Developer and publisher presence
- Relationships between reviews and player engagement

The goal is to transform raw gaming marketplace data into meaningful analytical and business insights.

---

## Objectives

The main objectives of this project are to:

- Perform data validation and quality assessment.
- Clean and prepare Steam game data for analysis.
- Analyze the distribution of free and paid games.
- Understand game pricing patterns.
- Identify dominant game genres.
- Analyze player engagement using Peak CCU and playtime.
- Analyze positive and negative review patterns.
- Calculate positive review rates.
- Identify highly reviewed and highly engaged games.
- Analyze relationships between reviews and player engagement.
- Prepare insights for Power BI dashboard development.

---

## Dataset Overview

The dataset contains Steam game information including:

- AppID
- Name
- Release date
- Estimated owners
- Peak CCU
- Required age
- Price
- Discount
- DLC count
- Metacritic score
- User score
- Positive reviews
- Negative reviews
- Achievements
- Recommendations
- Average playtime
- Median playtime
- Developers
- Publishers
- Categories
- Genres
- Tags

### Dataset Size

- 114,172 games
- 38 columns
- 70,736 unique developers
- 62,611 unique publishers
- 13,277 unique category combinations
- 2,888 unique genre combinations

The dataset covers Steam games through January 2026.

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Power BI
- Jupyter Notebook

---

## Data Cleaning & Quality Analysis

The dataset was first inspected for structure, data types, missing values, duplicate records, primary-key validity, invalid values, and outliers.

### Data Quality Checks

| Check | Result |
|---|---|
| Duplicate rows | None detected |
| AppID uniqueness | Valid |
| Missing AppID | None |
| Negative prices | None detected |
| Invalid discounts | None detected |
| Outliers | Present and investigated |
| Release date | Converted to datetime |
| Zero-review games | Present and treated separately |

The `AppID` column was validated as a unique identifier for each game.

Missing values were concentrated mainly in metadata fields such as Reviews, Website, Support URL, Notes, and Metacritic URL. Core analytical variables such as Price, Peak CCU, Positive Reviews, Negative Reviews, Recommendations, User Score, and Playtime were complete.

Because several numerical variables were highly skewed, particularly Peak CCU, reviews, recommendations, and playtime, extreme values were investigated rather than automatically removed.

---

## Exploratory Data Analysis

### 1. Steam Marketplace Overview

The dataset contains:

- 114,172 games
- 70,736 unique developers
- 62,611 unique publishers
- 13,277 unique category combinations
- 2,888 unique genre combinations

The average game price is approximately **$5.11**, while the median price is **$2.74**.

The large difference between the mean and median indicates that the Steam marketplace contains a large number of low-priced games along with a smaller number of expensive games.

---

### 2. Free vs Paid Games

The dataset contains:

- 17,891 free games
- 96,281 paid games

Free games represent approximately **15.67%** of the dataset.

The most common price points are:

| Price | Number of Games |
|---:|---:|
| $0.00 | 17,891 |
| $0.99 | 8,911 |
| $4.99 | 8,092 |
| $1.99 | 6,629 |
| $2.99 | 6,342 |

The maximum recorded game price is **$999.98**.

---

### 3. Genre Analysis

The dataset contains 2,888 unique genre combinations.

The most common genre combination is:

**Casual, Indie — 6,697 games**

Other highly represented combinations include:

- Action, Indie — 5,671
- Action, Adventure, Indie — 5,152
- Adventure, Indie — 4,305
- Adventure, Casual, Indie — 3,608

This indicates a strong presence of Indie and Casual-oriented games within the Steam catalog.

---

### 4. Player Engagement

Player engagement was analyzed using:

- Peak CCU
- Average playtime
- Median playtime
- Total reviews
- Recommendations

Across the full dataset:

- Average Peak CCU: approximately **57.64**
- Maximum Peak CCU: **1,013,936**
- Average lifetime playtime: approximately **222.47**
- Maximum lifetime playtime: **3,429,544**

Because the distribution is highly skewed, median values are much lower than the averages.

For games with both reviews and Peak CCU greater than zero, the analysis produced **18,486 games** for engagement analysis.

---

### 5. Reviews & Player Engagement

A total of:

- 124,167,562 positive reviews
- 19,943,033 negative reviews
- 109,303,707 recommendations

were recorded across the dataset.

The analysis created:

`total_reviews = Positive + Negative`

and:

`positive_review_rate = Positive / (Positive + Negative) × 100`

Games with zero positive and zero negative reviews were excluded from review-rate calculations because they do not provide enough information for a meaningful review percentage.

Among games with available review data, the average positive review rate was approximately **75.82%**.

---

### 6. Most Positively Reviewed Games

The games with the highest number of positive reviews included:

| Game | Positive Reviews |
|---|---:|
| Counter-Strike 2 | 7,642,084 |
| Dota 2 | 2,037,143 |
| Grand Theft Auto V Legacy | 1,739,980 |
| PUBG: BATTLEGROUNDS | 1,520,457 |
| Terraria | 1,373,979 |
| Garry's Mod | 1,122,546 |
| Black Myth: Wukong | 1,111,720 |
| Rust | 1,071,135 |
| Team Fortress 2 | 1,044,264 |
| ELDEN RING | 981,540 |

These games demonstrate the concentration of review activity around a relatively small group of highly popular titles.

---

### 7. Reviews vs Player Engagement

The relationship between total reviews and Peak CCU was analyzed using games with both values greater than zero.

The analysis produced a correlation coefficient of approximately:

**0.879**

This indicates a strong positive relationship between review volume and peak concurrent players within the filtered dataset.

In general, games with greater review activity also tend to show higher player engagement.

---

### 8. Age Restrictions

The dataset contains:

- 112,949 games with no age restriction
- 1,223 games with an age restriction

The majority of games in the dataset therefore do not have a specified age requirement.

Among age-restricted games, the most common required ages include 17, 13, and 18.

---

## Key Insights

### Marketplace

- Steam contains more than 114,000 games in the analyzed dataset.
- The marketplace is dominated by a large number of low-priced games.
- The median game price of $2.74 is considerably lower than the average price of $5.11.
- Free games account for approximately 15.67% of the catalog.

### Genre

- Casual and Indie combinations are highly represented.
- `Casual, Indie` is the most common recorded genre combination.
- The Steam marketplace contains a very large variety of genre combinations.

### Player Engagement

- Most games have relatively low Peak CCU.
- A small number of highly successful games generate extremely high player activity.
- Peak CCU is heavily right-skewed, with a maximum of more than one million concurrent players.

### Reviews

- Review activity is highly concentrated among popular games.
- Counter-Strike 2 has the highest number of positive reviews in the analyzed dataset.
- Games with both reviews and active players show a strong positive relationship between review volume and Peak CCU.

### Data Quality

- No duplicate rows were detected.
- AppID was validated as a unique identifier.
- No negative prices or invalid discount values were detected.
- Missing values were primarily found in optional metadata fields.
- Outliers were retained because they can represent genuinely successful games.

---

## Visualizations

The project uses several visualization techniques to explore the Steam marketplace, including:

- Bar charts
- Histograms
- Scatter plots
- Distribution plots
- Correlation analysis
- Count plots
- Comparative visualizations

The analysis focuses particularly on pricing, genres, reviews, player engagement, and marketplace distributions.

---

## Power BI Dashboard

The analysis was extended into an interactive Power BI dashboard designed to provide a visual overview of:

- Steam marketplace composition
- Game pricing
- Genre distribution
- Player engagement
- Review performance
- Game popularity
- Marketplace trends

The dashboard provides an interactive way to explore the patterns identified during the Python-based exploratory analysis.

---

## Project Workflow

```text
Raw Steam Dataset
        ↓
Data Loading
        ↓
Data Inspection
        ↓
Data Quality Checks
        ↓
Missing Value Analysis
        ↓
Duplicate & Primary Key Validation
        ↓
Range & Outlier Analysis
        ↓
Data Transformation
        ↓
Exploratory Data Analysis
        ↓
Statistical & Correlation Analysis
        ↓
Visualization
        ↓
Power BI Dashboard
        ↓
Business & Market Insights
