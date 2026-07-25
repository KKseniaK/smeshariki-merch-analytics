# Smeshariki Analytics: Economics of Nostalgia

> Exploratory Data Analysis of Smeshariki Merchandise across E-Commerce Platforms

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![pandas](https://img.shields.io/badge/pandas-2.0+-150458?logo=pandas)
![Selenium](https://img.shields.io/badge/Selenium-4.0+-43B02A?logo=selenium)
![Grade](https://img.shields.io/badge/Academic%20Grade-9%2F10-success)
![License](https://img.shields.io/badge/License-MIT-green.svg)

---

![Price Distribution Banner](assets/price_distribution.png)

---

## About

An exploratory data analysis (EDA) of the commercial merchandise market surrounding the [Smeshariki](https://smeshariki.ru/) brand. The project aggregates, cleans, and analyzes retail data collected from major Russian marketplaces and niche brand stores to examine pricing strategies, discount depths, and seller network distributions.

Developed as a university project centered on automated data ingestion, data quality assurance (QA), statistical profiling, and e-commerce market segmentation. **Evaluated with a grade of 9/10.**

---

## Dataset Overview & Sources

> *"Analyzing 2,962 unique product listings across 5 distinct retail channels..."*

The final aggregated dataset covers **2,962 unique product items** and **20 features** collected across 5 primary sources:

* **Major E-Commerce Platforms:** Wildberries, Ozon.
* **Official Merchandise:** Riki Shop.
* **Niche & Brand Partners:** SASONKO Jewelry House, Two Balls (*Два мяча*).

---

## Data Collection & Pipeline Architecture

The project relies on an automated, multi-stage ETL (Extract, Transform, Load) pipeline designed to extract structured commercial data from both static web pages and complex dynamic marketplaces.

### 1. Dynamic Web Scraping (`Selenium WebDriver`)
* **Dynamic Content Rendering:** Utilized Selenium with headless browser configurations to render JavaScript-heavy interfaces, infinite scrolls, and lazy-loaded product cards on platforms like Wildberries and Ozon.
* **Interaction Handling:** Automated page navigation, element waiting (`WebDriverWait`), and click actions to capture full pagination depth and hidden metadata (such as full seller details and raw discount tags).
* **Robustness & Rate Limiting:** Implemented request throttling, realistic user-agent rotation, and implicit/explicit waits to bypass anti-bot challenges and ensure continuous data extraction without session drops.

### 2. Extraction & Parsing
* Extracted raw HTML DOM elements and converted them into structured dictionary records containing essential commercial tags: prices, base/discount rates, seller names, platform ratings, review counts, and product URLs.

### 3. Data Cleaning & Quality Assurance (QA)
* **Deduplication:** Applied signature-based deduplication across `product_id` and unique source links to eliminate overlaps.
* **Type Normalization:** Standardized currency fields (removing `₽` symbols, converting string formats to float/int) and parsed nested ratings/review counts.
* **Null Value Management:** Handled missing attributes systematically, verifying a 100% completion rate across critical commercial metrics.

---

## Visualizations & Interface

### Price Distribution & Discount Depth
![Price Distribution](assets/price_distribution.png)

* **Base Prices:** Ranging from 115 ₽ to 101,364 ₽.
* **Discount Prices:** Ranging from 53 ₽ to 90,000 ₽.

### Marketplace Distribution & Seller Ecosystem
![Marketplace Share and Top Sellers](assets/marketplaces_share.png)

* **Platform Coverage:** Distribution analysis across mass market platforms and specialized brand stores.
* **Licensing Network:** Mapping of 292 unique sellers and 31 licensed brands represented in the dataset.

---

## Key Findings & Market Insights

* **Data Integrity & Completeness:** Complete absence of full duplicates or `product_id` overlaps (0%). Critical commercial attributes (`product_name`, `price`, `discount_price`, `seller`, `marketplace`, `link`) exhibit a 100% completion rate.
* **Two-Tier Market Segmentation:**
  * **Mass Market (Children/Household):** Low-cost stationery, books, small toys, and tableware.
  * **Premium / Nostalgic Merch (Adults):** High-ticket collectibles, fine jewelry, and designer apparel targeting long-time adult fans.
* **User Feedback Coverage:** User rating and review metrics are present for **97.91%** of all analyzed listings.

---

## Tech Stack & Methodology

* **Data Ingestion & Scraping:** Python, Selenium WebDriver, BeautifulSoup4, Requests
* **Data Processing & Analysis:** pandas, numpy
* **Visualization:** matplotlib, seaborn
* **Environment:** Google Colab, Jupyter Notebook
* **Methodology:** Automated Ingestion, DOM Parsing, Data Quality Assurance (QA), Descriptive Statistics, Correlation Analysis, E-Commerce Market Segmentation
