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
    
    * If there are multiple processors from a single website, then merge them all using `multimerger.ipynb` located in `1-web-scrapers/helper/multimerger.ipynb`.

    * After collecting the reviews from each website, merge all the reviews into a single dataset for analysis using `3merger.ipynb` found in `1-web-scrapers/helper/3merger.ipynb`.

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

    Six types of machine learning models were tried:
    * VADER
    * RoBERTa
    * TextBlob
    * XGBoost
    * Random Forest
    * Sector Vector

    At the end, two models were chosen due to their high accuracy:
    `VADER`
    `RoBERTa`

    * VADER provided the initial sentiment of all the reviews, which were stored in a CSV file.
    * RoBERTa was then trained on that data.

    ### Location of Code:
    **VADER:** `2-ml-model/3-model_code/vader_textblob.ipynb`

    **RoBERTa:** `2-ml-model/3-model_code/roberta_senti.ipynb`

4. ## Insights

    1. ### Exploratory Data Analysis (EDA)
    2. ### Technical Review Summarization
        * Technical reviews are summarized in 10 lines using bart-large-cnn.
    3. ### Product Pros & Cons
        * Filters the most common words in the product reviews, categorized as positive and negative.
    4. ### Product Suggestions
