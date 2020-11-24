# Web Scrapping

## Overview
Testing out basic web scrapper using Python. 
- scrap timejobs.com
- function will make request from job-search with python as a required skill on timejobs.com
- function will find all recently posted jobs by 'few' keyword in published date
- request user input to filter out skills user is unfamiliar with
- result will be stored locally in separate txt files
- function will scrape every 10 minutes

## Setting up python locally
- [Python on VSCode](https://code.visualstudio.com/docs/python/python-tutorial)
- `py -3 --version` (Python 3.9.0)
- `pip install beautifulsoup4` [beautifulSoup doc](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- `pip install lxml`
- `pip install requests`
- `pip install time`

## Running it locally
- open terminal and cd to project dir
- run `python main.py`

## Notes
- Web scraping is the process of getting information from the internet, typically involving automation
- Automated web scraping can be useful to speed up the data collection process. Write code once and let it gather information that you want many times from many pages
- Scraping APIs is generally more stable than parsing HTML [API integration in Python](https://realpython.com/api-integration-in-python/)

## Basic Steps for scraping a typical site
1. Explore the website you want to scrape
2. Decipher the information in URLs (Base URL & query parameters)
3. Inspect the site using developer tools (interactively explore the site's DOM)
4. Scrape HTML content from a page (use python's requests library)
```python
import requests

URL = 'https://www.monster.com/jobs/search/?q=Software-Developer&where=Las-Vegas'
page = requests.get(URL)
```
5. Parse HTML code with Beautiful Soup (Python library for parsing structured data)
```python
import requests
from bs4 import BeautifulSoup

URL = 'https://www.monster.com/jobs/search/?q=Software-Developer&where=Las-Vegas'
page = requests.get(URL)

soup = BeautifulSoup(page.content, 'html.parser')
```
6. Find elements by ID, HTML class name, or text content
7. Pass a function to a beautiful soup method
```python
python_jobs = results.find_all('h2',
                               string=lambda text: 'python' in text.lower())
```
8. Extract attributes from HTML elements
```python
python_jobs = results.find_all('h2',
                               string=lambda text: "python" in text.lower())

for p_job in python_jobs:
    link = p_job.find('a')['href']
    print(p_job.text.strip())
    print(f"Apply here: {link}\n")
```



