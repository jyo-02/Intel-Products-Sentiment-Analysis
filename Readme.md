<div align="center">
    <h1 align="center">Intel Sentiment Analysis</h1>
</div>

The goal of this project is to perform sentiment analysis on customer reviews to classify sentiments. This analysis will assist companies in improving product features and increasing sales performance by leveraging customer satisfaction and feedback.

# Project Workflow

1. ## Web Scraper
    The `1-web-scrapers` folder contains four web scrapers designed for different platforms:
    
    1. ### Amazon
        * BeautifulSoup and Splash in Docker are used to scrape reviews from all Amazon regions worldwide, including India, the US, the UK, Japan, and more.
    
    2. ### BestBuy & Flipkart
        * BeautifulSoup is employed to scrape reviews from both BestBuy and Flipkart.
    
    3. ### Technical Reviews
        * Selenium is used to scrape reviews from technical review sites such as Tom's Hardware and PCMag.

    * Save all the website links and processor names in their respective URL files. Run each program as needed to collect the data.
    
    * If there are multiple processor from a single wesite then merge them all by `multimerger.ipynb` which is in `1-web-scrapers/helper/`

    * After collecting the reviews from each website, merge all the reviews into a single dataset for analysis using `3merger.ipynb` which is in `1-web-scrapers/helper/`.

2. ## Text Preprocessing
    The collected reviews undergo the following preprocessing steps:
    * **Translation of Foreign Languages**
    * **Lowercase Conversion**
    * **Removal of Punctuation**
    * **Removal of Numerical Expressions**
    * **Removal of Stopwords**
    * **Tokenization**
    * **Lemmatization**
3. ## ML Model
    There are six types of ml model which have tried
    * Vader
    * RoBERTa
    * TextBlob
    * XGBoost
    * Random Forest
    * Sector Vector

At the end we choosed two model beacause of high accuracy they are:

`Vader`
`RoBERTa`

* Vader has given the initial sentiment of the all the reviews and stored in csv file.
* Later RoBERTa was trained on that data.

### Location of code:
**Vader :** `2-ml-model/3-model_code/vader_textblob.ipynb`

**RoBERTa** `2-ml-model/3-model_code/roberta_senti.ipynb`

3. ## Insights

    1. ### EDA
    2. ### Technical Review Summarization
        * Technical reviews are Summarized in 10 lines by bart-large-cnn.
    3. ### Product Prons & Cons
        * Filters the most common words in the review of product in positive and negative.
    4. ### Product Suggestion