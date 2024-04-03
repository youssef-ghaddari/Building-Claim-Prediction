# Building-Claim-Prediction
Building-Claim-Prediction
# Challenge Context

Building insurance is an insurance policy that protects the structure of your home – the walls, roof, floors, and common areas – against damage that could be caused by a flood or storm, by a fire, or by vandalism.

This challenge is part of the non-life insurance pricing process, which often consists of two stages:

- **Frequency modeling**, to determine the expected number of claims that an insurer will receive during a given time period.
- **Severity modeling** to predict how much the average claim will cost.

## Challenge Goals

The goal of the challenge is to predict if a building will have an insurance claim during a certain period. You will have to predict a probability of having at least one claim over the insured period of a building. The model will be based on the building characteristics. The target variable is a:

- `1` if the building has at least a claim over the insured period.
- `0` if the building doesn’t have a claim over the insured period.

During this challenge, you are encouraged to use external data. For instance: shops number by INSEE code (geographical code), unemployment rate by INSEE code, weather…

Some data can be found on the following website: [data.gouv.fr](https://www.data.gouv.fr/)

## Data Description

The input data contains the variables: Identifiant; ft_2_categ; EXPO; ft_4_categ; ft_5_categ; ft_6_categ; ft_7_categ; ft_8_categ; ft_9_categ; ft_10_categ; ft_11_categ; ft_12_categ; ft_13_categ; ft_14_categ; ft_15_categ; ft_16_categ; ft_17_categ; ft_18_categ; ft_19_categ; superficief; ft_21_categ; ft_22_categ; ft_23_categ; ft_24_categ; Insee; target.

### Details

- **Identifiant**: variable to identify the client in our database. Do not use it to model. Id variable.
- **ft_2_categ**: year of observation for the insured policy.
- **EXPO**: time insured in Generali on the year. (Ex: Full year insurance EXPO = 1; 6 months EXPO = 0.5) Numerical variable.
- **superficief**: size in m2 of the insured building. Numerical variable.
- **Insee**: French geographical code to locate the insured building. Very useful to add external data. Geographical/categorical variable.
- **target**: target variable. (0: no claim, 1: at least one claim over insured period).
- **other ft_i_categ**: anonymized characteristics of the building. Categorical variables.

## Benchmark Description

We launched a fast benchmark with an xgboost model and got a 0.41 NGC score. It is a basic model where all categorical variables are label encoded. Most important variables are superficief, ft_22_categ, EXPO.

Parameters for xgboost were found by cross-validation.

## Metric

The metric used for this challenge is the normalized Gini coefficient.

The goal of this challenge is to build a model that predicts claims order. A model is good if it detects with a higher probability buildings that actually had a claim.

To calculate the metric, observations are ordered by decreasing predicted probability. Predictions are only used here to order observations. Thus, the relative magnitude of predictions is not used with this scoring method.

Kaggle challenge with the same metric: [www.kaggle.com/c/porto-seguro-safe-driver-prediction](https://www.kaggle.com/c/porto-seguro-safe-driver-prediction)
