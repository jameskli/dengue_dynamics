# Dengue Dynamics

## Scope
* Project efforts for the DataDriven.Org Dengue Spread Competiton <https://www.drivendata.org/competitions/44/dengai-predicting-disease-spread/>

* Given historical weekly weather data (features) and number of dengue cases (labels) for two cities:
  *San Juan, Puerto Rico (1990-2008)
  * Iquitos, Peru (2000-2010)
* Build a model to predict the number of dengue cases for the following time period:
  * San Juan, Puerto Rico (2008 -2013)
  * Iquitos, Peru, from (2010-2013)

## Note
* Created within Google Colab environment and exported to Github. Code may not work as-is (for example it imports Google Sheet files rather than CSVs.
* Code uploaded for demonstration purpose only.

## Challenges
* `year` and `weekstartdate` features are always permanently increasing. In other words, all training data is historical, and predictions are all in the future.
* Cannot use previous rows to feed into current row

## Approach

### Pipeline
* `city` is a Category 
* the rest of the parameters are numeric.
* `StdScaler` was applied (but is not necessary for random forest).

### Model
* Initial attempt with a number of models with default parameters)
* `cross_val_fold scores` shown (neg_mean_abs_error)
* `RandomForest` ultimately chosen

## Discussion
* Typical values: train MAE=2, Test MAE=15
* Hyperparameter tuning cannot correct over-fitted model
* Not enough data (only 1500 samples) relative to 16 features
* Train/Test split can actually affect the result (eg 0.25 vs 0.4)
* Re-run feature importance to capture at least 90% of importance (keep top 12 features)  
  * Feature reduction has some improvement to over-fitting condition
* Also attempted to use time-series approach although it was beyond scope of competiton

## Future Work
1. Get more data!
2. Reduce model complexity, for example: reduce dimension, change test split ratio, limit hyperparameter tuning
3. Try different algorithm – use something that is good for time series forecasting
4. Engineer feature to reflect biology like cumulative precipitation (using past data)

## Credits
### Group partners
* Irina Tran
* Ted Wang
* Wei Li




