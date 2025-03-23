## Scrapping World Data

WorldDataScraper is a Python-based web scraping project that extracts structured global data from Wikipedia. It utilizes BeautifulSoup and Pandas to scrape, clean, and analyze data, making it accessible for further research and visualization.

## Features
- Extracts tabular data from Wikipedia pages.
- Parses and cleans data for better usability.
- Converts extracted data into structured formats like CSV.
- Allows easy analysis using Pandas.
- Automates data retrieval for research and visualization.

## Installation
Ensure you have Python installed and clone the repository:

```sh
# Clone the repository
git clone https://github.com/yourusername/WorldDataScraper.git

# Navigate to the directory
cd WorldDataScraper

# Install dependencies
pip install -r requirements.txt
```

## Python Functionalities Used
WorldDataScraper utilizes the following Python functionalities:

- **Web Scraping with BeautifulSoup:** Extracts HTML content and retrieves table data.
- **HTTP Requests with Requests Library:** Fetches Wikipedia pages for data extraction.
- **Data Processing with Pandas:** Cleans and structures extracted data into DataFrames.
- **String Manipulation:** Cleans up raw text data by removing unwanted characters and formatting inconsistencies.
- **File Handling:** Exports structured data into CSV format for storage and further analysis.

## Usage
### Scraping Wikipedia Data
```python
import requests
from bs4 import BeautifulSoup
import pandas as pd

# Define Wikipedia URL
url = "https://en.wikipedia.org/wiki/List_of_countries_by_population"

# Fetch the webpage content
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')

# Extract table data
table = soup.find('table', {'class': 'wikitable'})
```

### Converting Data into Pandas DataFrame
```python
# Extract table rows
rows = table.find_all('tr')
data = []

for row in rows:
    cols = row.find_all(['td', 'th'])
    cols = [col.text.strip() for col in cols]
    data.append(cols)

# Convert to Pandas DataFrame
df = pd.DataFrame(data)
df.head()
```

### Saving Data to CSV
```python
# Save to CSV
df.to_csv('world_population.csv', index=False)
print("Data saved successfully!")
```

## Project Structure
```
WorldDataScraper/
│── scraper.py          # Core script for scraping
│── data/               # Folder for storing extracted CSV files
│── notebooks/          # Jupyter notebooks for analysis
│── README.md           # Project documentation
│── requirements.txt    # Dependencies
```



