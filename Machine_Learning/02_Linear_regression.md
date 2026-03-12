# Linear Regression In Machine Learning

Linear regression is a type of supervised machine-learning algorithm that learns from the labelled datasets and maps the data points with most optimized linear functions which can be used for prediction on new datasets. It assumes that there is a linear relationship between the input and output, meaning the output changes at a constant rate as the input changes. This relationship is represented by a straight line.

algorithm used to predict a continuous numerical value based on input features.

It finds the best-fitting straight line that represents the relationship between input (X) and output (Y).

**Goal** -- Finds the best-fit straight line to model

**Example:**
Predicting house price based on size.

As the size increases, the price increases — linear relationship.

**Independent variable (input)**

  **Dependent variable (output)** 

<p align="center">
  <img width="506" height="323" alt="Representing-Linear-Regression-Model" src="https://github.com/user-attachments/assets/a348c8b2-744a-4af3-be7d-ef10c5dfe599" />
</p>

## Type of Linear Regression
<p align="center">
  <img width="614" height="329" alt="image" src="https://github.com/user-attachments/assets/23df0006-a216-4a4e-8369-14f18882dfd3" />
</p>

### Why Linear Regression is Important?

Simplicity and Interpretability

Predictive Ability

Basis for Other Models

Efficiency

Widely Used

## Goal of the Best-Fit Line in Linear Regression

The primary goal of the best-fit line in linear regression is to model the relationship between an independent variable (X) and a dependent variable (Y) in the most accurate and generalizable way.

More specifically, the best-fit line aims to:

**1. Minimize Prediction Error**

The line is chosen such that it minimizes the overall error between actual values and predicted values.
In standard linear regression, this is achieved using the least squares method, which minimizes the sum of squared residuals:

Residual = Actual Y − Predicted Y

Squaring ensures positive values and penalizes larger errors more heavily

This results in a line that is statistically optimal for prediction under common assumptions.

**2. Capture the Underlying Trend**

The best-fit line represents the average trend in the data rather than fitting every point exactly.
It helps distinguish signal (true relationship) from noise (random variation).

**3. Enable Reliable Prediction**

Once fitted, the line can be used to:

Predict Y for new, unseen X values

Estimate expected outcomes under different conditions

This is critical in business, engineering, and scientific decision-making.

**4. Quantify the Relationship Between Variables**

The slope and intercept provide interpretable insights:

Slope (β₁): How much Y changes for a one-unit change in X

Intercept (β₀): Expected value of Y when X = 0

These parameters allow stakeholders to understand direction, strength, and sensitivity of the relationship.

**5. Support Statistical Inference**

A best-fit line enables:

Hypothesis testing (e.g., “Is X significantly related to Y?”)

Confidence intervals for predictions

Model evaluation metrics such as R² and RMSE

In Simple Terms

The best-fit line is the line that stays as close as possible to all data points on average, while remaining simple, interpretable, and predictive.


## nbfieheoijoigowrg

<p align="center">
 <img width="1536" height="1024" alt="ChatGPT Image Jan 1, 2026, 07_58_32 AM" src="https://github.com/user-attachments/assets/31d55c7c-0938-4be3-b08b-24e6a79b6c28" />
 <img width="479" height="267" alt="A-simulated-dataset-of-20-observations-from-a-multiple-linear-regression-consisting-of-3" src="https://github.com/user-attachments/assets/a43fc5d3-3ae5-419e-8521-7c3788aa5175" />
</p>




