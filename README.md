# 🚗 Machine Learning Car Recommendation System

A **Machine Learning-based Car Recommendation System** that predicts the estimated ex-showroom price of a car based on user-provided specifications and recommends cars from the dataset with prices closest to the predicted value.

The project uses **Linear Regression** for price prediction and **Streamlit** to provide an interactive web-based interface.

---

## 📌 Project Overview

Choosing a car involves comparing several specifications such as mileage, horsepower, torque, and price. This project uses machine learning to estimate the expected price of a car based on its technical specifications.

The system:

1. Loads and preprocesses car dataset information.
2. Extracts useful numerical features from the raw data.
3. Trains a Linear Regression model.
4. Predicts the estimated ex-showroom price based on user specifications.
5. Searches the original dataset for cars with prices closest to the predicted price.
6. Displays the **Top 5 recommended cars** through a Streamlit application.

---

## 🎯 Objectives

* Predict car prices using machine learning.
* Use important car specifications as prediction features.
* Provide personalized car recommendations.
* Build an interactive and easy-to-use web application.
* Demonstrate the practical use of Linear Regression in a recommendation system.

---

## 🧠 Machine Learning Model

### Linear Regression

The project uses **Linear Regression** to predict the car's ex-showroom price.

### Input Features

The model uses three main features:

| Feature                  | Description                    |
| ------------------------ | ------------------------------ |
| `ARAI_Certified_Mileage` | Certified mileage of the car   |
| `Power_HP`               | Engine power in horsepower     |
| `Torque_Nm`              | Engine torque in Newton-metres |

### Target Variable

`Ex-Showroom_Price_in_Lakhs`

The original price is converted from the dataset's rupee format into lakhs for model training.

---

## 🔄 Project Workflow

```text
Car Dataset
     ↓
Data Cleaning
     ↓
Feature Extraction
     ↓
Missing Value Handling
     ↓
Select Features
     ↓
Train-Test Split
     ↓
Linear Regression
     ↓
Price Prediction
     ↓
Compare Predicted Price with Dataset
     ↓
Top 5 Car Recommendations
     ↓
Streamlit Web Application
```

---

## 🧹 Data Preprocessing

The project performs several preprocessing operations before training the model.

### 1. Remove unnecessary columns

The `Unnamed: 0` column is removed from the dataset.

### 2. Convert price

The `Ex-Showroom_Price` field is converted into a numerical value and represented in lakhs.

For example:

```text
Rs. 21,03,000
        ↓
21.03 Lakhs
```

### 3. Extract mileage

Mileage values such as:

```text
20 kmpl
18 km/kg
15 km/litre
```

are converted into numerical values.

### 4. Extract horsepower

Horsepower values are extracted from the `Power` column and stored in:

```text
Power_HP
```

### 5. Extract torque

Torque values are extracted from the `Torque` column and stored in:

```text
Torque_Nm
```

### 6. Handle missing values

Missing numerical values are replaced using the **median** of the corresponding column.

---

## 📊 Dataset

The project uses a car dataset containing information such as:

* Make
* Model
* Variant
* Ex-Showroom Price
* Mileage
* Power
* Torque
* and other car specifications

The dataset is loaded from Google Drive in the provided implementation.

> **Note:** The dataset is not included in this repository if it contains external or separately obtained data. Place the CSV file in the expected location before running the application.

---

## 🏗️ Model Training

The dataset is divided into training and testing sets:

```python
train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

This means:

* **80%** of the data → Training
* **20%** of the data → Testing

The Linear Regression model is then trained using the training data.

---

## 📈 Model Evaluation

The project calculates the **R² score** to evaluate the regression model.

R² indicates how well the model explains the variation in car prices.

The Streamlit application displays the R² score in the sidebar.

> Note: R² is a regression evaluation metric and should not be interpreted as classification accuracy.

---

## ⭐ Recommendation System

After predicting the price, the system calculates the difference between the predicted price and the actual prices of cars in the dataset.

The absolute price difference is calculated as:

```python
price_difference = abs(actual_price - predicted_price)
```

Cars are then sorted according to this difference.

The **5 cars with the smallest price difference** are displayed as recommendations.

---

## 🖥️ Streamlit Application

The project includes an interactive Streamlit interface.

Users can adjust:

* **Certified Mileage**
* **Horsepower**
* **Torque**

using sliders.

The application then displays:

### Predicted Price

The estimated ex-showroom price for the selected specifications.

### Top 5 Recommended Cars

The application displays information such as:

* Make
* Model
* Variant
* Actual Ex-Showroom Price
* Mileage
* Power
* Price Deviation

---

## 📁 Project Structure

```text
Car-Recommendation-System/
│
├── car_recommender_app.py
├── cars_ds_final.csv
├── Machine_Learning_Model_2.ipynb
├── README.md
└── requirements.txt
```

> File names and dataset locations can be changed according to your local setup.

---

## ⚙️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Streamlit**
* **Google Colab / Jupyter Notebook**

---

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/your-username/car-recommendation-system.git
```

Move into the project directory:

```bash
cd car-recommendation-system
```

Install the required libraries:

```bash
pip install pandas numpy scikit-learn streamlit
```

---

## ▶️ Running the Application

Run the Streamlit application using:

```bash
streamlit run car_recommender_app.py
```

After starting the application, open the Streamlit URL displayed in the terminal.

---

## 💻 Running the Notebook

The machine learning model can also be executed using the Jupyter Notebook:

```text
Machine_Learning_Model_2.ipynb
```

The notebook performs:

```text
Data Loading
    ↓
Data Cleaning
    ↓
Feature Engineering
    ↓
Train-Test Split
    ↓
Linear Regression
    ↓
Price Prediction
    ↓
Car Recommendation
```

---

## 🧪 Example

For example, a user may enter:

```text
Mileage    : 20 kmpl
Horsepower : 120 HP
Torque     : 200 Nm
```

The model produces an estimated price and finds cars in the dataset whose actual prices are closest to that prediction.

An example run from the project produced a predicted price of approximately:

```text
₹21,03,656
```

The recommendation output included vehicles such as Toyota Innova Crysta, MG ZS EV, and Honda Civic based on their price difference from the predicted value.

---

## 📊 Sample Recommendation Output

| Make   | Model         | Variant                    | Actual Price |
| ------ | ------------- | -------------------------- | -----------: |
| Toyota | Innova Crysta | 2.7 Zx At 7 Str            |   ₹21,03,000 |
| Toyota | Innova Crysta | Touring Sport 2.4 Vx 7 Str |   ₹20,97,000 |
| Toyota | Innova Crysta | 2.4 Zx 7 Str               |   ₹21,13,000 |
| MG     | ZS EV         | Excite                     |   ₹20,88,000 |
| Honda  | Civic         | 1.8 Zx Cvt                 |   ₹21,24,900 |

These recommendations are selected according to their proximity to the predicted price rather than a general ranking of vehicle quality.

---

## 🔮 Future Scope

The project can be further improved by:

### 1. Advanced Machine Learning Models

Experiment with models such as:

* Random Forest Regressor
* Gradient Boosting
* XGBoost
* Random Forest
* Support Vector Regression

### 2. More Features

Additional features could be incorporated, such as:

* Fuel Type
* Body Type
* Engine Displacement
* Number of Seats
* Transmission
* Brand
* Vehicle Age

### 3. Categorical Feature Encoding

Categorical features can be incorporated using techniques such as:

```text
One-Hot Encoding
```

### 4. Improved Recommendation System

Instead of recommending cars based primarily on price difference, the system could consider multiple user preferences simultaneously.

For example:

```text
Price
Mileage
Horsepower
Torque
Fuel Type
Body Type
Transmission
```

### 5. Interactive Visualizations

Future versions can include interactive charts showing:

* Price comparison
* Mileage comparison
* Horsepower comparison
* Recommended vs predicted price
* Feature relationships

---

## ⚠️ Limitations

* The model uses only three main numerical features for price prediction.
* Car prices can depend on many factors that are not included in the current model.
* The recommendations are based primarily on closeness to the predicted price.
* Dataset quality and completeness can affect prediction performance.
* The predicted price should be treated as an estimate rather than an actual market quotation.

---

## 📜 License

This project is intended for **educational and academic purposes**.

If you are using a third-party dataset, check and comply with the dataset's original license and usage conditions.

---

## 🙌 Acknowledgements

* Python
* Pandas
* NumPy
* Scikit-learn
* Streamlit
* Dataset contributors

---

## ⭐ If You Like This Project

If you find this project useful, consider giving the repository a ⭐ on GitHub.
