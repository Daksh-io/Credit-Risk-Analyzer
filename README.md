# 💳 Credit Risk Analyzer

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-0.141.1-green)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

A smart credit-risk prediction project that evaluates loan applicants using machine learning and a FastAPI backend. It analyzes applicant data like income, age, employment history, loan amount, and previous defaults to classify whether a loan is low-risk or high-risk.

> This project combines data analysis, model training, and a user-friendly prediction interface.

---

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Dataset](#dataset)
- [Model](#model)
- [Requirements](#requirements)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

The Credit Risk Analyzer is designed to support financial decision-making by predicting whether a borrower is likely to default on a loan.

It includes:
- A Jupyter notebook for exploratory data analysis (EDA)
- A machine learning model trained on credit data
- A FastAPI app to serve real-time predictions
- A static frontend interface for user interaction

This makes the project suitable for both learning and practical deployment.

---

## Features

- 🔍 Credit risk assessment using applicant details
- 📊 Exploratory data analysis and visualization
- 🤖 Machine learning-based default prediction
- 🌐 FastAPI REST API for real-time scoring
- 🧠 Probability output and risk classification
- 📁 Model persistence using joblib
- 🖥️ Simple static web interface
- 📈 Threshold-based decision logic for final risk label

---

## Project Structure

```text
Credit-Risk-Analyzer/
├── .gitignore
├── .ipynb_checkpoints/
├── __pycache__/
├── static/
│   ├── index.html
│   ├── script.js
│   └── styles.css
├── Credit_Risk.ipynb
├── README.md
├── best_threshold.pkl
├── credit_risk_dataset.csv
├── credit_risk_model.pkl
├── main.py
├── requirements.txt
└── .gitattributes
```

---

## Installation

### Prerequisites
- Python 3.8+
- pip
- virtual environment (recommended)

### Setup

1. Clone the repository
```bash
git clone https://github.com/Daksh-io/Credit-Risk-Analyzer.git
cd Credit-Risk-Analyzer
```

2. Create and activate a virtual environment
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

---

## Quick Start

### Run the API
```bash
uvicorn main:app --reload
```

Then open:
- API docs: http://localhost:8000/docs
- Web app: http://localhost:8000/

### Open the notebook
```bash
jupyter notebook
```

Open `Credit_Risk.ipynb` to inspect the analysis and model-building workflow.

---

## Usage

### Web Interface
1. Start the server
2. Open the local app in the browser
3. Enter applicant information
4. Click Predict
5. View the risk prediction and default probability

### API Example
```bash
curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{
    "person_age": 25,
    "person_income": 50000,
    "person_home_ownership": "RENT",
    "person_emp_length": 3.0,
    "loan_intent": "PERSONAL",
    "loan_grade": "C",
    "loan_amnt": 10000,
    "loan_int_rate": 12.5,
    "loan_percent_income": 0.20,
    "cb_person_default_on_file": "N",
    "cb_person_cred_hist_length": 4
  }'
```

Example response:
```json
{
  "default_probability": 0.2874,
  "default_prediction": 0,
  "threshold": 0.45,
  "Result": "Low Risk"
}
```

---

## API Endpoints

### POST /predict
This endpoint accepts loan application data and returns:
- `default_probability`
- `default_prediction`
- `threshold`
- `Result`

Request body fields include:
- `person_age`
- `person_income`
- `person_home_ownership`
- `person_emp_length`
- `loan_intent`
- `loan_grade`
- `loan_amnt`
- `loan_int_rate`
- `loan_percent_income`
- `cb_person_default_on_file`
- `cb_person_cred_hist_length`

---

## Dataset

The project uses `credit_risk_dataset.csv` which contains loan application records with features such as:
- applicant age
- income
- home ownership
- employment length
- loan amount and intent
- loan grade
- interest rate
- default history
- credit history length
- loan status target variable

The dataset is used to train a machine learning classifier that predicts whether a borrower is likely to default.

---

## Model

The project loads a pre-trained model and threshold from:
- `credit_risk_model.pkl`
- `best_threshold.pkl`

The prediction logic is implemented in `main.py`:

```python
probability = ml_model['model'].predict_proba(input_df)[:, 1][0]
prediction = int(probability >= ml_model["threshold"])
```

This means:
- if probability >= threshold → high risk
- else → low risk

---

## Requirements

```text
annotated-types==0.8.0
anyio==4.15.1
click==8.5.0
cloudpickle==3.1.2
fastapi==0.141.1
h11==0.16.0
idna==3.20
joblib==1.6.0
numpy==2.5.3
pandas==3.0.6
pydantic==2.13.5
pydantic-core==2.46.5
python-dateutil==2.9.0.post0
scikit-learn==1.9.1
scipy==1.18.1
six==1.17.0
starlette==1.7.0
threadpoolctl==3.7.0
typing-extensions==4.16.0
typing-inspection==0.4.4
uvicorn==0.54.0
xgboost==3.4.1
```

To install:
```bash
pip install -r requirements.txt
```

---

## Contributing

Contributions are welcome.

1. Fork the project
2. Create a feature branch
3. Make your changes
4. Commit and push
5. Open a pull request

Example:
```bash
git checkout -b feature/my-improvement
git add .
git commit -m "Add my improvement"
git push origin feature/my-improvement
```

---

## License

This project is licensed under the MIT License.

---

## Contact

- GitHub: https://github.com/Daksh-io/Credit-Risk-Analyzer
- Author: Daksh-io

If you want, I can also generate:
- a more modern GitHub-style README with badges and screenshots,
- a landing-page style README,
- or a shorter professional version for the repo home page.

---

<div align="center">

Made with ❤️ by Daksh-io

</div>
