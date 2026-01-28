# CS-Labs-web-scraping
A Python script designed to extract data from [https://books.toscrape.com/](https://books.toscrape.com/)
The project contains functions for the initial web scraping, data deduplication, and API calls.

## Key Features
1. Category Discovery: Retrieves the category list from the homepage sidebar.
2. Pagination Handling: Handles categories with multiple pages by locating the 'Next' button and clicking to get to the next page. 
3. Data Normalization: Uses a dictionary to make sure that there are no duplicate entries of books. If a book belongs to multiple categories, then the script merges the categories together and uses comma separation.
4. Connects to the ExchangeRate-API to fetch real-time GBP to EUR conversion rates.
5. Data Enrichment: Automatically generates a unique ID for every record and adds a timestamp for data extraction.

## Technical Stack
Python 3
### Libraries
1. Requests: For handling HTTP requests.
2. BeautifulSoup: For parsing HTML and DOM navigation.
3. Pandas: For data cleaning, transformation, and CSV export.
4. Regex (re): For cleaning and formatting price strings.

## Project Structure
- ├── CS_Labs_detyra_22_01.ipynb   # Original research and development notebook
- ├── main.py                     # Cleaned, production-ready Python script
- └── books_data.csv              # Final output (1,000 unique books)

## Project Steps
1. Find Categories: The script looks at the sidebar and gets links for every genre (Travel, Mystery, etc.).
2. Read Pages: It goes through every page of every category by clicking the "Next" button automatically.
3. Save Unique Books: If it sees a new book, it saves the Title, Price, and Category. If it sees the same book again in a different category, it just adds the new category to the first one.
4. Convert Money: It asks an API for the current GBP to EUR rate and calculates the new price.
5. Create File: It saves the final list of books into books_data.csv.

## Setup and Usage Instructions
1. Create an API Key at: https://www.exchangerate-api.com
3. Clone the repository: git clone https://github.com/4ndr-34/CS-Labs-web-scraping.git
4. Insert API Key at main.py line 86
5. Move to Project: cd CS-Labs-web-scraping
6. Install dependencies: pip install -r requirements.txt
7. Run the scraper: python main.py

## Test 
After testing for double categories, I found out that none of the books have two or more categories, but I did add a testcase to be sure. It can be seen in the notebook.
