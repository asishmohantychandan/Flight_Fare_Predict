# ✈️ Flight Price Prediction

An end-to-end machine learning regression project that predicts **flight ticket prices** using flight details such as airline, route, source, destination, duration, number of stops, departure time, and journey date.

The project focuses on building a practical regression pipeline covering **data cleaning, exploratory data analysis, feature engineering, model comparison, cross-validation, hyperparameter tuning, and model serialization**.

---

## 📌 Project Overview

Flight ticket prices vary significantly depending on factors such as:

* Airline
* Source and destination
* Number of stops
* Flight duration
* Departure time
* Journey date
* Route
* Additional flight information

The objective of this project is to learn the relationship between these features and ticket prices and build a machine learning model capable of predicting the expected fare.

### Problem Type

**Supervised Machine Learning — Regression**

### Target Variable

`Price`

The model predicts the estimated flight ticket price in Indian Rupees (₹).

---

## 🎯 Business Objective

A flight price prediction system can help travelers and travel platforms estimate expected ticket prices based on available flight information.

From a data science perspective, the project demonstrates how raw, semi-structured flight data can be transformed into machine-learning-ready features and used to build and optimize regression models.

---

## 📊 Dataset

The project uses the **Flight Fare dataset** loaded from:

```text
Flight_Fare.xlsx
```

The final modeling dataset contains:

* **10,681 observations**
* **43 input features** after feature engineering and encoding
* **1 target variable — Price**

The data contains flight information including:

| Feature           | Description                   |
| ----------------- | ----------------------------- |
| `Airline`         | Airline operating the flight  |
| `Date_of_Journey` | Date of the journey           |
| `Source`          | Departure city                |
| `Destination`     | Arrival city                  |
| `Route`           | Complete flight route         |
| `Dep_Time`        | Departure time                |
| `Arrival_Time`    | Arrival time                  |
| `Duration`        | Flight duration               |
| `Total_Stops`     | Number of stops               |
| `Additional_Info` | Additional flight information |
| `Price`           | Target flight fare            |

---

## 🔍 Exploratory Data Analysis

The notebook performs exploratory analysis to understand:

* Target price distribution
* Price outliers
* Airline distribution
* Average price by airline
* Source and destination patterns
* Relationship between number of stops and price
* Flight duration
* Departure and arrival time patterns
* Journey date characteristics
* Categorical feature distributions

### Target Distribution

The ticket price distribution is **right-skewed**, with most observations concentrated in lower and middle price ranges and a smaller number of higher-priced flights.

The analysis also uses boxplots to identify potential price outliers.

---

# 🧹 Data Cleaning & Feature Engineering

A significant part of the project involved transforming the raw flight data into usable machine-learning features.

### Missing Values

The dataset contained a very small number of missing observations in `Route` and `Total_Stops`.

Because the number of affected records was extremely small, those rows were removed.

---

### Duration Transformation

The original `Duration` column contained values such as:

```text
2h 50m
7h 25m
45m
7h
```

A custom parsing function was created to convert the duration into **total minutes**.

For example:

```text
2h 50m → 170 minutes
7h 25m → 445 minutes
45m    → 45 minutes
7h     → 420 minutes
```

An invalid duration record was also identified and removed during data-quality analysis.

---

### Departure & Arrival Time

Time information was transformed into numerical components.

Departure time was converted into:

* Departure hour
* Departure minute

Messy arrival-time values containing additional next-day date information were cleaned before processing.

---

### Journey Date

`Date_of_Journey` was converted into datetime format.

The following features were extracted:

* Day
* Month
* Weekday

The year was not retained because the observations belonged to the same year.

---

### Number of Stops

The `Total_Stops` feature contains naturally ordered categories:

```text
non-stop
1 stop
2 stops
3 stops
4 stops
```

These were converted into ordinal numerical values:

```text
non-stop → 0
```
