# Predicting Data Science Job Salaries

## Introduction

This project utilizes a dataset containing the salaries (in USD) of employees within the data science industry. The dataset was downloaded from Kaggle and is about 3 years old, so the statistics may not hold true anymore—especially considering the rapid growth of AI. The goal was to use this data to tackle the predictive task: to see if the salaries (in USD) of data science employees can be predicted through job characteristics such as experience level, job title, company location, and company size.

The predictive model focused on six key characteristics: experience level, employment type, job title, remote ratio, company size, and company location. Findings resulted after exploring four different models and four visualizations using the final model. While the project did not yield the desired results—the chosen features being good/sufficient indicators of salary—the data gained is still useful in understanding the industry.

## Data Source and Description

As previously mentioned, the data used in this predictive model comes from a dataset downloaded from Kaggle. The file provides a vast 245 rows of information and the eleven columns: work year, experience level, employment type, job title, salary, salary currency, salary in USD, employee residence, remote ratio, company location, and company size. With this dataset, the features that seemed most interconnected to the salaries are experience level, employment type, job title, remote ratio, company size, and company location. The other categories appeared to have significantly less correlation with salary (some of the categories being salary or a variant of salary). Furthermore, the file contains a diverse amount of data within the industry—making it more appealing and more accurate to the industry and task at hand.

## Exploratory Data Analysis

For the exploratory data analysis, four different models were explored—linear regression model, ridge regression model, lasso regression model, and random forest regressor model.

A linear regression model was used as a baseline model. Its simplicity and accessible interpretability allow for an easy comparison against more complex models to see if their complexities lead to any worthwhile performance improvements.

A ridge regression model was chosen to address multicollinearity introduced by one-hot encoded categorical variables. Furthermore, by applying L2 regularization, the model is able to shrink coefficient magnitudes and reduce overfitting. It is also included to see if regularization improves performance over the baseline linear model.

Next up is the lasso regression model. The model was chosen due to its L1 regularization—which allows it to perform feature selection. Additionally, through shrinking some coefficients to zero, the model is able to help identify the most influential predictors—an absolute necessity in this project.

Lastly, a random forest regressor model was included due to its nature as a non-linear model. As a non-linear model, it is capable of capturing the complex relationships and interactions between job characteristics. Salary is not guaranteed to depend on strictly linear combinations, so having this safety measure allowed for full coverage and assessment on what model was best at predictive performance.

Ultimately, upon comparing the R² scores, root mean square error (RMSE), and mean absolute error (MAE) with a model comparison table, it was determined that the ridge regression model performed the best amongst all the four models. The findings are as listed:
1. Linear regression and lasso regression performed the worst with a negative R² score of about -0.08 and -0.10 respectively. This indicates that the two models did not capture the variation in salaries well—a bit surprising for lasso regression model, but the findings not too much of a problem. Additionally, the RMSE and MAE scores of about 83934.13 and 43077.02 plus 84602.94 and 44116.97 respectively also support the notion that the models do a poor job at predicting the actual values.
2. Random forest regressor model performed better than the former two, with a positive R² of about 0.25 and a significantly lower RMSE and MAE of 69990.42 and 39327.44 respectively.
3. Ridge regression model had the best performance. It had the lowest RMSE of 68909.72, but with a slightly higher MAE than the random forest model at 40042.95. However, the R² of 0.27 and the better RMSE score overall indicate ridge regression to be the most optimal choice of the four.

Thus, the ridge regression was chosen as my final model to utilize for visualizations and analysis.

## Visualizations

For the visualizations, four visuals were selected—a scatter plot displaying the predicted vs actual salaries, a residual distribution histogram, a residuals vs predicted plot, and a ridge coefficient (feature importance) bar chart.

A predicted vs actual scatter plot was selected to evaluate and display the relationship of model predictions with actual salary values. The scatter plot provided an idea of model fit and also allowed for outliers to be visualized.

Next, a residual distribution histogram was chosen to examine the distribution of prediction errors. If the distribution centered around zero, then that implies unbiased predictions. On the other hand, extreme values help to identify outliers and any model limitations.

Third, a resiudals vs predicted plot was incorporated due to the ability of the plot at finding different model assumptions. If the random scatter is centered around zero, then there is indication of a stable model performance across the salary ranges.

Finally, with the feature importance bar chart, it's a given—the chart allows for a visualization of the importance of different features in relation to salary predictions. 

The findings through the visualizations are as listed:
1. Predicted vs Actual Scatter Plot
- R² Score (~0.27): The model explains roughly 27% of the variability in salaries. This indicates a weak to moderate fit.
- MAE ($40,043): The average prediction error is around $40,043, which is significant, especially for lower-paying roles.
2. Residual Distribution Histogram
- The histogram shows residuals centered near zero, indicating no massive systematic bias, but the long tails reflect the model's difficulty with extreme values.
3. Residuals vs Predicted Plot
- This plot reveals that while errors are generally centered around zero, the variance is not perfectly constant. There are distinct outliers at higher predicted values, suggesting that the model's precision decreases for higher-paying roles.
4. Ridge Coefficient (Feature Importance) Bar Chart
- Job Title: Specialized roles like Principal Data Engineer (+$167k), Financial Data Analyst (+$145k), and Applied Machine Learning Scientist (+$137k) command the highest premiums.
- Experience: Executive-level roles (EX) add approximately $75,000 to the baseline.
- Location: US-based roles (US) are associated with a $66,000 premium compared to the baseline.

## Interpretation

The model explains roughly 27% of the variability in salaries, indicating a weak to moderate fit. Furthermore, the average prediction error is around $40,043, which is significant, especially for lower-paying roles.

With the actual vs predicted salaries scatter plot, it is shown that while the model captures the general trend for low-to-mid salaries, it struggles with high-salary outliers, where points drift below the diagonal (indicating underprediction). Unsurprisingly, the residual distribution histogram shows residuals centered near zero, indicating no massive systematic bias, but the long tails reflect the model's difficulty with extreme values. This is then further reinforced with the reinforced vs predicted plot, which reveals that while errors are generally centered around zero, the variance is not perfectly constant. There are distinct outliers at higher predicted values, suggesting that the model's precision decreases for higher-paying roles. And while the bar chart did help with identifying some specific roles, experience, and location, those alone are still not enough on its own.

## Conclusion

This predictive task utilized ridge regression to identify key drivers of data science salaries—which unfortunately was not a satisfactory model for the task at hand. But with the information available, it can be noted that compensation is heavily influenced by seniority (Executive level), specialized job titles, and location (US-based companies pay significantly higher premiums). But to address the flaws, while the model successfully identifies these broad trends, the mean absolute error of $40,043 suggests that a significant portion of salary variance remains unexplained by the current features, which was reinforced by the different visualizations indicating unsatisfactory features. If this project were to be expanded upon, future iterations should incorporate more granular data, such as specific technical skills (e.g., Python, AWS, Spark), years of experience as a continuous variable, and educational background.
