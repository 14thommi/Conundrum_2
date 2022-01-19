# Conundrum 1: Law and Order Modeling
[Go to Conundrum](https://community.dataiku.com/t5/Community-Conundrums/Conundrum-1-Law-and-Order-Modeling/m-p/5492#U5492)

### Problem Statement
Welcome to our first Community Conundrum! Get ready to put your deerstalkers on and dive into the world of crime! Below you will find a dataset containing crime data relating to March 2019 in Hampshire, UK. This data includes a few things including the type of crime, location where it took place etc. 

Can you use this data to build a model that predicts if the accused received any form of punishment? 

For the sake of clarity we count the following, and only the following, outcomes as punishment - you may spot a certain common word to make filtering your data easier! 

* Offender given a caution
* Offender given community sentence
* Offender fined
* Offender given conditional discharge
* Offender sent to prison
* Offender given suspended prison sentence
* Offender ordered to pay compensation 
* Offender deprived of property
* Offender given a drugs possession warning

You can find the data attached. Now go ahead and get modeling!

## Plugins to Install
1. None

## Code Environments
1. Reference the code_environment.zip file to import the code enviornment I used to run the python recipes

## Solution Results
* Best Model: Logistic Regression
* Best Model ROC: 0.719
* Best Model Accuracy: 96.2%

## Solution Details: by Zone in Project
#### Import Data
1. **2019_03_hampshire_street:** Imported CSV data from the conundrum. No unique import options used. [Get Data](https://community.dataiku.com/t5/Community-Conundrums/Conundrum-1-Law-and-Order-Modeling/m-p/5492#U5492)

#### Data Understanding
1. EDA Analysis: This folder is the output of the python code. It contains the .html file for the pandas profiling report which can be seen in the jupyter notebook of the code recipe. This details distributions, interactions, and more descibing the "prepared" dataset.

#### Data Preparation
1. **prepared:** Using a prepare recipe I cleaned the data for the following:
  * Removed Rows: Where Crime ID was null. These rows did not have sufficient values to perform inference from
  * Removed Columns: Removed the following columns: Reported by, LSOA code, Month, Falls within. As they were not helpful for inference or were incomplete.
  * Feature Generation: Created new columns to help with inference by reducing cardinality of fields
      * Crime Category: Used a python processor, to group Crime Type into one of four categories crimes against property, crimes against person, crimes against morality, and other
      * Punishment: Used the formula processor to define which crimes were punished and which were not
      * Created GeoPoint: Merged latitude and longitude into a geopoint which can be used for visualizations of geographic data.
2. **prepared_python:** Prepared additional features to use in the labs environment for predicting punishment of a crime:
   * Ran a python script to find the number of historical crimes/punishment within a 10km radius for each crime. For each geography we then get the percent chance of a crime being punished within 10km area. The idea is to leverage historical geographic crime propensity to predict outcome in future proceedings. Perhaps certain judges or certain communities punish more readily than others.
   * Ran variations of each model/data in the lab "Punishment Prediction"
   * The best result returned was 96.2% accuracy with an ROC of 0.719 using logistic regression

** I have added comments throughout the project flow to help you understand what steps I accomplished in more detail
