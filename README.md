# Enron
A data science project to predict people of interest (POI) involved in the Enron sacandal.

Table of Contents
=================

   * [Introduction](#introduction)
   * [Directory Structure](#directory-structure)
   * [Pre-Process and Exploration](#pre-process-exploration)

## Introduction
This project was done to explore the Enron scandal and to create models to predict whether someone at the company was involved in the scandal. The data was received
from an online machine learning course on Udacity (https://classroom.udacity.com/courses/ud120), so the data was already pretty organized. However, the data is not perfect
as it contains missing values and therefore still requires pre-processing. The pre-processing is done in EnronPreprocess.ipynb whereas the models are trained and evaluated
in EnronModel.ipynb. The goal of the project is to predict who is a person of interest (POI) which is classified as someone who was either indicted, settled without adimtting 
guilt, or testified in exchange for immunity. The features of the dataset include salary, the number of emails sent to or received from a poi, deferral payments, etc.
PlotFunctions.py contains various plotting functions that allow for exploring features and targets and how they relate to each other.

## Directory Structure
<pre>
├── data
│   └── PreprocessedData.csv
├── data.pkl
├── EnronModel.ipynb
├── EnronPreprocess.ipynb
├── PlotFunctions.py
├── preprocess.py
</pre>

## Pre-Process and Exploration
- The data is read in from the pickle file and converted into a pandas dataframe.
- Various minor changes are made to the dataset to make it easier to explore (i.e. dropping the names and email addresses since they have no predictive power, 
changing the POI column to 0s and 1s instead of Strings, and making features numeric values rather than strings)
- An iterative imputer is used to fill in missing values
- Distributions of the features are displayed to find any patterns, many of them appear to be right-skewed, although the restricted_stock_deferred feature is left-skewed
- Features are plotted against targets, however, this did not reveal anything further about the data
- Finally, outliers are analyzed to see if any data should be dropped. Outliers are defined as any value that falls outside of the range of (1.5 x 75th_quantile - 25th_quantile)
  - No data was dropped as the outliers seemed to be valid and I don't think it would have benefited the models to drop them
  
## Models
- Random Forrest:
  - The best hyperparameters for the random forrest model are a minimum sample split of 4 and 100 estimators
  - This model has an accuracy score of 84% 
