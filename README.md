# California House Price Prediction

Predicting the price of houses in an area of California from information about the area.

## About this project

This project predicts the price of houses in an area in California, using information such as income, location, house age and population. The model relies most on income and location.

I used a California housing dataset with about 17,000 areas, and I built it in Python using pandas and scikit-learn.

> The data file is not included in this repository. It is the `california_housing_train.csv` file in the `sample_data` folder that every Google Colab session provides.

## What I did

1. **Loaded and explored the data:** 17,000 rows, 8 clue columns and the price column (`median_house_value`). There were no missing values and every column was already numeric, so no encoding was needed.
2. **Split the data** into 80% for training and 20% for testing.
3. **Trained a baseline model** (Linear Regression) and a **Random Forest**.
4. **Measured the errors** with the average error (how many dollars the guesses are off) and R2 (how much better the model is than always guessing the average price).
5. **Checked which clues matter most** using the Random Forest's feature importance.

## Results

I compared two models. Linear Regression was off by about 50,000 on average, and the Random Forest was off by about 32,000. The Random Forest was better, with an R2 of 0.82 against 0.66 for Linear Regression.

| Model | Average error | R2 |
|---|---|---|
| Linear Regression | about 49,983 | 0.66 |
| Random Forest | about 32,360 | **0.82** |

Unlike in my churn project, where the simple model won, the more complex model won here. House prices depend on location in a way that is not a straight line, and trees can learn that. The lesson is to compare against a simple baseline and let the numbers decide.

## Which clues matter most

| Clue | Importance |
|---|---|
| median_income | 0.52 |
| longitude | 0.17 |
| latitude | 0.16 |
| housing_median_age | 0.06 |
| the other four clues | 0.02 to 0.03 each |

The model relies mostly on income and location. This shows what the model used, not what causes high prices.

## Limitations

The prices in this dataset are capped: every area worth more than 500,000 is recorded as 500,001. The model can never predict a price above about 500,000, even for very expensive areas. The data is also from 1990, so the prices are old. I used it to practise the method.
