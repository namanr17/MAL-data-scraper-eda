# MyAnimeList Web Scraper

----------
## PLUGINS
----------

Software: Jupyter notebook  
    Shell scripts run jupyter notebooks in python3 env.

Environment: Python 3.8.10  
    Environment in which jupyter notebooks are executed.


---------------
## DEPENDENCIES
---------------

### Libraries: Python packages  
    Can be installed using the following command "$pip install -r requirements.txt"  

    -> Pandas 1.3.4             : For dataset manipulation, data analysis, time series & statistics.
    -> NumPy 1.21.4             : For mathematical functions & array computations.
    -> nbconvert 6.2.0          : Converts Jupyter Notebooks
    -> requests 2.22.0          : Python HTTP for Humans.
    -> beautifulsoup4 4.10.0    : Screen-scraping library.
    -> wordcloud 3.3.4          : creation of wordcloud
    -> nltk 3.2.1               : Natural Language processing library used for sentiment analysis
    -> vader 0.0.2              : tool used for calculation of sentiment scores (positive, negative, neutral and compound)
        - nltk.downloader.download('vader_lexicon')
        - nltk.download('stopwords')
        - nltk.download('averaged_perceptron_tagger')
        - nltk.download('wordnet')


### Datasets: 
Use semicolon(;) as seperator while reading CSV files.  

    -> `anime-info-main.csv`:  
        Contains information(features) of anime(s) scraped from myanimelist platform.  
        SOURCE URL EXAMPLE: 'https://myanimelist.net/anime/1535/Death_Note'

    -> `anime-review-main.csv`:  
        Contains reviews of anime(s) by users scrapped from myanimelist platform.
        SOURCE URL EXAMPLE: 'https://myanimelist.net/anime/1535/Death_Note'

    -> `anime-info-main-clean.csv`:
        Clean (preprocessed) version of `anime-info-main.csv`.
        

------------------------------
## NOTEBOOKS (PIPELINE STAGES)
------------------------------

Stage 1 (Data Extraction):
--------------------------

IPynb files in this stage are as follows:

    -> `myanimelist_url_scraper.ipynb`:
        Scraps the URLs of all anime(s) from `myanimelist.com` and saves them in `anime-urls-main.csv`
        Maximum number of threads for multithreading = 30  
        Maximum wait time between requests = 0.2 s  

        Run `$jupyter nbconvert --to notebook --execute --inplace myanimelist_url_scraper.ipynb` command to execute.

    -> `myanimelist_data_scraper.ipynb`:  
        Scraps the anime data (info & reviews) for all anime(s) from `myanimelist.com` and saves them in `anime-info-main.  csv` & `anime-review-main.csv`.  
        Optimal number of cores for multiprocessing = 8  
        Maximum number of threads for multithreading = 30  
        Maximum wait time between requests = 1.0 s  

        Run `$jupyter nbconvert --to notebook --execute --inplace myanimelist_data_scraper.ipynb` command to execute.

NOTE: Run time of web scraper on personal system was around an hour and might need human intervention due to server defences against DDoS.  


Stage 2 (Data Cleaning & EDA):
------------------------------

IPynb files in this stage are as follows:

    -> `myanimelist_data_cleaning.ipynb`:
        

    -> `myanimelist_data_analysis.ipynb`:
        