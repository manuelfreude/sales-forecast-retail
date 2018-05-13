# Udacity Machine Learning Engineer Nanodegree
## Capstone Proposal
Manuel Freude

May 2018

## Proposal

### Domain Background

The project will investigate a problem that is often encountered in the business context. Sales forecasting is an imporant task for estimating cash flow and required inventory levels. The better the sales forecasting is, the better a company can predict it's cash balance and organize its supply chain. The dataset for the capstone project is obtained from https://www.kaggle.com/c/rossmann-store-sales. Rossmann operates over 3,000 drug stores in 7 European countries, mainly Germany. 

### Problem Statement

Rossmann store managers are tasked with predicting their daily sales for up to six weeks in advance. Store sales are influenced by many factors, including promotions, competition, school and state holidays, seasonality, and locality. With thousands of individual managers predicting sales based on their unique circumstances, the accuracy of results can be quite varied. 

### Datasets and Inputs

Kaggle is providing historical sales data for 1,115 Rossmann stores. The task is to forecast the "Sales" column for the test set. Some stores in the dataset were temporarily closed for refurbishment. Four files are provided:

    train.csv - historical data including Sales
    test.csv - historical data excluding Sales
    sample_submission.csv - a sample submission file in the correct format
    store.csv - supplemental information about the stores

Looking at these, it looks like Rossmann is doing the final accuracy test internally, i.e. they don't provide sales data in the test file, which makes it impossible to compare predicted sales forecast against real sales forecast or real sales, so accuracy calculations will be difficult. It makes sense to split the train file into training and two testing datasets including all relevant variables. The two testing datasets will be used for a) testing the trained model and b) creating an artificial "true" dataset, which will serve as our final "true" data to calculate the accuracy score.

### Solution Statement

Solution of the project is to provide a comprehensive sales forecasting that has a high accuracy no matter which circumstances influence the store sales and that can be applied on a continuous basis. By helping Rossmann create a robust prediction model, the project will help store managers stay focused on what’s most important to them: their customers and their teams! 

### Benchmark Model

Along the information given by kaggle, main difficulties of the benchmark model are high efforts and varying accuracy of the manual sales predictions. Many different circumstances come into play, leading to different sales forecasts for different stores, which have a reason to exist but on the other hand are difficult to sanity check from upper management levels or financial controllers. The new model would improve this benchmark by laying out a clear path to calculate the sales forecast accuracy that people can a) trust in and b) could shift their efforts from sales forecasting itself towards understanding why sales forecasts were off, i.e. further improving the model in the end.

### Evaluation Metrics

The evaluation metric is the accuracy score of sales forecast vs. real sales data. As listed in the benchmark model, this score has been highly variable, yet we do not have exact benchmark figures. The project will include the following accuracy score by sklearn: the set of labels predicted for the training set must exactly match the corresponding set of labels in the (split) test set. Result will be a number between 0 and 1, which will be translated into a percentage. As Rossmann is not provided real accuracy score numbers, the goal will be to deliver a score as highly as possible. Benchmarks of "what good looks like" will be created by the iterations of different methods to solve the problem within this project. 

### Project Design

The kaggle project had been completed some time ago, I had a look at blog posts from the first (http://blog.kaggle.com/2015/12/21/rossmann-store-sales-winners-interview-1st-place-gert/), second (http://blog.kaggle.com/2016/02/03/rossmann-store-sales-winners-interview-2nd-place-nima-shahbazi/) and third (http://blog.kaggle.com/2016/01/22/rossmann-store-sales-winners-interview-3rd-place-cheng-gui/) prize winners to understand their way of approaching the solution. 

This is a classification problem where we input data and want the model to derive a sales forecast based on the input. In the CharityML project, I had already applied a choice of supervised classifiers: AdaBoost Ensemble, Support Vector Machines and Logistic Regression. Based on the blog posts listed above, it seems that XGBoost is a classifier I should also consider. It requires more training time without GPUs, I might use AWS for speeding up the calculations. I will compare the performance of these methods to get a feeling of the respective accuracy scores and decide which model works best. 

Before I start building the models, I need to wrangle the data and have a closer look at potential feature engineering. I will run this in an EDA-like manner looking at several uni- and bivariate numbers and plots, either coding with R or Python. Useful outputs might be correlation matrices or boxplots, examples from a former EDA project I did (public https://github.com/manuelfreude/white-wine-quality) are provided below: 

![](https://github.com/manuelfreude/sales-forecast-retail/blob/master/Sample%20correlation%20matrix.png)

![](https://github.com/manuelfreude/sales-forecast-retail/blob/master/Sample%20box%20plot.png)

Subsequently, I will write the classification code in Python. The performance evaluation could look similar to my CharityML (private https://github.com/manuelfreude/charity-ml-donors) project as stated below: 

![](https://github.com/manuelfreude/sales-forecast-retail/blob/master/Sample%20model%20performance%20comparison.png)

Once I obtained the basic models and their accuracy scores, I will decide on the best model and try to improve it further, keeping track on whether the performance improved or not. 

When the model is finalized, I will provide a detailed model evaluation and summary of the key findings.  

-----------

