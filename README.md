# Sales Forecast Retail for Rossmann (kaggle challenge)
Source: https://www.kaggle.com/c/rossmann-store-sales

Revised version April 2019 (original completion May 2018)

### Python project summary

- Prepared dataset of +1 million rows & +50 columns incl. merger, dummy variables creation, data types change
- Conducted exploratory data analysis with basic visualizations and statistics
- Developed benchmark regressor, implemented 7 additional prediction models
- Fine-tuned three top performers and visualized most important features
- Developed a stacked model and evaluated added value

### Project results

![Performance](https://github.com/manuelfreude/sales-forecast-retail/blob/master/rossmann_revisited_results.png)

Overall, the benchmark model proved that it was not only a “placeholder” benchmark, but the linear regression could stand up against other more sophisticated algorithms with an RMSPE score of about 0.18 and an r2 score of 91%. Three additional models showed better performance, and fine-tuning along grid search led to even further increases, especially for the XGBoost algorithm. When applied to the "true" dataset, XGBoost’s RMSPE of 0.08 is very strong, the r2 score of 97% also a great score rarely seen in other regression analyses. The respective scores of the LightGBM are 0.09 and 97 %. The competition's evaluation metric is the RMSPE, the winner achieved 0.10 against the data provided by Rossmann, which was not available for scoring this project code.

![Leaderboard](https://github.com/manuelfreude/sales-forecast-retail/blob/master/final_leaderboard.png)

Many features were used and are relevant for business management decisions. Of the top performing XGBoost, the most important features were extracted and visualized. It is fairly obvious that the number of customers plays an important role to predict sales correctly, but competition data is also very helpful. Information about promotions improves the model, different store assortments also have an impact on an accurate forecast.  

![Feat_importance](https://github.com/manuelfreude/sales-forecast-retail/blob/master/XGB_feature_importance.png)

A stacked model incorporating the XGB, LightGBM and a neural net prediction did not result in added value. 
