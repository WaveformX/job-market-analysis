# Data Analyst Job Market Analyzer

A Python project that collects Data Analyst job listings from the Adzuna Jobs API, cleans the data, extracts important skills, and visualizes hiring trends across companies.

---

## Features

- Fetches live Data Analyst job postings
- Cleans and structures job market data
- Extracts in-demand skills from job descriptions
- Visualizes:
  - Companies hiring the most Data Analysts
  - Skill demand trends
- Exports cleaned dataset to CSV

---

## Technologies Used

- Python
- Pandas
- Requests
- Matplotlib
- Adzuna Jobs API

---

## Project Structure

```bash
project/
│
├── jobs.py          # Main Python script
├── jobs.csv         # Exported dataset
├── README.md
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/data-analyst-job-analyzer.git
cd data-analyst-job-analyzer
```

Install dependencies:

```bash
pip install pandas matplotlib requests
```

---

## API Setup

Create a free account at Adzuna:

- https://developer.adzuna.com/

Replace the API credentials in the script:

```python
APP_ID = "your_app_id"
API_KEY = "your_api_key"
```

---

## How It Works

### 1. Fetch Job Listings

The script connects to the Adzuna API and downloads Data Analyst jobs from the Netherlands market.

### 2. Clean the Dataset

The following fields are extracted:

- Job title
- Company
- Location
- Salary range
- Description
- Posting date
- Job URL

### 3. Extract Skills

The script scans job descriptions for skills such as:

- Python
- SQL
- Excel

### 4. Visualize Hiring Trends

A bar chart displays which companies currently have the most open Data Analyst positions.

---

## Run the Project

```bash
python jobs.py
```

---

## Example Output

```bash
Open Data Analyst Positions by Company:

Booking.com      14
ING              10
Rabobank          8
ASML              7
```

The script also generates a visualization using Matplotlib.



## License

This project is open-source and available under the MIT License.
