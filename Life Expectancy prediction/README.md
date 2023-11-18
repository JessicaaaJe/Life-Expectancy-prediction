# Life Expectation Prediction

Abstract: 
Our research question is what and how some factors specifically affect people’s life expectancy. We obtained raw data on life expectancy from Kaggle, and analyzed the data using R. We applied EDA analysis on each potential predictors, and fit multiple linear regression lines between life expectancy and statistically significant predictors. The final reaching equation is 
Log(Life.expectancy) = -0.0011 Adult.Mortality + 0.1994 Income.composition.of.resources +0.0005 Adult.Mortality : Income.composition.of.resources. 

## Introduction
Human life expectancy grows over the year, but to which factors contributed the variance in life expectancy has always been the concern. The data we drew from Kaggle related to life expectancy and health factors of overall 193 countries has been collected from the same WHO data repository website and its corresponding economic data was collected from the United Nation website. Of the 19 variables given, we need to find out which explains the variance in life expectancy and what is the mathematical relationship between life expectancy and these variables. 

## Method
EDA is first applied on each predictor. Abnormal pattern shows up when fitting the linear model between life expectancy and adult mortality rate. On the left-hand side of figure 2, there is an almost straight-up line which does not significantly explain the relationship

between these two variables. We then make an accommodation on the data by removing raw data whose life expectancy is less or equal to 50 to make the data be more accurately analyzed. The new dataset name is given at the first page of the R file: Life.expectancy.rate.

<img width="823" alt="Screen Shot 2023-11-18 at 3 20 24 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/c0a8e65d-6786-4ff3-bc84-117dbfdbec0f">

There is an association between the development status and life expectancy. Developed countries show higher life expectancy than developing countries. There is a negative linear association between life expectancy and adult mortality rate. Positive linear association exit between life expectancy and income composition of resources, between life expectancy and schooling. No clear relationship between life expectancy and HIV.AIDS. We therefore log(Life.expectancy) and form a relatively moderate linear relationship between log(life.expectancy) and BMI. There is no obvious linear relationship between Hepatitis.B and life expectancy, so we will not consider this variable in the multilinear regression line. Overall, 6 explanatory variables will be tested in the multilinear regression model: country 
status, adult mortality rate, BMI, HIV AIDS, income composition of resources, and schooling. 
After being clear on the 6 variables we choose to use in fitting the multilinear regression line, we run the BSS model. The response variable y in BSS should be log (life,expectancy) as from the conclusion we derived from EDA that log transformation is needed in some variables. The best fitted model has R-squared 0.93, composed of three variables - adult mortality, HIV.AIDS, income composition of resources and one intercept. 

<img width="737" alt="Screen Shot 2023-11-18 at 3 21 17 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/db8f0688-76f7-4802-b142-e1299810dfc6">

These three variables are not necessarily independent of each other, so interaction is better to be checked. We draw a 4*4 matrix table on the three explanatory variables and life expectancy to see the in between correlation. 

Correlation between HIV.AIDS and adult mortality is 0.74, so we consider an interaction term: HIV.AIDS : Adult.Mortality. The correlation between income composition of resources and adult mortality is -0.83. Another interaction is added: income.composition.of.resources : adult.mortality. Now, the X-es that should be putte in the new BSS model BSS2 changes to adult mortality, HIV.AIDS, income composition of resources, HIV.AIDS:Adult.Mortality, and income.composition.of.resources:adult.mortality. 


<img width="817" alt="Screen Shot 2023-11-18 at 3 22 07 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/6b244615-dd2c-410a-bcfe-057ddf96ac56">

As seen from the plot of the BSS2 model drawn based on the adjusted R squared, there are three BSS models with the same high adjusted R squared: 0.93. We will then make analysis and comparison between these three models. 
<img width="756" alt="Screen Shot 2023-11-18 at 3 22 42 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/9a57fd09-39bd-4a4e-801e-d791336a7f81">


Model1 (Life.expectancy ~ adult.mortality + adult:Mortality: HIV.AIDS + income composition of resources : adult mortality). Model 2: (Life expectancy ~ adult.mortality + income composition of resources + adult mortality : HIV.AIDS + income.composition.of.resources + adult.mortality : HIV.AIDS + income.composition.of.resources: adult.mortality). Model3: (Life expectancy ~ adult.mortality + HIV.AIDS + income composition of resources + adult.mortality : HIV.AIDS + income composition of resources : adult mortality. We then do an analysis of variance of these three models, check the probability of the F test and adjust the R square of three models. From the analysis of the variance table, model 2 successfully rejects model2, which is then statistically significant, but model 3 does not successfully reject model2, which means the added predictor HIV.AIDS is not statistically significant. The same conclusion can be drawn by checking the adjusted R square of three models. Adj.r squared 2 > adjj.r.squared 3 > adj.r.squared 1. The best model of this data set is therefore model2. 
Model 2 is then put as our final model: a linear regression between life expectancy and adult mortality, income composition of resources, adult mortality: HIV.AIDS, income composition of resources: adult.Mortality. All predictors are statistically significant and the adjusted r squared of this model is high as 0.9322. However, we consider to delete the interaction term adult mortality: HIV.AIDS because HIV.AIDS does not appear to be the explanatory predictors in this model. So we fit the second version of final model final2, fitting the linear regression model with only predictors adult mortality, income composition of resources and income composition of resources: adult mortality. The change in fitness of the model is insignificant, with less than 0.01 change in adjusted R squared. From the summary of the final model, we can conclude that the final model is 
log(life expectancy) = -0.0011 adult mortality + 0.1994 income composition of resources + 0.0005 adult mortality : income composition of resources + 4.2637. 

After fitting the final model, we check the conditions when fitting the linear regression model. The graph indicates a negative linear association between log(life expectancy) and predictors. The condition of linearity is met. 

<img width="831" alt="Screen Shot 2023-11-18 at 3 24 33 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/db8a119f-f361-4520-a9c9-7f8e3671262f">
Then, the residual plot checks the constant variance and zero mean. 
<img width="694" alt="Screen Shot 2023-11-18 at 3 25 16 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/47d0c13b-7767-40fd-b803-2cfcc5fdad72">

And the QQ plot checks the normality. 
<img width="712" alt="Screen Shot 2023-11-18 at 3 25 49 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/2a13954f-bfe6-431f-8cbf-e9651abcbadb">




## Analysis and Results
All of our analysis is completed by using R, and the packages we used include base, datasets, ggplot2, bestglm, Matrix, and leaps. In our process of analyzing the relation between life expectancy and the potential variables, We use the BSS model to get the best fitted linear regression line. In the R file, we also show how the final model can be obtained using nested F tests on every preditors. 
   	The model we chose was as follows:
<img width="746" alt="Screen Shot 2023-11-18 at 3 26 21 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/0d55a17e-3b01-4117-a4e6-5929069e0348">

 
Two statistics prove why it is the best fitted model. First, of the three models we fitted in, the final model has the highest adjusted R square. And second, all the

predictors in the model are statistically significant. Life expectancy is highly correlated to adult mortality and income composition of resources.  
Speaking of the performance of our final model, we think it fits our assumption that life expectancy is affected by a number of regressors. Although we only have three predictors in our final model, we still proved in the first part that all those predictors are influencing life expectancy. We chose the best model with predictors being statistically significant.

<img width="741" alt="Screen Shot 2023-11-18 at 3 27 05 AM" src="https://github.com/JessicaaaJe/R-Project/assets/94040700/1a85d7c5-6dd6-4cf1-a174-4cc906d49ea6">

Assuming no change in other predictors, we are 95% confident that Adult Mortality is estimated to be on the range between -0.0013 to -0.000893, Income Composition of Resources is estimated to be on the range between 0.1281 to 0.2707, Adult Mortality * Income Composition of Resources is estimated to be in the range between 0.00014 to 0.0008.

Holding everything else constant, on average, one unit increase in adult mortality will lead to -0.0011 increase in life expectancy, offset by 0.0005 unit increase in income composition of resources. Holding everything else constant, on average, one unit increase in income composition of resources will lead to 0.1994 unit increase in life expectancy, offset by an increase in 0.0005 unit increase in adult mortality. 

## Conclusion
By doing a thorough and comprehensive analysis of the datasets of life expectancy using five different variables, we came up with a model that could predict life expectancy using relevant regressors. In the process of building a model, we chose the best model with less regressors and could make the best prediction.		
In the beginning of our research, we aim to find factors that affect people’s life expectancy. The model includes two major factors that are significant to the prediction of life expectancy, and the interaction term reduces the problem of multicollinearity. Our research is useful because it could provide some helpful insights about the prediction and estimation of life expectancy. It can be used in medical as well as health policy area in the future.
















