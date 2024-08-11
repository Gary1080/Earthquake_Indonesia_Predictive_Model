# Earthquake Prediction Model


## Introduction
This project focuses on predicting earthquake magnitudes in Indonesia using data from 2008 to 2022. Indonesia experiences frequent earthquakes due to its location in the "Ring of Fire." The dataset includes details like date, time, location coordinates, depth, and magnitude of each earthquake. Three machine learning models were compared: Linear Regression, Random Forest, and Neural Networks. This project highlights the potential of machine learning in natural disaster prediction.

This folder contains 4 files:
* data.csv - The training and validation data
* Earthquake_ML_Model.ipynb - The training/testing of 3 machine learning models (Linear Regression, Random Forest, & Neural Network)
* random_forest_model.pkl - SEE NOTE BELOW
* Model_Testing.ipynb - A notebook to allow testing of new data points
* data_sheet.md -  provides detailed information about the dataset including their creation, content, and intended use.
* model_card.md - provides details about the machine learning model, including its performance and limitations.

Note: the model 'random_forest_model.pkl' could not be uploaded to Github due to file size limtations therefore there are 2 options to obtain it:
1) download the model(1.53GB) from https://rapidgator.net/file/5e8b20640cf4eb1212fbad9c568d2f3a/random_forest_model.pkl.html
or
3) download the file 'Earthquake_ML_Model.ipynb' above onto your own machine from this repository and re-run the code to re-create the file 'random_forest_model.pkl'


## DATA
The dataset is taken from https://www.kaggle.com/datasets/greegtitan/indonesia-earthquake-data

This dataset contains records of all earthquake occurrences in Indonesia from 2008 to 2022, a region known for frequent seismic activity due to its location in the "Ring of Fire." The dataset includes the following columns:

    * __Date and Time__: When the earthquake occurred.
    * __Latitude and Longitude__: Geographic coordinates of the earthquake's epicenter.
    * __Depth__: Depth of the earthquake's hypocenter in kilometers.
    * __Magnitude__: Strength of the earthquake measured on the Richter scale.

## MODEL 

The Random Forest (RF) model was chosen as the final model due to its superior performance compared to Linear Regression and Neural Networks (NNs). The RF model achieved a Mean Squared Error (MSE) of 0.3184, Root Mean Squared Error (RMSE) of 0.5643, and Mean Absolute Error (MAE) of 0.4343 on the test set, indicating its high accuracy.

Strengths of Random Forest:

    * __Robustness__: RF is less prone to overfitting compared to NNs, particularly with small to medium-sized datasets.
    * __Interpretability__: RF provides insights into feature importance, aiding in understanding the model's decision process.
    * __Flexibility__: RF handles both linear and nonlinear relationships effectively, whereas Linear Regression assumes linearity.
    * __Less Data Preprocessing__: RF does not require extensive data scaling or normalization, unlike NNs, which need well-preprocessed data for optimal performance.

Given these advantages, the RF model is well-suited for predicting earthquake occurrences in the given dataset, providing reliable and interpretable results.

## HYPERPARAMETER OPTIMSATION

__Hyperparameters__:

    * __n_estimators__: The number of trees in the forest. Values tested: 100, 200, 300.
    * __max_depth__: The maximum depth of each tree. Values tested: None (no limit), 10, 20, 30.

__Grid Search CV__:
Grid Search Cross-Validation (Grid Search CV) was used to systematically explore the combinations of these hyperparameters to find the optimal settings for the Random Forest model. This process involves training and evaluating the model for each combination using cross-validation, ensuring robust performance across different subsets of the data.

## RESULTS

The Random Forest model achieved a Mean Squared Error (MSE) of 0.3184, Root Mean Squared Error (RMSE) of 0.5643, and Mean Absolute Error (MAE) of 0.4343 on the test set, indicating its high accuracy.


## Files
https://github.com/Gary1080/Earthquake_Indonesia_Predictive_Model/


