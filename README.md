# Flight Fare Prediction

A Flask-based machine learning web application that predicts flight ticket fares based on journey details such as airline, source, destination, departure time, arrival time, duration, and number of stops.

This project uses a trained **Random Forest Regression** model to estimate flight fares from historical flight price data.

---

## Live Demo

Deployment Link:

```text
https://flightfare-owx1.onrender.com/
```

> Note: Replace the above URL with your actual Render deployment link after deployment.

---

## Demo Screenshots

### Home Page

![Home Page](assets/demo1.png)

### Prediction Result

![Prediction Result](assets/demo2.png)

---

## Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Proposed Solution](#proposed-solution)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Main Files Explanation](#main-files-explanation)
- [How to Run Locally](#how-to-run-locally)
- [Requirements](#requirements)
- [Deployment](#deployment)
- [Deploying on Render](#deploying-on-render)
- [Model Information](#model-information)
- [Input Features](#input-features)
- [Output](#output)
- [Limitations](#limitations)
- [Future Enhancements](#future-enhancements)
- [Common Errors and Fixes](#common-errors-and-fixes)
- [Authors](#authors)
- [Acknowledgement](#acknowledgement)
- [License](#license)

---

## Project Overview

Flight ticket prices change frequently depending on several factors such as airline, journey date, route, departure time, arrival time, duration, and number of stops. Many travelers find it difficult to estimate the right fare before booking tickets.

The **Flight Fare Prediction** system is designed to help users estimate flight ticket prices using machine learning. The application takes journey-related inputs from the user and predicts the approximate fare using a trained **Random Forest Regression** model.

---

## Problem Statement

Flight prices are dynamic and may vary based on route, airline, demand, timing, number of stops, and booking period. Inexperienced travelers may find it difficult to understand whether the displayed fare is reasonable or expensive.

This project aims to provide a simple web-based fare prediction system that helps users estimate flight prices before booking.

---

## Proposed Solution

The proposed system uses a machine learning regression model to predict flight ticket prices based on user input. The model is trained using historical flight fare data and learns the relationship between travel-related features and ticket prices.

The user enters flight details through a web interface. The Flask backend processes the input, loads the trained model, and returns the predicted fare.

---

## Features

- Predicts flight fare based on user input
- Uses a trained Random Forest Regression model
- Flask-based backend application
- HTML, CSS, Bootstrap-based frontend
- Simple and user-friendly interface
- Instant prediction output
- Supports journey details such as:
  - Airline
  - Source
  - Destination
  - Journey date
  - Departure time
  - Arrival time
  - Number of stops

---

## Tech Stack

### Frontend

- HTML
- CSS
- Bootstrap
- JavaScript

### Backend

- Python
- Flask
- Flask-CORS

### Machine Learning

- Pandas
- NumPy
- Scikit-learn
- Random Forest Regression
- Pickle

### Deployment

- GitHub for source code hosting
- Render for Flask application hosting

---

## Project Structure

```text
FLIGHT-FARE-PREDICTION/
│
├── assets/
│   ├── demo1.png
│   └── demo2.png
│
├── static/
│   └── css/
│       └── styles.css
│
├── templates/
│   ├── home.html
│   └── login.html
│
├── app.py
├── flight_rf.pkl
├── Data_Train.xlsx
├── Test_set.xlsx
├── requirements.txt
├── Procfile
├── runtime.txt
├── .python-version
├── README.md
└── .gitignore
```

---

## Main Files Explanation

### `app.py`

The main Flask application file. It starts the server, handles routes, processes form input, loads the trained machine learning model, and returns the predicted flight fare.

### `flight_rf.pkl`

The trained machine learning model file. This file is loaded by the Flask application to perform prediction.

### `templates/`

Contains HTML pages rendered by Flask.

```text
templates/
├── home.html
└── login.html
```

### `static/`

Contains static frontend files such as CSS, images, and JavaScript.

### `assets/`

Contains README/demo screenshots.

```text
assets/
├── demo1.png
└── demo2.png
```

### `requirements.txt`

Contains the Python dependencies required to run the project.

### `Procfile`

Used by Render to start the Flask application using Gunicorn.

### `runtime.txt`

Specifies the Python runtime version for deployment.

### `.python-version`

Specifies the Python version for Render and other deployment platforms.

### `.gitignore`

Prevents unnecessary files like virtual environments and cache files from being pushed to GitHub.

---

## How to Run Locally

Follow these steps to run the project on your local system.

### 1. Clone the repository

```bash
git clone https://github.com/maheshchilukamari/flightfare.git
cd flightfare
```

### 2. Create a virtual environment

For Windows:

```bash
py -3.10 -m venv venv
```

### 3. Activate the virtual environment

```bash
venv\Scripts\activate
```

After activation, your terminal should look like this:

```bash
(venv) C:\Users\YourName\Desktop\Flight-Fare-Prediction>
```

### 4. Install required packages

```bash
python -m pip install --upgrade pip setuptools wheel
python -m pip install -r requirements.txt
```

### 5. Run the Flask application

```bash
python app.py
```

### 6. Open the application in your browser

```text
http://127.0.0.1:5000
```

---

## Requirements

Recommended Python version:

```text
Python 3.10.13
```

Required packages:

```txt
setuptools==68.2.2
wheel==0.41.2
Flask==2.2.5
Flask-Cors==3.0.10
gunicorn==20.1.0
joblib==1.2.0
numpy==1.23.5
scipy==1.9.3
pandas==1.5.3
scikit-learn==1.1.1
```

---

## Deployment

This project cannot run directly on **GitHub Pages** because GitHub Pages supports static websites such as HTML, CSS, and JavaScript.

This project uses:

```text
Python
Flask
Scikit-learn
Pickle model file
```

So it needs a backend server.

Recommended deployment platform:

```text
Render
```

GitHub is used to store the code. Render is used to run the Flask application online.

---

## Deploying on Render

### 1. Push the project to GitHub

```bash
git init
git add .
git commit -m "Initial commit - Flight fare prediction Flask app"
git branch -M main
git remote add origin https://github.com/maheshchilukamari/flightfare.git
git push -u origin main
```

If the remote already exists:

```bash
git remote set-url origin https://github.com/maheshchilukamari/flightfare.git
git push -u origin main
```

---

### 2. Create a New Web Service on Render

Go to Render and select:

```text
New + → Web Service
```

Connect your GitHub repository:

```text
maheshchilukamari/flightfare
```

---

### 3. Render Settings

Use the following settings:

```text
Name:
flightfare
```

```text
Environment:
Python
```

```text
Branch:
main
```

```text
Root Directory:
Leave empty
```

```text
Build Command:
python -m pip install --upgrade pip setuptools wheel && pip install -r requirements.txt
```

```text
Start Command:
gunicorn app:app
```

---

### 4. Set Python Version on Render

Add this environment variable in Render:

```text
Key:
PYTHON_VERSION
```

```text
Value:
3.10.13
```

Also keep a `.python-version` file in the project root with:

```text
3.10.13
```

Keep `runtime.txt` as:

```text
python-3.10.13
```

---

### 5. Deploy

After updating the settings, click:

```text
Manual Deploy → Clear build cache & deploy
```

After successful deployment, Render will provide a live URL similar to:

```text
https://flightfare.onrender.com
```

---

## Model Information

The prediction model used in this project is a **Random Forest Regression** model.

Random Forest Regression is an ensemble learning algorithm that uses multiple decision trees to improve prediction performance. In this project, the model predicts flight fares based on journey-related features such as airline, source, destination, departure time, arrival time, duration, and stops.

The trained model is saved as:

```text
flight_rf.pkl
```

This file is loaded inside the Flask application using Python pickle.

---

## Input Features

The model considers several features for fare prediction, including:

- Airline
- Source
- Destination
- Date of journey
- Departure time
- Arrival time
- Total stops
- Journey day
- Journey month
- Route-related information

---

## Output

The application returns the estimated flight fare.

Example:

```text
Predicted Flight Fare: ₹ 7,850
```

---

## Limitations

- The prediction depends on the quality and age of the dataset.
- The model does not fetch live airline prices.
- Actual ticket prices may vary due to demand, holidays, airline offers, fuel prices, and last-minute booking changes.
- The model was trained on historical data, so newer market trends may not be reflected.
- Incorrect or incomplete input data can result in inaccurate predictions.
- The current system does not include database storage for previous predictions.

---

## Future Enhancements

- Add live flight price API integration
- Retrain the model using updated datasets
- Add database support for storing search history
- Improve user interface and responsiveness
- Add user authentication
- Add prediction history dashboard
- Add more airlines, routes, and cities
- Deploy with CI/CD automation
- Add cloud database support
- Improve model accuracy with advanced algorithms

---

## Common Errors and Fixes

### 1. `ModuleNotFoundError: No module named flask`

Install Flask:

```bash
python -m pip install flask
```

---

### 2. `ModuleNotFoundError: No module named flask_cors`

Install Flask-CORS:

```bash
python -m pip install flask-cors
```

---

### 3. Scikit-learn Pickle Version Error

If you see an error related to `flight_rf.pkl`, `pickle`, or scikit-learn version mismatch, install the compatible scikit-learn version:

```bash
python -m pip install scikit-learn==1.1.1
```

Use Python 3.10 for best compatibility.

---

### 4. `TemplateNotFound: home.html`

Make sure `home.html` is inside the `templates` folder:

```text
templates/home.html
```

---

### 5. Render Using Wrong Python Version

If Render uses Python 3.13 or 3.14, the deployment may fail due to old scikit-learn compatibility.

Set this Render environment variable:

```text
PYTHON_VERSION = 3.10.13
```

Also add this file:

```text
.python-version
```

Inside `.python-version`, write:

```text
3.10.13
```

---

### 6. Git Push Rejected

If Git says:

```text
Updates were rejected because the remote contains work that you do not have locally
```

Run:

```bash
git pull --rebase origin main
git push origin main
```

---

## Git Ignore

The `.gitignore` file should include:

```gitignore
venv/
__pycache__/
*.pyc
.ipynb_checkpoints/
.env
```

Do not push the `venv` folder to GitHub.

---

## Authors

- CH Mahesh
- Priyanka Kumari
- V Akshay Reddy

---

## Acknowledgement

This project was developed as a mini project under the Department of Information Technology. The system focuses on predicting flight fares using machine learning and helping users estimate flight ticket prices based on journey details.

---

## License

This project is created for academic and learning purposes.

---

## Repository

```text
GitHub Repository:
https://github.com/maheshchilukamari/flightfare
```

---

## Project Status

```text
Status: Completed / Deployment in Progress
```
