Here’s an updated README.md file tailored to your GoMarble assignment using Flask and an LLM CSS selector scraper in the utils folder:

---

# GoMarble: Review Extraction API

## Objective

This API extracts reviews from product pages (e.g., Shopify, Amazon) using Flask and a Large Language Model (LLM) to dynamically identify CSS selectors for reviews. The API handles pagination and ensures compatibility with different review pages.

## Project Structure

plaintext
go-marble-review-extraction-api/
├── app/
│   ├── __init__.py                # Marks the directory as a Python package
│   ├── main.py                    # Flask app (entry point)
│   ├── api/                       # API-specific functionality
│   │   ├── __init__.py
│   │   ├── reviews.py             # Endpoint handling and review extraction logic
│   │   ├── utils.py               # Helper functions (including LLM CSS selector scraper)
│   ├── .env                       # Store environment variables (e.g., OPENAI_API_KEY)
├── requirements.txt               # Python dependencies
├── .gitignore                     # Git ignore file
├── README.md                      # Project overview, instructions, and documentation
└── tests/                         # Unit tests for the project
    ├── __init__.py
    ├── test_api.py                # Unit tests for API endpoints
    ├── test_browser.py            # Unit tests for scraping logic
    ├── test_llm.py                # Unit tests for LLM integration


## Functional Requirements

- *Dynamic CSS Identification*: Use an LLM (e.g., OpenAI) to identify dynamic CSS selectors for reviews on the given product page.
- *Pagination Handling*: The API navigates through multiple pages of reviews to retrieve all available reviews.
- *Universal Compatibility*: Ensure the API works across different product pages with various review structures.

## API Endpoint

### GET /api/reviews

This endpoint extracts reviews from a given product page.

*Request*:
plaintext
GET /api/reviews?page=<product_page_url>


- page: The URL of the product page from which reviews will be extracted.

*Response*:
json
{
  "reviews_count": 100,
  "reviews": [
    {
      "title": "Review Title",
      "body": "Review body text",
      "rating": 5,
      "reviewer": "Reviewer Name"
    },
    ...
  ]
}


### Example Request:
plaintext
GET /api/reviews?page=https://example.com/product


### Example Response:
json
{
  "reviews_count": 50,
  "reviews": [
    {
      "title": "Great product!",
      "body": "I really liked this product. It works as expected.",
      "rating": 5,
      "reviewer": "John Doe"
    },
    ...
  ]
}


## Setup Instructions

### 1. Clone the repository
bash
git clone https://github.com/yourusername/go-marble-review-extraction-api.git
cd go-marble-review-extraction-api


### 2. Install dependencies
bash
pip install -r requirements.txt


### 3. Set environment variables
Create a .env file in the root directory and add your OpenAI API key (if using OpenAI for CSS selector identification).

plaintext
OPENAI_API_KEY=your_openai_api_key


### 4. Run the Flask app
bash
python app/main.py


The API will be available at http://127.0.0.1:5000.

## Usage

Once the server is running, you can send a GET request to /api/reviews with a page query parameter (product page URL) to get the reviews.

### Example:
bash
curl "http://127.0.0.1:5000/api/reviews?page=https://2717recovery.com/products/recovery-cream"


This will return a JSON response with the reviews of the product.

## Project Details

- *Flask*: Used for building the API.
- *LLM for CSS Selector Scraping*: The utils.py script uses an LLM (e.g., OpenAI API) to identify the CSS selectors dynamically based on the HTML structure of the product page.
- *Browser Automation: We use **Playwright* (or *Selenium*) for simulating the browser behavior and scraping the content (such as reviews) from the page.

## Testing

To run the tests, use pytest:

bash
pytest


This will run all the unit tests defined in the tests/ folder.

### Test Coverage:
- *test_api.py*: Tests for the /api/reviews endpoint.
- *test_browser.py*: Tests for scraping logic using Playwright/Selenium.
- *test_llm.py*: Tests for LLM integration and CSS selector scraping.

## Contributions

Feel free to fork and contribute to this project. If you encounter any issues, please open an issue in the GitHub repository.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

This structure and README file provide a clean approach to building and documenting the Flask API with the LLM CSS selector scraper for your task. Let me know if you need any further adjustments!
