# HELOC-RiskFlag-Prediction
House Equity Line of Credit (HELOC)

See html file for details.

## Overview
This project is to predict the HELOC credit flag with a high prediction accuracy while fully explaining the machine learning model used to predict the flag.

HELOC credit flag denotes whether the loan is risky or not. This risk flag is given 'good' or 'bad' according to the loan's risk. It can be easily found that the main feature affecting the risk flag is "Consolidated version of market risk", which is calculated by FICO. All the data is provided by FICO. 

Details of challenge can be found here: https://community.fico.com/s/explainable-machine-learning-challenge

## Keynotes
## Engineering new feature
Even though not provided, new feature "percentage of satisfactory trades" is provided as a new feature by calculating number of satisfactory trades and number of total trades.

## Feature Selection
Roughly 10 features will be selected based on three standards:

(1) Model-free feature selection
Univariate feature selection

(2) Model based feature selection
LassoCV
Permutation Feature Importance

(3) Correlation and outliers
Highly correlated features will not be included. (Only few will be selected)
Feature with too many outliers may lead a misleading result. Therefore these features may be filtered out.

## Model
Goal of this project is to achieve a high prediction accuracy and interpretable model at the same time. Therefore, both white-box models and black-box models will be used and provide various interpretations according to the results of fitted models. For white-box models, visualization and model-diagnostic methods wil be discussed. For black-box models, model agnostic post hoc methods such as VI, PDP, ICE, and SHAP will be used.

White-box model includes: GAM

Black-box models include: Gradient Boosting, MLP

Post hoc methods:

Variable Importance: for the forest based fitted models, variable importance will be discussed for the global interpretation.

Partial Dependency Plot (PDP) / Individual Conditional Expectation (ICE): Considering that the features are not highly correlated, dependency plots will provide meaningful insights of features globally.

SHAP: For both global and local interpretation, SHAP will be leveraged to explain how the changes in feature affect the prediction. SHAP will be fully leveraged especially for Deep Neural Network model.

## Conclusion
Logistic GAM with B spline reported 72.01% training accuracy and 71.89% test accuracy.
Gradient boosting reported 73.78% training accuracy and 70.89% test accuracy.
MLP reported 72.62% training accuracy and 70.79 test accuracy.

All models had similar accuracy (~1% gap). Hyperparameter tuning did not improve accuracy by a significant portion. This leads us to believe to achieve higher accuracy, the effects of better feature selection should be more significant than hyperparameter tuning. Further improvement on feature selection is recommended.

Finally, logistic GAM with b-splines is recommended. It has the highest test accuracy and smallest training accuracy to test accuracy gap. In addition, logistic GAM is a whitebox model. Therefore, it is more interpretable than the other two blackbox models we've used.
