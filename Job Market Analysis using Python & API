import requests
import pandas as pd
from pandas import json_normalize
import matplotlib.pyplot as plt
import re
import time

# 🔑 API credentials
APP_ID = "3e80aba1"
API_KEY = "2a712dbe2c50312eb5128c3bec054dbd"

BASE_URL = "https://api.adzuna.com/v1/api/jobs/nl/search/{}"

PARAMS = {
    "app_id": APP_ID,
    "app_key": API_KEY,
    "what": "data analyst",
    "results_per_page": 50,
    "max_days_old": 21
}

# 🎯 Skills
SKILLS = ["python", "sql", "excel"]

# -------------------------------
# 📥 FETCH DATA
# -------------------------------
def fetch_jobs(max_pages=10):
    all_jobs = []

    for page in range(1, max_pages + 1):
        url = BASE_URL.format(page)
        print(f"Fetching page {page}...")

        try:
            response = requests.get(url, params=PARAMS, timeout=10)

            if response.status_code != 200:
                print(f"Error {response.status_code}")
                continue

            data = response.json()
            jobs = data.get("results", [])

            if not jobs:
                print("No more data.")
                break

            all_jobs.extend(jobs)
            time.sleep(1)  # avoid rate limits

        except requests.exceptions.RequestException as e:
            print("Request failed:", e)
            break

    return all_jobs


# -------------------------------
# 🧹 CLEAN DATA
# -------------------------------
def clean_data(jobs):
    df = json_normalize(jobs)

    df = df[[
        "title",
        "company.display_name",
        "location.display_name",
        "salary_min",
        "salary_max",
        "created",
        "redirect_url",
        "description"
    ]]

    df.columns = [
        "title", "company", "location",
        "salary_min", "salary_max",
        "created", "url", "description"
    ]

    # Fill missing
    df["description"] = df["description"].fillna("").str.lower()
    df["company"] = df["company"].fillna("Unknown")
    df["location"] = df["location"].fillna("Unknown")

    # Remove duplicates
    df = df.drop_duplicates()

    return df


# -------------------------------
# 🔍 SKILL EXTRACTION
# -------------------------------
def extract_skills(df):
    for skill in SKILLS:
        df[skill] = df["description"].str.contains(
            rf"\b{skill}\b", regex=True
        ).astype(int)

    return df


# -------------------------------
# 📊 VISUALIZATION
# -------------------------------
def plot_skills(df):
    skill_counts = df[SKILLS].sum().sort_values(ascending=False)

    print("\nSkill demand:\n", skill_counts)

    skill_counts.plot(kind="bar")
    plt.title("Most In-Demand Skills for Data Analysts")
    plt.xlabel("Skill")
    plt.ylabel("Number of Job Listings")
    plt.tight_layout()
    plt.show()


# -------------------------------
# 🚀 MAIN PIPELINE
# -------------------------------
def main():
    jobs = fetch_jobs(max_pages=10)

    print("Total jobs collected:", len(jobs))

    df = clean_data(jobs)
    df = extract_skills(df)

    plot_skills(df)

    df.to_csv("jobs.csv", index=False)

    print("\nSample data:")
    print(df.head())
    print("\nDataset shape:", df.shape)


if __name__ == "__main__":
    main()
