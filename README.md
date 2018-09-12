# Fortune 500

This project scrapes data from Fortune.com's [Fortune500 list](http://www.fortune.com/Fortune500).

Optimally, we would be able to use the `requests` library to download the html file of interest and process the data directly. Unfortunately, though, Fortune.com has their list set up such that it only partially loads the data to the html file on initlal request, and the html file gets updated when the page is scrolled to the bottom. 

## Inputs
To deal with this, I've downloaded the html files of interest manually and saved them in the `input/` directory.

There are 3 separate html files for each year between 2015 and 2018 (12 html files in total). One file each for:
* revenues
* profits
* assets

Two Example URLs:  
* [http://fortune.com/fortune500/2017/list/filtered?sortBy=revenues&first500](http://fortune.com/fortune500/2017/list/filtered?sortBy=reveunes&first500)
* [http://fortune.com/fortune500/list/filtered?sortBy=assets&first500](http://fortune.com/fortune500/list/filtered?sortBy=assets&first500)

### Notes about the data
* Need the `&first500` suffix to limit data to only the top 500 companies (otherwise top 1,000 (or more) are returned)
* Don't need the year in the URL for the current year data
* The top 500 companies in the Fortune500 list are ranked by revenues
* Prior to 2015, Fortune.com has the company names and rank available, but no additional financial information

## Code
The data scraping was done in python, and executed in a Jupyter notebook (`Fortune500.ipynb`). See `ENVIRONMENT.md` for details/requirements.

## Output
The `output\` directory contains the csv file of interest. 

The file has six columns:
1) year
2) company
3) rank
4) revenues
5) profits
6) assets

There are 2,000 rows in the file (500 * 4 years).

