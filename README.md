# ABSENTEEISM
Absenteeism dataset exploration

THE DATASET

This is the data set of an already existing study about the prediction of absenteeism at work.

Dataset: "Absenteeism_data.csv"

Raw dataset's columns: ID, Reason for Absence, Date, Transportation Expense, Distance to Work, Age, Daily Work Load Average, Body Mass Index, Education, Children, Pets, Absenteeism Time in Hours

We are trying to predict Absenteeism Time in Hours

This analysis will explore  whether a person presenting certain characteristics  is expected to be away from work at some point in time or not. 
In other words, we want to know how many working hours an employee could be away from work for, based on information  such as how far they live from their workplace, how many children and pets they have and whether they have higher education and so on.


PREPROCESSING

All the data preprocessing is executed in the Jupyter Notebook file "Absenteeism - Preprocessing.ipynb"

- Raw dataset gets loaded
- "ID" column gets removed as it doesn't provide any value to our analysis
- "Reason for Absence" gets transformed into dummy variables (we drop the first dummy to avoid multicollinearity)
- The "Reason for Absence" dummies get thematically grouped into 4 categories, we now have 4 "Reason for Absence" dummies (the base case is "no reason provided")
- We extract "Month" and "Day of the Week" from the "Date" column.
- We remove the "Date" column and add "Month" and "Day of the Week" columns to the dataset instead
- We analyze the "Education" column and decide to group the 4 values into 2 groups: "undergraduate" and "graduate".
- We save the preprocessed dataset as "Absenteeism_preprocessed.csv"

The resulting preprocessed dataset is: Absenteeism_preprocessed.csv


THE LOGISTIC REGRESSION

- We load the preprocessed dataframe. We are trying to predict "Absenteeism Time in Hours" by using all other columns as predictors.
- We look at the "Absenteeism Time in Hours", find its median, and use that as a cutoff for the creation of two classes: "Moderately absent" and "Excessively absent".
-We are now trying to predict, by using our predictors, if a person will be "Moderately absent" and "Excessively absent".
This is now a problem suiting a logistic regression.
- We create a custom scaler in order to be able to choose which columns to scale, in order to be able to leave the dummies unscaled.
- We shuffle and split the dataset into train and test sets (80/20 split).

- We train the model on the training dataset and evaluate its accuracy (0.77), both with a function, and "the long way", by comparing the prediceted results to the actual ones.

- We obtain the coefficients and intercept, and format them in a neat chart
- We drop some variables that did not have strong predictive powers ('Day of the Week','Daily Work Load Average','Distance to Work')

- The coefficients are predicting the log odds, so we interpret them by finding their exponentials and we add a "Odds Ratio" column to our summary table

