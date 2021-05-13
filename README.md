## Predicting % of Capacity for an MLB Game Using Linear Regression

### Abstract

In this linear regression project, my goal was to come up with the most predictive model possible for the % of stadium capacity sold for an MLB game. My base features come from scraping [baseball reference](https://www.baseball-reference.com/teams/ARI/2019-schedule-scores.shtml) as well as weather data from [weather underground](https://www.wunderground.com/history/monthly/us/az/phoenix/KPHX/date/2019-9). Multiple linear regression model types were tested, including (but not limited to) base linear regression, polynomial regression, and lasso regression. Models were validated using 5-fold validation on a test dataset (80 % of total set) comparing R-squared and MAE. The primary use case for this model is to find potential low attendance games that can be prioritized in marketing campaigns and ticket promotions.

### Design

The design of this project focused on being able to predict the percent of stadium capacity used (tickets sold/stadium total capacity). Because of this, interpretability of the model was given less focus over prediction power. The main metrics for this model were either competitive in nature (team performance) or based on weather. The more predictive the model is, the more accurate targeted social media campaigns and ticket promotions can be.

### Data

The data for the 2019 MLB season was scraped from [baseball reference](https://www.baseball-reference.com/teams/ARI/2019-schedule-scores.shtml) and [weather underground](https://www.wunderground.com/history/monthly/us/az/phoenix/KPHX/date/2019-9) using both the beautifulsoup and selenium packages. The model focused on predicting stadium attendance, so teams away games were filtered out of the data set after aggregation and feature creation was completed. After some data exploration, I found that the first home series for teams [had a skewed % of capacity](https://user-images.githubusercontent.com/75561764/118175484-02c0bb00-b3e5-11eb-87bd-20d2423d4b50.png), which due to opening day being a popular 'holiday' like event made sense. The first set of games also suffered from lack of development in aggregate features such as Win-Loss %. This led me to filter out the first home series, and left ~2300 home games in the data set. The features consist of mostly performance based metrics such as: Win-Loss %, Avg runs scored in last 5 games, current win streak, and more. They also included weather features for max daily temperature and if there was rain that day or not.

### Algorithms

*Feature Engineering*

1. Variables were tested for multicollinearity (MC) using VIF and then cleaned to reduce MC.
2. Many features were created by aggregating a set number of games prior to create a rolling average.
3. Polynomial terms and interactions were introduced and cross validated

*Models Tested*
1. Base linear regression model
2. Linear regression model with interactions and some polynomials
3. Complete polynomial regression
4. Lasso regularization on the polynomial regression

*Model Evaluation and Selection*

I used 5-fold cross validation on 80% of the data and evaluated the listed models on 2 main criteria, [R-squared](https://user-images.githubusercontent.com/75561764/118177942-34875100-b3e8-11eb-9b38-bd17c30cef4c.png) and mean absolute error. This led to choosing the poly Lasso model as the best predictive model, which was validated again on the test set (remaining 20%).


### Tools

* Web Scraping Packages
  * Beautiful Soup for HTML scraping
  * Selenium for opening and allowing weather underground to load before scraping HTML
* Scikit-learn for the modeling and Validation
* Seaborn for plotting 

### Communication

The main form of communication for this model is through slides and a presentation.
