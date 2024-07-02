<div align="center">
    <h1 align="center">Intel Sentiment Analysis</h1>
</div>

The goal of this project is to perform sentiment analysis on customer reviews to classify sentiments. This analysis will assist companies in improving product features and increasing sales performance by leveraging customer satisfaction and feedback.

## Getting Started

Install the required dependencies with: `pip install -r requirements.txt --upgrade`.

# Project Workflow

1. ## Web Scraper
    The `1-web-scrapers` folder contains four web scrapers designed for different platforms:

    1. ### [Amazon](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/1-amazon/amazon_scraper.ipynb)
        * `BeautifulSoup` and `Splash` in Docker are used to scrape reviews from all Amazon regions worldwide, including India, the US, the UK, Japan, and more.
        * Add the URL and name of the processor in a text file and run the scraper.
        * Code location: `1-web-scrapers/1-amazon/amazon_scraper.ipynb`
        * All the files of scraped reviews will be stored in `1-web-scrapers/5-data/amazon-dataset`

    2. ### [BestBuy](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/2-bestbuy/bestbuy_scraper.ipynb)
        * `BeautifulSoup` is employed to scrape reviews from BestBuy.
        * Add the URL and name of the processor in a text file and run the scraper.
        * Code location: `1-web-scrapers/2-bestbuy/bestbuy_scraper.ipynb`
        * All the files of scraped reviews will be stored in `1-web-scrapers/5-data/bestbuy-dataset`

    3. ### [Flipkart](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/3-flipkart/Flipkart_Scraper.ipynb)
        * `BeautifulSoup` is employed to scrape reviews from Flipkart.
        * Add the URL and name of the processor in a text file and run the scraper.
        * Code location: `1-web-scrapers/3-flipkart/flipkart_scraper.ipynb`
        * All the files of scraped reviews will be stored in `1-web-scrapers/5-data/flipkart-dataset`

    4. ### [Technical Reviews](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/4-technical/technical-scraper.ipynb)
        * `Selenium` is used to scrape reviews from technical review sites such as Tom's Hardware and PCMag.
        * Add the names of all processors in a text file and run the scraper.
        * Code location: `1-web-scrapers/4-technical/technical-scraper.ipynb`
        * All the files of scraped reviews will be stored in `1-web-scrapers/5-data/technical-dataset`

* Save all the website links and processor names in their respective text files. Run each program as needed to collect the data.

* If there are multiple processors from a single website, then merge them all using `multimerger.ipynb` located in `1-web-scrapers/helper/multimerger.ipynb`.

* After collecting the reviews from each website, merge all the reviews into a single dataset for analysis using `3merger.ipynb` found in `1-web-scrapers/helper/3merger.ipynb`.

* All the reviews will be saved in a CSV file located at `1-web-scrapers/5-data/all-products-data.csv`.

2. ## [Text Preprocessing](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/6-data-pre-processing-nlp/data-pre-processing-nlp.ipynb)

    The collected reviews undergo the following preprocessing steps:
    * Translation of Foreign Languages
    * Lowercase Conversion
    * Removal of Punctuation
    * Removal of Numerical Expressions
    * Removal of Stopwords
    * Tokenization
    * Lemmatization
    
    Code location: `1-web-scrapers/6-data-pre-processing-nlp/data-pre-processing-nlp.ipynb`

    saved location: `1-web-scrapers/5-data/cleaned-all-products-data.csv`

3. ## ML Model

    Six types of machine learning models were tried:
    * VADER
    * RoBERTa
    * TextBlob
    * XGBoost
    * Random Forest
    * Sector Vector

    At the end, two models were chosen due to their high accuracy:
    
    [`VADER`](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/2-ml-model/3-model_code/vader_textblob.ipynb)
    [`RoBERTa`](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/2-ml-model/3-model_code/roberta_senti.ipynb)

    * VADER provided the initial sentiment of all the reviews, which were stored in a CSV file `2-ml-model/1-review_data/dataset_7(senti)_vader.csv`.
    * RoBERTa was then trained on that data.

    ### Location of Code:
    **VADER:** `2-ml-model/3-model_code/vader_textblob.ipynb`

    **RoBERTa:** `2-ml-model/3-model_code/roberta_senti.ipynb`

    * Run the VADER model first and later RoBERTa, which will provide the sentiment of each review which is stored in `2-ml-model/1-review_data/dataset_7(senti)_vader.csv`.

4. ## Insights

    1. ### Exploratory Data Analysis (EDA)
    2. ### [Technical Review Summarization](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/3-insights/2-techical-reviews-summarization/1-technical-reviews-summarization.ipynb)
        * Technical reviews are summarized in 10 lines using `bart-large-cnn`.
        * Code location: `3-insights/2-technical-reviews-summarization/1-technical-reviews-summarization.ipynb`.
        * All the summarizations are stored in `3-insights/2-technical-reviews-summarization/3-summarized-review.csv`.
    3. ### [Product Pros & Cons](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/3-insights/3-product-pros-cons/1-product-pros-cons.ipynb)
        * Filters the most common words in the product reviews, categorized as positive and negative.
        * Code location: `3-insights/3-product-pros-cons/1-product-pros-cons.ipynb`.
        * Inside the above file, you can find all the summarizations of processors.
    4. ### Product Suggestions