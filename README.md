# Udacity Machine Learning Engineer Nanodegree
## Sales Forecast Retail Proposal
Manuel Freude

May 2018

### Python project summary

- Prepared dataset of +1 million rows & +45 columns incl. merger, dummy variables creation, data types change
- Conducted exploratory data analysis with visualizations and statistics
- Developed benchmark regressor, implemented 6 additional prediction models and fine-tuned two top performers

### Performance overview of selected algorithms

![Performance](https://github.com/manuelfreude/sales-forecast-retail/blob/master/Performance_comparison.png)

Overall, the benchmark model proved that it was not only a “placeholder” benchmark, but the linear regression could stand up against other more sophisticated algorithms with an RMSPE of below 1,200 and an r2 score of 91%. Yet, the two high-performing models showed even better performance, and the fine-tuning led to even further increases, especially for the XGBoost algorithm. XGBoost’s RMSPE of 634.38 is very strong, the r2 score of 97% also a great score, which is rarely seen in regression analyses. Both the refined MLP and XGBoost had performed slightly better on the test dataset than on the “true” dataset, but any hypothesis on overfitting can certainly be rejected at this point


## Proposal

### Domain Background

The project will investigate a problem that is often encountered in the business context. Sales forecasting is an important task for estimating cash flow and required inventory levels. The better the sales forecasting is, the better a company can predict it's cash balance and organize its supply chain. Some exemplary algorithms to solve this problem are regression techniques, which have been frequently discussed in academics (e.g. https://link.springer.com/article/10.1007/s00521-016-2215-x). The dataset for the capstone project is obtained from https://www.kaggle.com/c/rossmann-store-sales. Rossmann operates over 3,000 drug stores in 7 European countries, mainly Germany.

### Problem Statement

Rossmann store managers are tasked with predicting their daily sales for up to six weeks in advance. Store sales are influenced by many factors, including promotions, competition, school and state holidays, seasonality, and locality. With thousands of individual managers predicting sales based on their unique circumstances, the accuracy of results can be quite varied.

There are two ways to look at this from a data analysis point of view. Firstly, if we want to understand what are main contributors or "influence factors" for sales values, we would use regression techniques. Secondly, if we are less focused on how the sales values is estimated, but rather try to predict the sales values with other models that incorporate non-linearity, here we would also use regression techniques.

### Datasets and Inputs

Kaggle is providing historical sales data for 1,115 Rossmann stores. The task is to forecast the "Sales" column for the test set. Some stores in the dataset were temporarily closed for refurbishment. Four files are provided:

    train.csv - historical data including Sales
    test.csv - historical data excluding Sales
    sample_submission.csv - a sample submission file in the correct format
    store.csv - supplemental information about the stores

Looking at these, it looks like Rossmann is doing the final accuracy test internally, i.e. they don't provide sales data in the test file, which makes it impossible to compare predicted sales forecast against real sales forecast or real sales, so accuracy calculations will be difficult. It makes sense to split the train file into training and two testing datasets including all relevant variables. The two testing datasets will be used for a) testing the trained model and b) creating an artificial "true" dataset, which will serve as our final "true" data to calculate the evaluation metric. Summary stats will be provided in the project report.

### Solution Statement

Solution of the project is to provide a comprehensive sales forecasting that has a high accuracy no matter which circumstances influence the store sales and that can be applied on a continuous basis. By helping Rossmann create a robust prediction model, the project will help store managers stay focused on what’s most important to them: their customers and their teams!

After cleaning the data and engineering featutures, classifiers like Support Vector Linear Regressors or XGBoost will be applied and their performance compared. The final model will be build to forecast the sales values. Then the model's accuracy will be calculated along the evaluation metrics.

### Benchmark Model

Along the information given by kaggle, main difficulties of the benchmark model are high efforts and varying accuracy of the manual sales predictions. Many different circumstances come into play, leading to different sales forecasts for different stores, which have a reason to exist but on the other hand are difficult to sanity check from upper management levels or financial controllers. As Rossmann is not providing a benchmark in numbers, a linear regression benchmark will be build to estimate the sales values based on the given input assuming linear relations. This is not only a "placeholder" benchmark model as there is good reason to believe that it can perform very well to predict sales values.

The new regressor model could improve this benchmark by considering nonlinearities, performance scores of different algorithms will be compared. Overall goal is to lay out a clear path to calculate the sales forecast accurately that people can a) trust in and b) shift their efforts from sales forecasting itself towards understanding why sales forecasts were off, i.e. further improving the forecasting model in the end.

### Evaluation Metrics

The accuracy of the sales forecast is what we are looking for. As indicated above, this score has been highly variable, yet we do not have exact benchmark figures. As provided in the kaggle competition, the evaluation metric is the Root Mean Square Percentage Error (RMSPE). On top, the r2 score will be calculated for all models to showcase how much variance in the sales data can be explained by the model. Both will be calculated for the benchmark model and regressor models.

Rossmann is not providing real accuracy score numbers, the goal will be to deliver a score as highly as possible. Benchmarks of "what good looks like" will be created by the benchmark model and iterations of different methods to solve the problem within this project.  

### Project Design

The kaggle project had been completed some time ago, I had a look at blog posts from the first (http://blog.kaggle.com/2015/12/21/rossmann-store-sales-winners-interview-1st-place-gert/), second (http://blog.kaggle.com/2016/02/03/rossmann-store-sales-winners-interview-2nd-place-nima-shahbazi/) and third (http://blog.kaggle.com/2016/01/22/rossmann-store-sales-winners-interview-3rd-place-cheng-gui/) prize winners to understand their way of approaching the solution.

This is a regression problem where we input data and want the model to derive a sales forecast based on the input. In the Boston Housing Price prediction, I had been using regression techniques. Based on the blog posts listed above, it seems that XGBoost is an algorithm I should also consider. I'll check if I can include regressions in AdaBoost Ensemble and leverage Support Vector Regressors (instead of Machines). Some algorithms might require more training time without GPUs, I might use AWS for speeding up the calculations. I will compare the performance of these methods to get a feeling of the respective evaluation metrics and decide which model works best.

Before I start building the models, I need to wrangle the data and have a closer look at potential feature engineering. I will run this in an EDA-like manner looking at several uni- and bivariate numbers and plots, either coding with R or Python. Useful outputs might be correlation matrices or boxplots, examples from a former EDA project I did (public https://github.com/manuelfreude/white-wine-quality) are provided below:

![](https://github.com/manuelfreude/sales-forecast-retail/blob/master/Sample%20correlation%20matrix.png)

![](https://github.com/manuelfreude/sales-forecast-retail/blob/master/Sample%20box%20plot.png)

Subsequently, I will write the code in Python. The performance evaluation could look similar to my CharityML (private https://github.com/manuelfreude/charity-ml-donors) project as stated below:

![](https://github.com/manuelfreude/sales-forecast-retail/blob/master/Sample%20model%20performance%20comparison.png)

Once I obtained the basic models and their performance scores, I will decide on the best model and try to further improve it, keeping track on whether the performance increased or not.

When the model is finalized, I will provide a detailed model evaluation and summary of the key findings.  
