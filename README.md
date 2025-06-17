# MarketingAnalytics_and_Retail_BusinessMgmt
In this project, I have built models that can be used for forecasting house prices using linear regression, handling special events like Holiday Sales, identifying trends and seasonality for forecasting, Market Basket Analysis, RFM Analysis, Lifetime Customer Value, Estimating Demand, Pricing Strategy, and Pricing Analysis. I have used Microsoft Excel to solve business problems through formulas and calculations.

# You can read further for the theory and explanation of all the topics covered in this project, and can refer to the files used for data and insights.
## Business Knowledge - Understanding what all factors are important and have an impact on the variables of interest. "Quality of the inputs will decide the quality of the model output."

Types of Research - Primary Research & Secondary Research
Primary Research involves - 1. Discussions - Asking questions and gathering information from the stakeholders, 2. Dry Run - If possible, take a dry run of the problem you're trying to investigate.
Secondary Research involves - 1. Reports and Studies - Read reports and studies by the government agencies, trade associations, or other businesses. 2. Previous Works - Go through any previous work & findings related to the problem.

Linear Regression - Is a linear approach to modelling the relationship between a dependent variable and one or more independent variables.

Question - 1. Prediction Question - How accurately can I predict the price of a house, given the values of all the variables?                                                                                                      2. Inferential Question - How accurately can we estimate the effect of each of these variables on the house price?

## Simple Linear Regression is an approach for predicting a quantitative response Y on the basis of a single predictor variable X. It assumes that there is approximately a linear relationship between X and Y.

Model Equation --> Y ~ B0 + B1X  ; B0 --> known as Intercept, B1 --> known as Slope.

Together, B0 and B1 are known as the model coefficients or parameters.
From the training data, we get B0 and B1. Eg., Y ~ B0 + B1 * Room_num

## Estimating the coefficients -
* Our goal is to obtain coefficient estimates B0 and B1 such that linear model fits the available data well

* The difference between the ith observed response value and the ith response value that is predicted by our linear model is known as the residual.

* Residual sum of squares(RSS) - The Least Squares approach chooses B0 and B1 to minimize the RSS. Using some calculus, one can show that the minimizers are --> B0 = y - B1*x

We assume that the true relationship between X and Y takes the form Y = f(X) + e for some unknown function f, where e is a mean-zero random error term.

If f is to be approximated by a linear function, then we can write this relationship as - Y = B0 + B1*X + e ; B0 --> intercept, B1 --> Slope, e --> error term

Hypothesis Testing - Is there any relationship between X and Y? If B1 = 0, it means that there is no relationship
H0: No relationship between X and Y ; H0: B1 = 0
Ha: Some relationship between X and Y ; Ha: B1 != 0

To disapprove H0, we calculate the T statistics = B1 - 0/ SE(B1)

We also compute the probability of observing any value equal to t or larger. This probability is called the p-value.

* A small p-value(less than 5% or 1%) means there is an association between the predictor and response. Means, we can reject the null hypothesis and declare that there is a relationship between X and Y.

RSE is the average amount that the response will deviate from the true regression line. RSE is also considered a measure of the lack of fit of the model to the data.
RSE provides an absolute measure of lack of fit of the model to the data.

Adjusted R-Squared: More preferred term over R-squared. Modified version of R-squared that has been adjusted for the number of predictors in the model.                                                                                  Adjusted R-Squared increases only if the new term improves the model more than would be expected by chance. It decreases when the predictor improves the model by less than expected by chance.

## Multiple Linear Regression

More than 1 predictor variables are used to predict the response variable. The relationship between this can be - Y = B0 + B1X1 + B2X2 +...+BpXp + e ; B0 --> Intercept, p --> no. of predictors, e --> error term

* For our model the equation is --> Price = B0 + B1*Crime_rate + B2*poor_population+...+B16*avg_dist

* For each variable, we have a t-value, which tells us whether each individual predictor is related to the response.

* For a large no. of variables, if we depend on individual p-values, there is a very high chance that we will incorrectly conclude that there is a relationship between predictor variables and the response variable.

Solution:- To adjust the no. of predictors for these p-values, the new statistic, which adjusts the no. of predictors, is called the F-statistic.

F = (TSS - RSS)/p / RSS(n-p-1)
* We also have to check whether the p-value of the F-statistic is lower than a threshold, i.e., 5% or 1%
* p-value threshold --> values < 0.05 ==> impacting dependent variable.

So, for categorical variables, MLR Yi = B0 + B1*Xi + Ei, If Airport present then --> B0+B1+Ei, If Airport is not present then --> B0 + Ei

## Limitations of Regression in Excel
* Excel Regression tool can handle a maximum of 16 dependent variables, which may not be sufficient when Categorical variables have a lot of categories.

* Solution --> Excel Solver can be used to build a forecasting model involving up to 200 changing cells.

* Excel Solver is an optimization tool that finds the best solution (maximum, minimum, or specific value) for a formula in one cell (the objective) by changing values in other cells (the variables/decision cells) subject to certain constraints.

* We can incorporate the effects of Special Events like eg, Holiday Sales, Match nights, etc., which lead to unusual changes in the sales/marketing activity.

# Seasonality & Trends

* Seasonality is a characteristic of a time series in which the data experiences regular and predictable changes that recur every calendar year. Any predictable fluctuation or pattern that recurs or repeats over a one-year period is said to be seasonal.

* A pattern of gradual change in a condition, output, or process, or an average or general tendency of a series of data points to move in a certain direction over time, represented by a line or curve on a graph. Trend is not affected by seasonal change. It is a Gradual change over the years.

* Problem Statement - 1. Monthly airline miles travelled data Jan'09-Apr'18                                                                                                                                                                2. Identify seasonality and trend effects                                                                                                                                                                            3. Forecast future sales
* For forecasting, we have 2 Models and we have used both-

* Additive Model --> Predicted Period t Sales = Base + Trend * Period Number + Seasonal Index for Month t

* Multiplicative Model --> Predicted Period t Sales = Base * (Trend t) * (Seasonal Index for Month t)

# Market Basket Analysis & Lift

* Identifying products that customers buy together, place them closely to increase cross-selling.

* Market Basket - List of products bought by each customer ==> Although, primary aim of maintaining this data may be to do invoicing or inventory management, but can be used for Market Basket Analysis, i.e, extracting useful information from the transactions that customers are having.

## Lift = (Actual no. of times combination occurs) / (Predicted no. of times combination occurs if items in combination were independent)

E.g., Step 1 --> Get data of the past 100 transactions
      Step 2 --> How many people bought vegetables (out of 100), How many people bought meat (out of 100)
      Step 3 --> If these 2 are independent, how many people would have bought both?
      Step 4 --> Compare this number(3) with the actual number of people who have bought both.

      Observation ==> If actual>3, Products are complementary
                      If actual<3, Products are not complementary

So, the Formula for Lift would be => Fraction of people buying a & b both / (Fraction of people buying a) * (Fraction of people buying b) > 1

For 2 products --> it is called 2-way Lift; For 3 products --> it is called 3-way Lift.

We have used Named Ranges, the Indirect function, Solver, and Data Table for What-If Analysis for finding out the combination of product values that are greater than 1 and can be placed closely, eg. DVDs and Baby products have more than 1 value so they can be placed closely. # Walmart increased its profit by placing DVDs and Baby products in the same set.

# Recency, Frequency & Monetary Value Analysis

## To find out the 'Best Customers' basis past purchase behavior. 'Best Customer' --> More likely to purchase our products

*Example - Database of 1000 customers
            Cost of sending promotional mail - $1 per mail
            Profit/product sale - $100
(1) Send 1000 mails for 2% conversion OR (2) Send 300 mails for 5% conversion. Which is more profitable?

Recency - How recent was the last purchase
Frequency - How many times the customer has purchased from us
Monetary value - Average amount of purchases made by the customer/year

* Customer is rated on these 3 parameters from 1 to 5; 5 for most likely to purchase & 1 for least likely to purchase

* The top 20% of the customers who have the most recent purchases will be ranked five, the Next 20% will be ranked four, and so on.

* Same with Frequency - Top 20% customers with high frequency will be given 5

* Same with Monetary Value.

* We've chosen the categories that will give us the Best ROI(return on investment)

* Steps --> 1. Rank customers on 3 parameters: R, F, and M
            2. Use historical data to find the response rate of each combination of RFM ranking
            3. Choose the categories with the highest conversion rate for marketing communication

* For Ranking in Excel, we use -> 1. Rank.AVG (for Recency), Countifs (for finding out the no. of customers matching the category of all three R, F, M)

# Pricing

* Steps - I. Selecting the Pricing Objective
          II. Determining Demand
          III. Estimating Costs
          IV. Analyzing Competitors' Costs, Prices, and Offers
          V. Selecting a Pricing Method
          VI. Selecting the Final Policy

I. Selecting the Pricing Objective - (a) Survival, (b) Maximize Current Profit, (c) Maximum Market Share, (d) Maximum Market Skimming (Tech Companies, eg, Apple),                                                                                        (e) Product-Quality Leadership, (f) Other Objectives.

*** Most Common Pricing Objective --> Maximum Current Profit / Maximum Market Share

# Estimating Demand

* Sensitivity of demand with price tells you how much the demand will change when you change the price.

* Estimating the Demand Curves -  1) Surveys - Can explore how many units consumers would buy at different proposed prices.
                                  2)Price Experiments - We can vary the prices of different products in a store or charge different prices for the same product to see how the change affects sales.
                                  3) Statistical Analysis - Using past prices, quantities sold, and other factors to get a relationship between these factors and estimate the price and quantity demanded.

* Price Elasticity of Demand - Given a demand curve, the price elasticity of demand is the " % of decrease in demand resulting from a 1 percent increase in price".

* Forms of Demand Curves - (1) Linear Demand Curve --> q = a - b*p, (2) Power Demand Curve --> q = a*p^b, (3) Subjective Demand Curve --> Demand = a*(price)^2 + b*(price) + c

* Price Elasticity = (% Change in Quantity) / (% Change in Price)

* Nonlinear Pricing --> The Total amount a customer pays for a set of products is not equal to the sum of the individual product prices.

* Types of Nonlinear Pricing --> (1) Bundling --> (A) Pure Bundle, (B) Mixed Bundle                                                                                                                                                                  (2) Quantity Discounts --> (A) Standard Quantity Discount, (B) Non-standard Quantity Discount                                                                                                                       (3) Two-part Tariff
# Lifetime Customer Value

* Attrition OR Churn rate = 1 - Retention rate

* Basic Terminology: (1) Discount Rate - Refers to the interest rate used in discounted cash flow(DCF) analysis to determine the present value of future cash flows.                                                                     (2) Retention Rate - Customer retention rate designates the % of customers the company has retained over a given time period.

* Total present revenue / No. of customers initially --> Lifetime Value of Customers

* What does Customer LTV mean?
                              ==> Suppose we sell a Pizza for $20 that has a Production cost of $10 and the Margin price per customer of $10. Now, if we sell the Pizza for $5, that means we are bearing a loss of 75% on the Total Cost, and this idea brings 100 new customers, so the Total present-day value tells us how much revenue these customers would generate based on the idea of discounted rate. Also, if we have the Margin in total generated at the end of the year, then we have to calculate the Net Present Value(NPV), which is a formula in Excel that takes the value of the discounted rate & the Total Margin.

* Discount rate in CLV --> Represents the interest rate used to calculate the present value of future money, OR reduction in value for future money compared to its present value, accounting for time value of money.

## Sensitivity and Variation Analysis

* Sensitivity Analysis --> Used to tell how robust a model is. If the Customer Value does not change much by changing the Discount rate and Retention rate, then we have a fairly robust customer value calculated with us. If Customer Value changes a lot with a small change in Discount rate and Retention rate, firstly, we need to calculate very precisely what the actual discount rate and retention rate is. Secondly, by making small changes in these 2 things, we can significantly improve Profits and CLV.

* Variations in Retention Rate --> It is important to know when a customer is generating profit for the firm. The no. of customers generating profit will depend on this value:
                                    * 100 for the beginning of the year
                                    * 100 * (1 - retention rate) for end of year
                                    * 0.5 * 100 * (1 + retention rate) for middle of year

* Variations in Discount Rate --> Similarly, we have to account for the discount rate depending on when a customer is generating profit for the firm.
                                    * 1 for the beginning-of-year discount factor for year 1
                                    * 1/1.10 for the end-of-year discount factor for year 1
                                    * 1/1.1^0.5 for the middle-of-year discount factor for year 1 (1 + Discount rate + Period)

* Variations in Changing Margin --> Often, the profit from a single customer depends on the length of association that the customer has with the organization.
                                    Usually, the loyal customer with 4-5 years of association would bring a lot more revenue/profit as compared to a new, recently acquired customer.
                                    We can use a varying margin as per the business to account for this effect.
                                    How to find whether the margin for a customer will change or not? ==> Can do Secondary Research, Competitor Analysis, Primary Research, i.e, talking to customers.
                                    The revenue model must adjust based on when payments are made because customers may churn during the year.
                                    Therefore, it's important to consider the retention rate at different points to ensure the CLV calculation reflects only the customers who remain at the time of payment. 
