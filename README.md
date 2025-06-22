# Yahoo Finance Trending Stocks Scraper

## Project Description

This project provides a robust and professional Python script for scraping trending stock data from Yahoo Finance. It leverages `Selenium` for web automation, `Pandas` for data processing and cleaning, and exports the final structured data into an Excel file. This tool is designed for efficient and reliable extraction of key financial metrics for top-trending tickers.

## Features

  * **Automated Web Scraping:** Uses Selenium to navigate and extract data from dynamic web pages on Yahoo Finance.
  * **Headless Browser Support:** Runs the browser in headless mode by default, allowing for background execution without a graphical user interface.
  * **Configurable:** URLs, XPath selectors, and output file names are defined as constants for easy customization.
  * **Robust Error Handling:** Implements `try-except` blocks to gracefully handle common web scraping issues like timeouts, missing elements, and general WebDriver errors.
  * **Structured Logging:** Utilizes Python's `logging` module to provide informative messages about the scraping process, status, warnings, and errors.
  * **Data Cleaning & Transformation:**
      * Converts raw text data (e.g., "1.23M", "50%") into numerical formats.
      * Splits the "52-Week Range" into separate "Low" and "High" columns.
      * Handles potential irregularities in scraped rows (e.g., missing or extra columns).
  * **Excel Export:** Saves the cleaned and structured data into a user-friendly `.xlsx` file.
  * **Preview Output:** Prints a markdown-formatted preview of the processed DataFrame in the console/notebook output.

## Prerequisites

Before running this script, ensure you have the following installed:

  * **Python 3.x:** (e.g., Python 3.8 or newer is recommended).
  * **pip:** Python's package installer (usually comes with Python).
  * **Google Chrome Browser:** Required for Selenium.
  * **ChromeDriver:** The WebDriver for Chrome. Make sure its version matches your Chrome browser's version and that `chromedriver.exe` (or `chromedriver` on Linux/macOS) is in your system's PATH.
      * You can download ChromeDriver from [here](https://chromedriver.chromium.org/downloads).

## Installation

1.  **Clone the repository (if applicable) or download the `Yahoo-finance.ipynb` file.**

2.  **Create a Virtual Environment (Recommended):**

    ```bash
    python -m venv venv
    ```

3.  **Activate the Virtual Environment:**

      * **Windows (Command Prompt):**
        ```bash
        venv\Scripts\activate.bat
        ```
      * **Windows (PowerShell):**
        ```bash
        .\venv\Scripts\Activate.ps1
        ```
      * **macOS/Linux:**
        ```bash
        source venv/bin/activate
        ```

4.  **Install Required Python Libraries:**

    ```bash
    pip install pandas selenium openpyxl
    ```

      * `pandas`: For data manipulation and DataFrame creation.
      * `selenium`: For web scraping and automation.
      * `openpyxl`: Required by pandas to write to `.xlsx` files.

## Usage

1.  **Open the Jupyter Notebook:**

    ```bash
    jupyter notebook Yahoo-finance.ipynb
    ```

2.  **Run Cells Sequentially:** Execute each cell in the notebook from top to bottom.

      * The first few cells handle imports, configurations, and function definitions.
      * The final cell (Main Execution Logic) will run the scraping process.

3.  **Output:**

      * The script will print log messages to your console/notebook output, indicating its progress, warnings, and any errors.
      * A markdown-formatted table showing the first few rows of the scraped data will be printed.
      * An Excel file named `yahoo_stocks_data.xlsx` will be created in the same directory as your notebook, containing the complete extracted and processed data.

## File Structure (within the Notebook)

The `Yahoo-finance.ipynb` notebook is structured into logical cells:

  * **Cell 1: Imports and Configuration**
      * Imports all necessary libraries and defines global constants for URLs, XPaths, and output file.
      * Sets up basic logging.
  * **Cell 2: WebDriver Initialization Function**
      * `initialize_webdriver()`: Configures and starts the Chrome WebDriver.
  * **Cell 3: Navigation Function**
      * `Maps_to_page()`: Handles navigating to specified URLs with WebDriverWait.
  * **Cell 4: Data Extraction Function**
      * `extract_trending_stock_data()`: Locates the stock data table and extracts information from its rows.
  * **Cell 5: Data Cleaning and Conversion Function**
      * `clean_and_convert_data()`: Processes raw scraped strings, converts types, and structures data into a Pandas DataFrame.
  * **Cell 6: Data Export Function**
      * `export_dataframe_to_excel()`: Saves the DataFrame to an Excel file.
  * **Cell 7: Main Execution Logic**
      * The primary execution block that calls all the functions in sequence, manages WebDriver lifecycle, and handles overall process flow.

## Error Handling & Logging

The script is designed with robustness in mind:

  * **Error Messages:** Specific error types (e.g., `TimeoutException`, `NoSuchElementException`) are caught and logged at appropriate levels (ERROR, WARNING, CRITICAL).
  * **`finally` Blocks:** Ensure that the WebDriver is properly closed (`driver.quit()`) even if exceptions occur during the scraping process.
  * **Informative Logs:** Check your console or notebook output for detailed log messages, which are invaluable for debugging.

-----
