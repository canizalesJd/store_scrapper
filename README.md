# Store Scrapper

## Overview

The **Store Scrapper** project is designed to scrape book data from the website [Books to Scrape](https://books.toscrape.com/), process the data, and serve it through a Flask API. The project is divided into two main parts: the data scraper and the API server.

- The scraper collects book data, including titles, prices, availability, and more, from all categories on the website.
- The scraped data is saved as a JSON file for easy access and manipulation.
- The Flask API provides endpoints to retrieve and search for books based on various criteria.

## Features

- **Scraping**: Automatically scrapes book data from the entire website.
- **Data Storage**: Stores the scraped data in a structured JSON format.
- **Flask API**: Serves the data through various API endpoints, including:
  - `/books`: Retrieve all books.
  - `/books/categories`: Retrieve all available categories.
  - `/books/<category>`: Retrieve books by category.
  - `/search?q=<query>`: Search for books by title.

## Project Structure

- `scrappers/books.py`: Contains the logic to scrape book data from the website.
- `main.py`: Executes the scraping process and saves the data as a JSON file for the API.
- `api/`: Contains the Flask API setup, including routes to serve the book data.
- `requirements.txt`: Lists all dependencies required to run the project.

## Installation

1. Clone the repository:
```
bash
git clone https://github.com/your-username/store_scrapper.git
cd store_scrapper
```

2. Create and activate a virtual environment (optional but recommended):
``` 
python3 -m venv venv
source venv/bin/activate
```

3. Install the required dependencies:
```
pip install -r requirements.txt
```

## Usage
### Running the Scraper
To scrape data from the website and generate the JSON file, run:
`python3 main.py`

## Running the Flask API
Once the data is scraped and stored, you can start the Flask API to serve the data:
```
cd api
python3 main.py
```

## Accessing the API
### Get all books:
- **Endpoint:** `GET /books`
- **Description:** Retrieves all books stored in the JSON data.
- **Sample Response:**
```
{
    "mystery": [
        {
            "id": "1",
            "title": "Sharp Objects",
            "price": "£47.82",
            "availability": "In stock",
            "image_url": "http://example.com/sharp-objects.jpg"
        },
        {
            "id": "2",
            "title": "The Girl on the Train",
            "price": "£39.99",
            "availability": "In stock",
            "image_url": "http://example.com/girl-on-train.jpg"
        }
    ],
    "fiction": [
        {
            "id": "3",
            "title": "The Night Circus",
            "price": "£20.99",
            "availability": "In stock",
            "image_url": "http://example.com/night-circus.jpg"
        }
    ],
    ...
}
```

### Get all categories: 
- **Endpoint:** `GET /books/categories`
- **Description:** Retrieves all available categories in the JSON data.
- **Sample Response:**
```
[
    "mystery",
    "fiction",
    "science_fiction",
    ...
]
```

### Get books by category:
- **Endpoint:** `GET /books/<category>`
- **Description:** Retrieves books by a specific category name
- **Sample Input:** `/books/mystery`
- **Sample Response:** 
```
[
    {
        "id": "1",
        "title": "Sharp Objects",
        "price": "£47.82",
        "availability": "In stock",
        "image_url": "http://example.com/sharp-objects.jpg"
    },
    {
        "id": "2",
        "title": "The Girl on the Train",
        "price": "£39.99",
        "availability": "In stock",
        "image_url": "http://example.com/girl-on-train.jpg"
    }
]
```

### Search books by title:
- **Endpoint:** `GET /search?q=<query>`
- **Description:** Searches for books by title based on the provided query.
- **Sample Input:** `/search?q=sharp`
- **Sample Response:** 
```
[
    {
        "id": "1",
        "title": "Sharp Objects",
        "price": "£47.82",
        "availability": "In stock",
        "image_url": "http://example.com/sharp-objects.jpg"
    }
]
```

## Contributing
Contributions are welcome! If you have suggestions or improvements, feel free to create an issue or submit a pull request.

## Acknowledgments
[Books to Scrape](https://books.toscrape.com/) for providing the data source used in this project.