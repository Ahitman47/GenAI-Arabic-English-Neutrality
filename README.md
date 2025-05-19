# GenAI-Arabic-English-Neutrality

This repository contains the code and Jupyter notebooks used for my thesis, which investigates:

- Trending topic identification from news headlines
- Automated sentiment analysis on ChatGPT o1 output regarding questions on the identified topics (AWS Comprehend)
- Human survey ratings
- Comparative evaluation of automated vs. human judgments

---

## 📂 Repository Structure

```
.
├── ComprehendDataAnalysis.ipynb      # Exploratory analysis & preprocessing of AWS Comprehend outputs
├── ComprehendSentimentAnalysis.ipynb # Full sentiment-analysis pipeline using AWS Comprehend
├── SurveyDataAnalysis.ipynb          # Cleaning & descriptive statistics on survey responses
├── SurveyVsComprehend.ipynb          # Comparative analyses: survey ratings vs. Comprehend scores
├── TrendingTopics.ipynb              # Fetching headlines & identifying top sensitive topics
├── data/                             # Place raw data files here (see “Data” below)
├── requirements.txt                  # Python dependencies
└── README.md                         # This file
```

---

## 🚀 Installation & Setup

### Clone the repository

```bash
git clone https://github.com/your-username/your-thesis-repo.git
cd your-thesis-repo
```

### Create a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate     # macOS/Linux
venv\Scripts\activate.bat    # Windows
```

### Install dependencies

```bash
pip install -r requirements.txt
```

> Key libraries: `pandas`, `numpy`, `matplotlib`, `scipy`, `boto3`, `scikit-posthocs`, `pingouin`, `requests`, `groq`

---

## 📁 Data

The `data/` directory contains the data used for this research. The notebooks expect:

- **Survey export** (semicolon-delimited CSV)  
  e.g. `data/Survey Results.csv`

- **AWS Comprehend outputs** (Excel or CSV)  
  e.g. `data/sentiment_analysis_full_results raw.xlsx`

- **Fetched article titles** (CSV)  
  e.g. `data/article_titles.csv`

> Adjust the file paths at the top of each notebook if you choose different locations.

---

## 📓 Notebooks Overview

### 1. `TrendingTopics.ipynb`
Fetches news headlines via API, batches titles to an LLM for sensitive-topic extraction, and summarizes the top sensitive topics across all collected headlines.

### 2. `ComprehendDataAnalysis.ipynb`
Loads and preprocesses raw AWS Comprehend sentiment scores, computes sentiment-difference metrics, and generates basic descriptive statistics.

### 3. `ComprehendSentimentAnalysis.ipynb`
Uses AWS Comprehend API to fetch sentiment scores for each model and question, computes inter-language distances, and saves full results for downstream analysis.

### 4. `SurveyDataAnalysis.ipynb`
Reads and reshapes raw Qualtrics survey data, filters for valid responses, computes descriptive statistics, and visualizes human ratings across metrics.

### 5. `SurveyVsComprehend.ipynb`
Merges survey ratings with automated Comprehend scores, performs group comparisons (t-tests, ANOVA, nonparametric tests), computes correlation matrices, and calculates Rank-Biased Overlap.


---

## ▶️ Running the Notebooks

To launch Jupyter:

```bash
jupyter notebook
```

Open each `.ipynb` in order, or jump to the analysis you need.

> Ensure that API keys (AWS, Perigon, Groq) are set in environment variables or in the notebook’s configuration cell.
