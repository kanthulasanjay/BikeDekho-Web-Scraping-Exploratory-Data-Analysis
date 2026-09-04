# 🏍️ BikeDekho Web Scraping & Exploratory Data Analysis

## 📌 Project Overview

This project focuses on **web scraping and exploratory data analysis (EDA) of bikes and scooters listed on BikeDekho**.

The project extracts important bike specifications from BikeDekho using Python web-scraping techniques and analyzes the collected data to understand pricing, engine capacity, power, torque, and mileage patterns.

The data collection process uses `Requests` and `BeautifulSoup`, while `Pandas`, `NumPy`, `Matplotlib`, and `Seaborn` are used for data processing and visualization.

---

## 🎯 Objectives

* Scrape bike and scooter information from BikeDekho.
* Extract important specifications such as:

  * Bike Name
  * Price
  * Engine Capacity
  * Power
  * Torque
  * Mileage
  * Bike URL
* Convert scraped numerical values into appropriate data types.
* Identify missing values.
* Clean and prepare the dataset for analysis.
* Perform exploratory data analysis.
* Visualize relationships between different bike specifications.
* Save the scraped dataset for further analysis.

---

## 🌐 Data Source

The data was collected from:

**BikeDekho – New Bikes**

https://www.bikedekho.com/find-new-bikes

The source page contained hundreds of bikes and scooters at the time of scraping. The project selected bike URLs from the page and scraped individual bike pages for detailed specifications.

> ⚠️ **Note:** Website data can change over time. The scraped values in this repository represent the data collected when the notebook was executed.

---

## 🛠️ Technologies Used

| Technology       | Purpose                              |
| ---------------- | ------------------------------------ |
| Python           | Programming language                 |
| Requests         | Sending HTTP requests                |
| BeautifulSoup    | HTML parsing and web scraping        |
| Pandas           | Data manipulation and analysis       |
| NumPy            | Numerical operations                 |
| Matplotlib       | Data visualization                   |
| Seaborn          | Statistical visualization            |
| Jupyter Notebook | Development and analysis environment |

---

## 📂 Project Structure

```text
BikeDekho-EDA/
│
├── BikeDekho_EDA.ipynb
├── bikedekho_raw.csv
├── README.md
└── requirements.txt
```

---

## 🔎 Web Scraping Process

The project follows these major steps:

### 1. Import Libraries

The notebook uses Python libraries including:

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
import numpy as np
import re
import time

import matplotlib.pyplot as plt
import seaborn as sns
```

### 2. Access BikeDekho

The BikeDekho new-bikes page is accessed using `Requests` with a browser-style User-Agent.

### 3. Extract Bike URLs

The HTML page is parsed using BeautifulSoup and relevant bike URLs are extracted.

The notebook identified **26 bike URLs** for scraping.

### 4. Scrape Individual Bike Pages

A custom `scrape_bike()` function extracts information from individual bike pages.

The following fields are collected:

```text
Name
Price
Engine
Power
Torque
Mileage
URL
```

The scraper uses regular expressions to identify numerical specifications from the page text.

### 5. Create DataFrame

The scraped records are combined into a Pandas DataFrame.

The resulting dataset contains:

```text
26 rows × 7 columns
```

The seven columns are:

```text
Name
Price
Engine
Power
Torque
Mileage
URL
```

---

## 🧹 Data Cleaning

After scraping, the numerical columns are converted from strings into numeric data types.

```python
numeric_columns = [
    "Price",
    "Engine",
    "Power",
    "Torque",
    "Mileage"
]

for col in numeric_columns:
    df[col] = pd.to_numeric(df[col], errors="coerce")
```

This allows numerical analysis and visualization to be performed correctly.

---

## 🕵️ Missing Value Analysis

Missing values were identified using:

```python
df.isnull().sum()
```

The dataset initially contained missing values in several numerical columns, particularly Price, Engine, Power, Torque, and Mileage.

The notebook also investigates individual records with missing specifications and revisits their BikeDekho pages to identify why some values were not captured by the initial extraction pattern.

---

## 📊 Dataset Features

| Feature   | Description              |
| --------- | ------------------------ |
| `Name`    | Name of the bike/scooter |
| `Price`   | Price of the vehicle     |
| `Engine`  | Engine capacity in cc    |
| `Power`   | Engine power in PS       |
| `Torque`  | Torque in Nm             |
| `Mileage` | Mileage in kmpl          |
| `URL`     | BikeDekho page URL       |

---

## 📈 Example Data

An example scraped record from the project is:

```text
Name       : Royal Enfield Classic 350
Price      : 214270
Engine     : 349 cc
Power      : 20.21 PS
Torque     : 27 Nm
Mileage    : 41.55 kmpl
```

Another example is the Hero Splendor Plus:

```text
Name       : Hero Splendor Plus
Price      : 77777
Engine     : 97.2 cc
Power      : 8.02 PS
Torque     : 8.05 Nm
Mileage    : 70 kmpl
```

---

## 📊 Exploratory Data Analysis

The project analyzes the collected bike specifications to understand patterns and relationships between:

* Price
* Engine capacity
* Power
* Torque
* Mileage

The EDA helps identify differences between commuter bikes, performance-oriented bikes, scooters, and electric vehicles represented in the scraped sample.

---

## 💾 Dataset Export

The raw scraped dataset is saved as:

```python
df.to_csv("bikedekho_raw.csv", index=False)
```

This makes the collected data available for further analysis or machine-learning projects.

---

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/BikeDekho-EDA.git
```

### 2. Navigate to the Project

```bash
cd BikeDekho-EDA
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open

```text
BikeDekho_EDA.ipynb
```

Run the notebook cells sequentially.

---

## 📦 Requirements

Create a `requirements.txt` file containing:

```text
requests
beautifulsoup4
pandas
numpy
matplotlib
seaborn
jupyter
```

Install them using:

```bash
pip install -r requirements.txt
```

---

## ⚠️ Important Notes

* The project depends on the current HTML structure of BikeDekho.
* Website layouts and page content may change, which can affect scraping results.
* Some fields may not be available in a consistent format across different vehicle pages.
* The project intentionally investigates missing values instead of assuming that every specification can be extracted using the same pattern.
* Use web scraping responsibly and respect the website's terms, robots.txt, and applicable laws.

---

## 🔮 Future Improvements

Possible improvements include:

* Scraping a larger number of bike records.
* Extracting manufacturer/brand separately.
* Adding vehicle type such as Bike/Scooter/Electric.
* Extracting top speed and kerb weight.
* Improving extraction for electric vehicles.
* Handling missing values more systematically.
* Adding advanced statistical analysis.
* Building an interactive dashboard using Streamlit.
* Creating a bike price prediction model.
* Building a bike recommendation system.
* Automating periodic data collection.

---

## 👨‍💻 Author

**Sanjay**

This project was developed as a practical project for learning and demonstrating:

* Web Scraping
* Python
* Data Cleaning
* Exploratory Data Analysis
* Data Visualization
* Pandas
* BeautifulSoup

