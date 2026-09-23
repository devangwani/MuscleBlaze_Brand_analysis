# MuscleBlaze Brand Analysis 📊

A data analytics project focused on understanding **MuscleBlaze's social media performance and marketplace presence** using data from **YouTube, Instagram, and Amazon**.

The project combines **data cleaning, preprocessing, exploratory data analysis (EDA), text analysis, sentiment analysis, outlier analysis, visualization, and database storage** to extract business-oriented insights from brand data.

---

## 📌 Project Overview

The objective of this project is to analyze how MuscleBlaze performs across different digital channels and identify patterns in:

- Social media engagement
- Content performance
- Audience interaction
- Content sentiment and language
- Product pricing and ratings
- Product review volume
- High-performing/outlier content and products

The analysis is performed as a **single-brand deep dive**, rather than a comparison between multiple brands.

---

## 📂 Datasets

The final analysis uses three cleaned datasets:

| Platform | Records | Unit of Analysis | Main Metrics |
|---|---:|---|---|
| YouTube | 400 | Video | Views, Likes, Comments, Subscribers |
| Instagram | 300 | Post / Reel / Carousel | Likes, Comments, Views, Plays |
| Amazon | 100 | Product Listing | Price, Rating, Reviews |

### YouTube
Key fields include:
- `viewCount`
- `likes`
- `commentsCount`
- `numberOfSubscribers`
- `title`
- `hashtags`
- `location`

### Instagram
Key fields include:
- `likesCount`
- `commentsCount`
- `videoViewCount`
- `videoPlayCount`
- `caption_clean`
- `hashtags`
- `mentions`
- Post type

### Amazon
Key fields include:
- `price/value`
- `stars`
- `reviewsCount`
- Product title
- Product description

---

## 🛠️ Technologies & Tools

- **Python**
- **Pandas** – data manipulation and analysis
- **NumPy** – numerical operations
- **Matplotlib** – visualization
- **Seaborn** – statistical visualization
- **NLTK** – text preprocessing
- **TextBlob** – sentiment analysis
- **WordCloud** – text-frequency visualization
- **SQLite** – relational data storage
- **MongoDB / PyMongo** – NoSQL data storage
- **Jupyter Notebook / Google Colab**

---

## 🔄 Project Workflow

```text
Data Collection / Scraping
          ↓
Raw CSV Datasets
          ↓
Data Inspection
          ↓
Data Cleaning & Preprocessing
          ↓
Duplicate & Missing-Value Handling
          ↓
Text Cleaning
          ↓
Filtering & Data Storage
      ↙          ↘
   SQLite       MongoDB
      \          /
       ↓        ↓
      Cleaned Datasets
             ↓
      Exploratory Data Analysis
             ↓
    Visualization & Text Analysis
             ↓
     Sentiment & Outlier Analysis
             ↓
       Business Insights
```

---

## 🧹 Data Cleaning & Preprocessing

The preprocessing pipeline includes:

- Removing unnecessary/irrelevant columns
- Handling missing and invalid values
- Removing duplicate records
- Cleaning text fields
- Removing HTML tags and URLs
- Removing punctuation and emojis
- Converting text to lowercase
- Removing stopwords
- Standardizing repeated characters
- Optional stemming and lemmatization
- Filtering datasets for analysis
- Storing processed data in SQLite and MongoDB

---

## 📊 Exploratory Data Analysis

### 1. YouTube Analysis

The YouTube analysis examines:

- Video views and likes
- Comment activity
- Engagement patterns
- Posting day and hour
- Video title patterns
- Hashtag usage
- Sentiment of video titles
- Word frequency
- Outlier videos

Key observations from the analysis:

- YouTube views and likes are strongly right-skewed, with a small number of highly viewed videos contributing a large share of reach.
- The median view count is approximately **15.3M**, compared with a mean of approximately **25.6M** in the analyzed dataset.
- Only **28 of 400 videos** contained at least one hashtag.
- Video performance varies across posting days and hours.
- Title sentiment was analyzed using TextBlob and classified as Positive, Neutral, or Negative.

---

### 2. Instagram Analysis

The Instagram analysis examines:

- Reels vs. carousel performance
- Likes and comments
- Video views and plays
- Caption length
- Caption sentiment
- Hashtag and mention usage
- Engagement outliers
- Frequently used words

Key observations:

- Reels/video posts showed substantially higher average engagement than carousel posts in the analyzed dataset.
- Captions were generally short and tended toward positive or neutral sentiment.
- Hashtag and mention usage was relatively sparse.
- A small number of posts generated a disproportionate amount of engagement.
- Outlier posts were retained because they represent potentially important examples of high-performing content.

---

### 3. Amazon Marketplace Analysis

The Amazon analysis examines:

- Product prices
- Star ratings
- Review counts
- Product categories
- Product-title keywords
- Price and rating relationships
- Review-count distribution
- Product outliers

Key observations:

- The analyzed catalog is concentrated around whey/protein and other supplement products, with additional apparel and fitness accessories.
- Review counts are highly right-skewed, with a small number of established products accounting for a large share of reviews.
- Price does not show a strong linear relationship with star rating in the analyzed sample.
- High-price products and high-review products were treated as meaningful business signals rather than automatically removed as outliers.

---

## 📈 Text & Sentiment Analysis

Text analytics were applied to social-media titles and captions.

### Techniques used

- Text cleaning
- Stopword removal
- Word frequency analysis
- Word clouds
- Sentiment polarity
- Sentiment classification

Example sentiment classification:

```text
Polarity > 0.05    → Positive
Polarity < -0.05   → Negative
Otherwise          → Neutral
```

---

## 🚨 Outlier Analysis

The project uses the **Interquartile Range (IQR)** method to identify unusual observations.

Outliers were **flagged rather than automatically deleted** because highly successful content and products are valuable business signals.

Examples:

- Viral YouTube videos
- High-engagement Instagram Reels
- High-priced premium products
- Products with exceptionally high review counts

This approach prevents the analysis from removing the very observations that may be most useful for marketing and business decisions.

---

## 💡 Business Insights

The combined analysis provides several useful observations:

1. **Video content is an important engagement format** across the analyzed YouTube and Instagram datasets.
2. **A small number of high-performing posts/videos drive a disproportionate share of engagement.**
3. **Hashtag usage is relatively low** in the analyzed social-media datasets.
4. **Motivational and positive/neutral messaging** is common in the analyzed social content.
5. **A small group of hero products generates substantial review activity** on Amazon.
6. **Price alone does not explain product ratings** in the analyzed Amazon sample.
7. Outlier analysis can be used as a **business discovery tool**, rather than simply treating outliers as errors.

---

## 🗄️ Database Storage

The preprocessing experiment demonstrates storing cleaned datasets using both:

### SQLite
A local relational database:

```text
social_media.db
```

### MongoDB
A local NoSQL database:

```text
Database: social_media_analytics
```

MongoDB is configured for local development using:

```text
localhost:27017
```

---

## 📁 Repository Structure

```text
MuscleBlaze_Brand_analysis/
│
├── 255_DEVANG__WANI_EXP_4_SMA_26.ipynb
│   └── Complete EDA and visualization analysis
│
├── Experiment_3_Data_Cleaning_Filtering_Storage (1) (1).ipynb
│   └── Cleaning, preprocessing, filtering and database storage
│
├── Data_Scraping_information.docx
│   └── Data collection / scraping information
│
├── youtube_data.xls
├── youtube_cleaned.csv
│
├── instagram_dataset.xls
├── instagram_cleaned.csv
│
├── amazon_dataset_full.xls
├── amazon_cleaned.csv
│
└── README.md
```

---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/devangwani/MuscleBlaze_Brand_analysis.git
cd MuscleBlaze_Brand_analysis
```

### 2. Install Python dependencies

```bash
pip install pandas numpy matplotlib seaborn wordcloud textblob nltk pymongo
```

For the preprocessing notebook:

```bash
pip install nltk pymongo
```

### 3. Open the notebooks

Use Jupyter Notebook, JupyterLab, or Google Colab.

```bash
jupyter notebook
```

### 4. Run the preprocessing notebook

Run:

```text
Experiment_3_Data_Cleaning_Filtering_Storage (1) (1).ipynb
```

This notebook performs cleaning, preprocessing, filtering and storage.

### 5. Run the EDA notebook

Run:

```text
255_DEVANG__WANI_EXP_4_SMA_26.ipynb
```

Make sure the cleaned CSV files are available in the same working directory.

---

## ⚠️ Limitations

- The analysis focuses on a single brand, so the findings should not be treated as general conclusions about the entire fitness industry.
- Social-media engagement can change over time.
- Amazon product categories are partly derived using title-based keywords and should be treated as approximate.
- Engagement-rate comparisons involving Instagram video metrics are limited to posts where video metrics are available.
- Missing values may reflect the nature of the source data rather than random missingness.

---

## 🎯 Skills Demonstrated

This project demonstrates practical experience in:

- Data Collection
- Data Cleaning
- Data Preprocessing
- Exploratory Data Analysis
- Statistical Analysis
- Data Visualization
- Text Analytics
- Sentiment Analysis
- Outlier Detection
- Social Media Analytics
- Marketplace Analytics
- SQLite Database Management
- MongoDB / NoSQL
- Python Data Analysis
- Business Insight Generation

---

## 👨‍💻 Author

**Devang Kishor Wani**

GitHub: [@devangwani](https://github.com/devangwani)

Repository: [MuscleBlaze Brand Analysis](https://github.com/devangwani/MuscleBlaze_Brand_analysis)
