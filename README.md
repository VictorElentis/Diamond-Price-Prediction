# Diamond Price Prediction

Which characteristics of a diamond determine its price, and how accurately can we predict it? This project answers that using about 54,000 diamonds.

## Data
The `diamonds` dataset from seaborn: 53,940 diamonds with carat, cut, color, clarity, dimensions and price.

## Approach
- Cleaned 23 rows with impossible dimensions (zero or extreme values)
- Explored the data and found that price is heavily right-skewed
- Log-transformed price and carat, and encoded cut, color and clarity as ordered categories
- Trained linear regression and random forest models on an 80/20 split and compared both to a mean-price baseline

## Results
| Model | RMSE | MAE | R² |
|---|---|---|---|
| Baseline (mean price) | $3,970 | $3,008 | 0.00 |
| Linear regression | $919 | $455 | 0.95 |
| Random forest | $532 | $264 | 0.98 |

The random forest's typical prediction is off by about 4.4%.

## Key findings
- Size drives price: `y` (width) carried about 85% of the forest's importance, with `log_carat` at 7%
- Clarity and color come next; cut barely matters once size is accounted for
- Ideal-cut diamonds are actually the cheapest on average ($3,457) because they tend to be smaller (0.70 carat)

## How to run
Open `diamond_price_prediction.ipynb` in Google Colab and select Runtime → Run all. No downloads needed, since the data loads through seaborn.

## Next steps
Cross-validation, hyperparameter tuning with GridSearchCV, and gradient boosting.
