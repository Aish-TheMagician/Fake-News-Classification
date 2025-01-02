# Fake News Classification Report

## Project Overview

This project focuses on detecting fake news using a dataset of news articles. The analysis involved cleaning and preprocessing the data, extracting linguistic and textual features, exploring patterns, and applying machine learning models to classify news articles as fake or real. A combination of statistical analysis, Natural Language Processing (NLP), and supervised machine learning techniques was used to achieve high accuracy in classification.

---

## Workflow

### 1. Data Loading and Preprocessing

#### Dataset Overview

The dataset consisted of multiple columns, including titles, text, subjects, labels (indicating whether the news is fake or real), and publication dates. The first step involved loading the dataset and performing an initial inspection to identify inconsistencies, missing values, and potential biases.

#### Steps:

- **Missing Values:** Rows with missing values in critical columns (`title`, `text`, `date`) were removed. Additionally, rows with missing `year` values and all data from 2015 were excluded due to inconsistencies in reporting.
- **Column Renaming:** Columns were renamed for better readability and consistency throughout the analysis.

#### Key Observations:

The distribution of fake and real news across different subjects was highly imbalanced:

```
label            0 (Fake)    1 (Real)
Subject
Government News     1014           0
Middle-east          530           0
News                6099           0
US_News              536           0
left-news           2953           0
politics            4346        7689
worldnews              0        6833
```

- Categories like `Government News`, `Middle-east`, and `US_News` contained only fake news, while `worldnews` consisted entirely of real news.
- The `politics` category was relatively balanced but leaned toward real news.

To address this imbalance, stratified sampling and resampling techniques were used to ensure model performance was not skewed.

---

### 2. Feature Engineering

Feature engineering involved deriving meaningful features from the available data to improve the model’s predictive performance.

#### Date Features:

- The `date` column was split into `day`, `month`, and `year`. Additionally, a `day_of_week` column was created to analyze temporal patterns.

##### Observations:

- **Weekly Patterns:** On weekends, the proportion of fake news to real news increased from 1:1 to 2:1.
- **Monthly Trends:** Fake news dominated in the first eight months of the year (2:1 ratio), whereas real news surged in the last four months (1:2 ratio).

#### Linguistic Features:

- **Title Features:**
  - Extracted character count, word count, sentiment analysis scores, and keyword density.
- **Text Features:**
  - Computed word count, sentence count, sentiment analysis scores, and readability scores (e.g., Flesch-Kincaid).

#### Topic Modeling:

Using Latent Dirichlet Allocation (LDA), five key topics were identified. The LDA model identified 5 topics based on the word co-occurrence patterns in the text data.  The topics were chosen algorithmically by the LDA model.&#x20;

LDA aims to find groups of words (topics) that frequently appear together across different documents. The algorithm iteratively assigns words to topics based on the probability of their occurrence within a topic and probability of a topic in a document. Each topic is represented by a probability distribution over the vocabulary, with the top words reflecting the most likely words for that topic.

Each topic was defined by its top keywords, helping classify articles based on thematic content.

---

### 3. Exploratory Data Analysis (EDA)

#### Sentiment Analysis:

- A scatter plot comparing text and title sentiment revealed a weak positive correlation (correlation coefficient: 0.21).
- Fake news articles were often emotionally charged, with extreme positive or negative sentiment scores, while real news maintained a neutral tone.

#### Temporal Analysis:

- **Quarterly Trends:** Real news articles surged by approximately four times their original volume in the last quarter of the year, coinciding with significant political and social events.

#### Readability Analysis:

- Real news articles were more readable than fake news, as measured by readability scores.
- A strong negative correlation was observed between readability scores and noun frequency, indicating that simpler language was associated with higher readability.

#### POS Tag Analysis:

- Real news articles used more nouns and verbs, aligning with their informative nature.
- Fake news relied heavily on adverbs and present-tense verbs, suggesting a tendency to sensationalize.

---

### 4. Model Training and Evaluation

Several machine learning models were trained and evaluated using different feature sets:

#### Logistic Regression (Using POS Tags):

- **Accuracy:** 96.66%
- **F1 Score:** 0.97

#### Random Forest (Using POS Tags):

- **Accuracy:** 97.47%
- **F1 Score:** 0.98

#### Support Vector Machine (Using POS Tags):

- **Accuracy:** 95.39%
- **F1 Score:** 0.96

#### Random Forest (Hyperparameter Tuned):

- **Best Parameters:** `{'max_depth': None, 'min_samples_split': 2, 'n_estimators': 200}`
- **Accuracy:** 98.51%

#### Logistic Regression (Using TF-IDF Features):

- **Accuracy:** 98.76%
- **AUC-ROC:** 0.9992

#### LSTM (Using TF-IDF Features):

- **Accuracy:** 97.62%
- **AUC-ROC:** 0.9950

---

### 5. Feature Importance

The Random Forest classifier highlighted the following key features:

- **Subject:** Played a critical role due to biases in certain categories.
- **Title and Text Lengths:** Indicative of the article’s style and complexity.
- **Topic 1 (LDA):** Captured patterns commonly found in fake news articles.

---

### 6. Results and Findings

- **Model Performance:** All models performed exceptionally well, with the TF-IDF-based logistic regression model achieving the best accuracy and AUC-ROC scores.
- **Insights:**
  - Real news articles are linguistically distinct from fake news.
  - Temporal patterns revealed significant differences in the volume of fake and real news over time.
  - Linguistic features, such as sentiment and readability, were strong indicators of authenticity.

---

## Conclusion

This project successfully demonstrated a robust pipeline for fake news detection using advanced feature engineering, NLP techniques, and machine learning models. The findings emphasize the importance of linguistic features and temporal patterns in distinguishing fake news from real news. The classification models developed here provide a strong foundation for real-world applications in combating fake news.

---

## Submission Files

1. **Code:** Provided as a Jupyter Notebook.
2. **Report:** This document.
3. **Results:** Output saved as `result.json` and visualizations (confusion matrices, AUC-ROC curves, etc.) included.

---

## Future Work

- Extend analysis to include social media data, which often contains fake news in different formats.
- Implement ensemble models to further improve classification performance.
- Explore bias mitigation techniques to handle imbalanced datasets more effectively.


