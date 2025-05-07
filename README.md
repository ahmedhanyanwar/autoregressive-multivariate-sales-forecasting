# Autoregressive Multivariate Time Series Sales Forecasting

A time series forecasting project using autoregressive modeling for multivariate sales data. Predicts future product demand across cities using lag-based features like quantity, price, and discount. Built entirely in a Jupyter Notebook with Python 3.9.

## 📁 Project Structure

```
├── Multivariant_Time_Series_Forecasting.ipynb  # Main Jupyter Notebook with modeling pipeline
├── data/
│   └── product_sales_dataset.csv               # Multivariate time series dataset
├── requirements.txt                            # Python package dependencies
├── LICENSE                                     # License file
└── README.md                                   # Project documentation
```


## 🔍 Project Overview

The project aims to:

* Perform autoregressive forecasting using lag features.
* Model product sales across different cities.
* Evaluate both visually and numerically.

## 📌 Key Features

* Multivariate autoregressive model
* Lag-based features for quantity, price, and discount
* 10-day prediction horizon
* Visual and numerical evaluation (MAE, RMSE, SMAPE)

## 🧪 Notebook Sections Summary

1. **Forecasting Setup**: Define lag structures and autoregressive prediction function.
2. **Single Prediction Example**: Generate and inspect prediction for one city-product pair.
3. **Evaluation - Visualization**: Plot predictions vs actuals for multiple days.
4. **Evaluation - Final 10 Days**: Forecast when target values are not available.
5. **Evaluation - Metrics**: Compute MAE, RMSE, SMAPE across all products and cities.

## 🧹 Data Preprocessing and Feature Engineering

In the data preprocessing stage, several techniques were applied to handle the challenges present in the dataset:

- **Missing Values**: We encountered missing values, particularly in the area columns. These were handled through imputation, but further exploration revealed large gaps in the data.
  
- **Data Gaps**: The data had substantial gaps, especially in terms of days when no sales were recorded. This issue was addressed by setting zeros for missing sales values, allowing us to interpolate gaps based on the missing rate.

- **Outliers**: Outliers in the data were handled using **capping (Winsorization)** to limit extreme values and improve model stability.

- **Time Feature Engineering**: Additional time-based features were created to help capture seasonal trends and other time-related patterns.

## 🧑‍🔬 Modeling and Evaluation

- **Model Selection**: Initially, an LSTM model was tested, but it performed poorly due to the large gaps in the data. Instead, **LightGBM** was used as a more effective model, demonstrating superior performance.

- **Randomized Search**: A **randomized search** was applied to find optimal hyperparameters for LightGBM, improving model performance.

- **Autoregressive Function**: An autoregressive function was developed to forecast sales for the next 10 days using lag-based features for each city-product combination.

- **Model Evaluation**: After training the model, the feature importance was analyzed, and the model's performance was evaluated using metrics like **MAE**, **RMSE**, and **SMAPE**.

## 🛠️ Requirements

Ensure Python 3.9 is installed.

Steps:  

1) Download and install Miniconda from [here](https://www.anaconda.com/docs/main#quick-command-line-install)

2) Create a new enviroment using the following command:
```bash
$ conda create -n timeseries_forecasting python=3.9
```

3) Activate the enviroment:
```bash
$ conda activate mini-rag-app
```

4) Install dependencies:
```bash
pip install -r requirements.txt
```

## 🚀 How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/autoregressive-multivariate-sales-forecasting.git
   cd autoregressive-multivariate-sales-forecasting
   ```
2. Install required packages:

   ```bash
   pip install -r requirements.txt
   ```
3. Open the notebook:

   ```bash
   jupyter notebook Multivariant_Time_Series_Forecasting.ipynb
   ```

## 📊 Dataset

The dataset `product_sales_dataset.csv` contains daily sales records for multiple products across different cities. It includes:

* `time_step`: Date of the sales record
* `city`: City name
* `product_name`: Product name
* `quantity`, `price`, `discount`: Feature variables

## 📜 License

This project is licensed under the MIT License.

---

Feel free to contribute, fork, or use it as a template for your own time series forecasting projects!
