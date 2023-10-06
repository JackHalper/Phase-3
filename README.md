# Phase 3 Project - Star Classification
By Jack Halper

## Overview 

The University of Washington (“The Client”) has come to us to assist in classifying celestial objects observed by the their newly upcoming sky-survey.
The University of Washington has hand-classified celestial objects in the past, however, with the new volume of observations coming in with their new extremely powerful ground based telescopes they would like to automate the classification process. If you want to dive deeper into the full analysis click [here!](https://github.com/JackHalper/Phase-3/blob/main/Final_Notebook.ipynb)

## The Data
The University of Washington has kindly provided us with [100,000 spectrograph classified observations of numerous celestial objects](https://www.kaggle.com/datasets/fedesoriano/stellar-classification-dataset-sdss17). There are no-missing values and the dataset is very clean.
These data were captured by the [Sloan Digital Sky Survey (SDSS)](https://www.sdss.org/) and represent a small sample of the overall survey which began in 2000. These data were captures with a 2.5 meter ground-based telescope located in Apache, New Mexico. The Data include a variety of spectroscopic observations of electromagnetic radiation celestial objects emit. Redshift, a proxy for distance which measures how much the wavelengths of the radition have lengthened as they traverse the continually expanding universe is a particularly important feature of this sample dataset. The celestial objects are classified in three distinct classes: Stars, Galaxies, and Quasars.

![image](https://github.com/JackHalper/Phase-3/assets/137962760/fffc73e3-0a17-4831-b532-72c4f01a8cbe)

It's evident that the dataset is slightly unbalanced with Galaxies comprising 60% of observations and Quasars and Stars making up the final 40%. It's important to note, however, that this is not reflective of the true nature of the composition of the universe. Galaxies are necessarily less abundant than stars given that they are literally comprised of stars but their significantly higher luminosity (often times billions or trillions times brighter than a single star) allows them to be seen from significantly further distances and therefore they make up a large percentage of observations because we are able to see galaxies that are orders of magnitutude further away then even the brightest stars. Quasars are even less common but make up a disproportionate amount of the sample due to their brightness. Quasars can be thousands of times brighter then our own milky way galaxy and have been observed up to ten's of billions of lightyears away as they appeared in the primordial universe.

## The Metric
Accuracy is the primary metric we have decided to evaluate the following predictive models. The reason for selecting accuracy as our evaluation metric is that for a survey of this nature, overall accuracy is the key perogative. The Difference between False Positives and False Negatives in this context is negligible and overall accuracy is the key concern. The objective is to obtain as accurate a survey of the universe as is attainable given the observations

## The Approach 
We utilize a supervised machine learning algorithm, Logistic Regression, to classify each object based upon select features of the spectrograph.

## The Features
The Features include spectroscopic observations of slices of the electromagnetic spectra emitted from objects. Each of these "slices" is represented with a numeric value. 

## The Target
Our target variable is the "class" variable which indicates if an object is (0) Galaxy, (1) Quasar or (2) Star

#### Investigating Collinearity
![image](https://github.com/JackHalper/Phase-3/assets/137962760/e593baa7-5918-4e04-9a61-dd4b36652515)

It's obvious several features exhibit severe collinearity. Notably, Z, U, and G; R and I are highly collinear exhibiting correlations approaching 1. Given that we utilizing logistic regression to create this predictive model, we must drop some collinear features due to the fact that logistic regression assumes no severe collinearity. We drop U, Z, and I to eleminate any outstanding collinnearity. Our final feature set is as follows: alpha, delta, R, G, and Redshift 

![image](https://github.com/JackHalper/Phase-3/assets/137962760/d1ad8ee1-f14a-4354-81cd-ac05eb2a6689)

Great! Now that we've dealt with collinearity we can move onto intializing our baseline model: 

## The Baseline Model (Logistic Regression with no modifications)

Our Baseline Model yields an impressive accuracy score of 95.015% and correctly classifies 76,012 out of 80,000 total objects correctly. The image below represents a confusion matrix evaluating our baseline model performance:  

![image](https://github.com/JackHalper/Phase-3/assets/137962760/7041111b-f6a1-402e-af38-a616719f496b)

## Hyperparameter Tuning
We manually tuned two specific hyperparameters using iterative cross-validation: C(Regularization Strength) and Solver. We find that C=100, which is very weak regularization, provides the strongest accuracy performance before pleteauing as regularization strength decreases. We feel confident selecting this weak regularization given the integrity, cleanliness and size of the overall dataset. 
We further find that the "Newton-CG" yields the best accuracy for our logistic regression predictive classification model

## Evaluating the Final Model
Our Final Model Preforms very well on the training data yielding an accuracy score of 95.83% and correctly classifying 76,663/80,000 objects.

![image](https://github.com/JackHalper/Phase-3/assets/137962760/d3adbce1-8a27-4d08-a1b3-a2a3ee7b64dd)

This accuracy performance represents an improvement on the baseline model by a factor of 0.8%





![image](https://github.com/JackHalper/Phase-3/assets/137962760/d4b36991-d31f-411b-9c0e-43b9258f9551)

Our Final Model performs very well on the unseen test data yielding an accuracy score of 95.665%; correctly classifying 19,133/20,000 objects. This compares to a baseline accuracy on the test data of 94.91%. Our final model, then, improved on the baseline model's accuracy by a factor of 0.75%

## Recommendations 
It's obvious that the model struggles most with distinguishing Quasars and Galaxies. 
Looking at the distribution of features it is obvious that redshift is the most distinguishing features between these three classes:

![image](https://github.com/JackHalper/Phase-3/assets/137962760/6b6db15f-97fc-49e5-bc2d-c69d9bb171e0)

There is substantial overlap, however, between galaxies and quasars in redshift whereas stars are almost uniformly at 0. Incorporating Radio Spectroscopy to the model to identify emissions unique to Quasars may provide the necessary data to improve the model's accuracy by giving the information it needs to distinguish between these two objects. Researchers should consider including this in future sky-surveys. 

## Next Steps

New unsupervised machine learning techniques could yield better results than this logistic regression model and should be considered as an alternative modeling solution for future attempts.

