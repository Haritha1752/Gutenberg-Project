# Gutenberg Project Analysis

This project investigates the factors influencing the popularity of English-language fiction books from Project Gutenberg. By analyzing various features like narrative information revelation, sentiment dynamics, and genre, we aim to understand what drives reader engagement, measured by download counts.

## Table of Contents
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Methodology](#methodology)
  - [Data Processing](#data-processing)
  - [Exploratory Analysis](#exploratory-analysis)
  - [Predictive Modeling](#predictive-modeling)
- [Key Findings](#key-findings)
- [Requirements](#requirements)
- [Usage](#usage)
- [File Structure](#file-structure)

## Project Overview
The purpose of this project is to analyze and predict the popularity of books based on key textual features. We focus on:
- **Narrative Information Revelation** (using Kullback-Leibler Divergence)
- **Sentiment Dynamics** (average sentiment and volatility)
- **Genre-Specific Characteristics** 

## Data Sources
1. **Project Gutenberg**: A collection of book metadata, including download counts and genres.
2. **KLD Scores**: Book-level narrative information revelation scores.
3. **Extra Controls**: Contains sentiment and word count data, and genre indicators for each book.

## Methodology

### Data Processing
- **Feature Engineering**: Calculated book-level metrics from KLD scores (average, variance, range, and slope) and created a clean dataset including sentiment scores, genres, and log-transformed download counts.
- **Imputation**: Missing values were imputed using the mean for reliable model training.

### Exploratory Analysis
1. **Book-Level KLD Metrics**: We calculated average KLD, variance, and slope for each book, showing different patterns in information revelation.
2. **Regression of KLD Measures Against Popularity**: We performed linear regression to understand how each KLD feature impacts book downloads.
3. **Genre-Specific Analysis with LASSO**: Using LASSO regression, we identified genre-specific predictors for download counts, focusing on the most influential features in each genre.
4. **Sentiment Analysis**: We examined average sentiment and sentiment volatility across genres to see if emotional dynamics play a role in engagement.

### Predictive Modeling
We used **Random Forest** and **Linear Regression** models to predict the popularity of books based on:
- **Sentiment Metrics**: `sentiment_avg` and `sentiment_vol`
- **KLD Metrics**: `kld_avg`, `kld_var`, `kld_slope`, etc.
- **Genres**: Represented by one-hot encoded genre columns.

**Model Performance Summary**:
| Model              | Mean Squared Error (MSE) | R² Score |
|--------------------|--------------------------|----------|
| Linear Regression  | 1.068                    | 0.151          |
| Random Forest      | 1.116                    | (0.112         |

The **Random Forest model** provided the highest accuracy, indicating complex relationships between features.

## Key Findings
1. **Narrative Dynamics**: Higher variance in KLD scores was linked to higher downloads, suggesting that readers favor books with dynamic narratives.
2. **Genre-Specific Insights**: Certain genres, like thriller and science fiction, showed stronger relationships between sentiment volatility and popularity.
3. **Top Predictors of Popularity**: Sentiment volatility, certain KLD features (like `kld_var`), and genres (especially thrillers) were among the top predictors of download counts.

## Requirements
The following libraries are required to run the notebook:
- `pandas`
- `numpy`
- `scikit-learn`
- `matplotlib`

You can install the required packages with:
```bash
pip install -r requirements.txt
