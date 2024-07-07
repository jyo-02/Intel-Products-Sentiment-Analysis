<div align="center">
    <h1 align="center">Intel Products Sentiment Analysis From Online Reviews</h1>
</div>

The objective of this project is to conduct Sentiment Analysis on customer reviews sourced from prominent E-commerce platforms for various Intel Processors, aiming to classify sentiments. This analysis will assist Intel in improving product features and boosting sales performance through actionable insights derived from customer satisfaction and feedback.

## Getting Started
Clone the repository:
   ```bash
   git clone https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis.git
   ```

Install the required dependencies with: `pip install -r requirements.txt --upgrade`.

## Dataset Information

We utilize various sentiment analysis models on reviews. The training dataset is expected to be a csv file with columns: `Product` (Intel Processor names), `Rating` (user star ratings), `Date` (review dates), `Source` (review origin), `Review` (user feedback), and `Sentiment` (coded as 1 for positive and 0 for negative). Ensure CSV headers are excluded from both training and test datasets.

# Project Workflow

1. ## Web Scraper
    The `1-web-scrapers` folder contains four web scrapers designed for different platforms:

    1. ### [Amazon](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/1-amazon/amazon_scraper.ipynb)
        * `BeautifulSoup` and `Splash in Docker` are used to scrape reviews from various regional domains of Amazon worldwide, including India, the US, the UK, Japan, and more.
        * Add the URL and name of the processor in a text file and run the scraper.
        * Code Location: `1-web-scrapers/1-amazon/amazon_scraper.ipynb`
        * All the files of scraped reviews will be stored in `1-web-scrapers/5-data/amazon-dataset`

    2. ### [BestBuy](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/2-bestbuy/bestbuy_scraper.ipynb)
        * `BeautifulSoup` is employed to scrape reviews from BestBuy.
        * Add the URL and name of the processor in a text file and run the scraper.
        * Code Location: `1-web-scrapers/2-bestbuy/bestbuy_scraper.ipynb`
        * All the files of scraped reviews will be stored in `1-web-scrapers/5-data/bestbuy-dataset`

    3. ### [Flipkart](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/3-flipkart/Flipkart_Scraper.ipynb)
        * `BeautifulSoup` is employed to scrape reviews from Flipkart.
        * Add the URL and name of the processor in a text file and run the scraper.
        * Code Location: `1-web-scrapers/3-flipkart/flipkart_scraper.ipynb`
        * All the files of scraped reviews will be stored in `1-web-scrapers/5-data/flipkart-dataset`

    4. ### [Technical Reviews](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/1-web-scrapers/4-technical/technical-scraper.ipynb)
        * `Selenium` is used to scrape reviews from technical review sites such as Tom's Hardware and PCMag.
        * Add the names of all processors in a text file and run the scraper.
        * Code Location: `1-web-scrapers/4-technical/technical-scraper.ipynb`
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
    
    Code Location: `1-web-scrapers/6-data-pre-processing-nlp/data-pre-processing-nlp.ipynb`

    Saved Location: `1-web-scrapers/5-data/cleaned-all-products-data.csv`

3. ## ML Models

    Six different Machine Learning Models were tried:
    * VADER
    * RoBERTa
    * TextBlob
    * XGBoost
    * Random Forest
    * Sector Vector

    At the end, two models were selected based on their high accuracy:
    
    [`VADER`](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/2-ml-model/3-model_code/vader_textblob.ipynb)
    [`RoBERTa`](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/2-ml-model/3-model_code/roberta_senti.ipynb)

    * VADER provided the initial sentiment of all the reviews, which were stored in a CSV file `2-ml-model/1-review_data/dataset_7(senti)_vader.csv`.
    * RoBERTa was trained on that data and used to obtain valuable insights.

    ### Location of Code:
    **VADER:** `2-ml-model/3-model_code/vader_textblob.ipynb`

    **RoBERTa:** `2-ml-model/3-model_code/roberta_senti.ipynb`

    * Note: Run the VADER model first and RoBERTa later, which will provide the sentiment of each review which is stored in `2-ml-model/1-review_data/dataset_7(senti)_vader.csv`.

4. ## Insights

    1. ### [Exploratory Data Analysis (EDA)](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/3-insights/1-eda/scripts)
        * Pre-Sentiment Analysis EDA explores the Intel Processors' dataset after Web Scraping. <br/>
        Code Location: `3-insights/1-eda/scripts/1-data-exploration-initial.ipynb`.
        * Post-Sentiment Analysis EDA  analyses Intel Processors' sentiment trends. <br/>
        Code Location: `3-insights/1-eda/scripts/1-data-exploration-final.ipynb`.
        
    2. ### [Technical Review Summarization](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/3-insights/2-techical-reviews-summarization/1-technical-reviews-summarization.ipynb)
        * Technical reviews are summarized in 10 lines using `bart-large-cnn`.
        * Code Location: `3-insights/2-technical-reviews-summarization/1-technical-reviews-summarization.ipynb`.
        * All the summarizations are stored in `3-insights/2-technical-reviews-summarization/3-summarized-review.csv`.
    3. ### [Product Pros & Cons](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/3-insights/3-product-pros-cons/1-product-pros-cons.ipynb)
        * Filters the most common words in the product reviews, categorized as positive and negative.
        * Code Location: `3-insights/3-product-pros-cons/1-product-pros-cons.ipynb`.
        * Inside the above file, you can find all the summarizations of processors.
    4. ### [Product Suggestions](https://github.com/viswachaitanyasai/Intel-Products-Sentiment-Analysis/blob/main/3-insights/4-products-suggestions/1-products-suggestion.ipynb)
        * Provides suggestions on Product Improvements using `Topic Modeling`
        * Code Location: `3-insights/4-products-suggestions/1-products-suggestion.ipynb`.

## Information about other files

* `2-ml-model/1-review_data/random25_7_reviews.csv`: Dataset used to train the RoBERTa.
* `2-ml-model\4-ml_trained_model\roberta_senti`: Trained RoBERTa model.