IMDB Scraper
============

Part of CS685A: Data Mining Project  
See [box-office-knowledge-discovery](https://github.com/pawan47/box-office-knowledge-discovery) (on GitHub) for entire project  

Overview
--------

This is a data collection program to collect movies data from IMDB.  
The working of this program depends on the structure of the IMDB website and may not work effectively if the website format of IMDB changes post testing of the program.  
Last Tested: November 25, 2018  

Requirement
-----------

* Python 3.6 or above
* Scrapy

Instructions
------------

To run the program follow the instructions below:  

1. Install Scrapy: `pip install scrapy` or if you use anaconda, `conda install scrapy`

2. Clone the repository and enter into the **data-collection** folder of the repository  
```
git clone https://github.com/pawanmsr/imdb-scraper
cd path/to/cloned-directory
```

3. Enter `scrapy list` on the terminal to obtain the list of spider programs and related instructions.  
There are two spider programs: **imdbLinks** and **movieCrawler**  
**movieCrawler** is the main spider program and it can only be run after seed urls have been collected and saved. To obtain the seed urls run **imdbLinks** spider; enter `scrapy crawl imdbLinks` in the terminal.  
This program will save a JSON file (**imdbLinks.json**) to **links** folders. This file contains a dictionary of links that will be used by the main spider program to crawl through the *IMDB* website.

4. To run the main spider program, enter `scrapy crawl movieScraper` in the terminal. This program will scrape the necessary information from *IMDB* movie pages and then follow the links on the page to other movie pages. All data of a particular movie is saved in a *JSON* file in the **movies** folder. No provision has been made in the program to automatically stop. Manually stop the program once enough data has been collected.

Method
------

The has been collected by recursively following links on movies pages of *IMDB* website. The starting urls are the links to *IMDB* top 250 movies. Patterns in the movie webpage have been identified and by element analysis of the pages, the necessary information has been picked. **xpath** has been used to pick information. Following information is collected for each movie (most of the fields are self-explanatory):

* Id: unique identification string for each movie
* Title
* Film_rating: who can watch the movie; PG-13, R and so on
* Duration
* Description
* IMDB_Rating
* IMDB_rating_count: number of people who have rated the movie
* Genre
* release_data
* Storyline
* Cast
* Taglines
* Director
* Writers
* Budget
* Revenue
* Country
* Language
* url

Each file is saved with *Id* as filename.