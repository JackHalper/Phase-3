# Phase 3 Project - Star Classification


## Overview 

The University of Washington (“The Client”) has come to us to assist in classifying celestial objects observed by the their newly upcoming sky-survey.
The University of Washington has hand-classified celestial objects in the past, however, with the new volume of observations coming in with their new extremely powerful ground based telescopes they would like to automate the classification process. If you want to dive deeper into the full analysis click [here!](https://github.com/JackHalper/Phase-3/blob/main/Final_Notebook.ipynb)

## The Data
The University of Washington has kindly provided us with [100,000 spectrograph classified observations of numerous celestial objects](https://www.kaggle.com/datasets/fedesoriano/stellar-classification-dataset-sdss17). There are no-missing values and the dataset is very clean.
These data were captured by the [Sloan Digital Sky Survey (SDSS)](https://www.sdss.org/) and represent a small sample of the overall survey which began in 2000. These data were captures with a 2.5 meter ground-based telescope located in Apache, New Mexico. The Data include a variety of spectroscopic observations of electromagnetic radiation celestial objects emit. Redshift, a proxy for distance which measures how much the wavelengths of the radition have lengthened as they traverse the continually expanding universe is a particularly important feature of this sample dataset. The celestial objects are classified in three distinct classes: Stars, Galaxies, and Quasars.

![image](https://github.com/JackHalper/Phase-3/assets/137962760/fffc73e3-0a17-4831-b532-72c4f01a8cbe)

It's evident that the dataset is slightly unbalanced with Galaxies comprising 60% of observations and Quasars and Stars making up the final 40%. It's important to note, however, that this is not reflective of the true nature of the composition of the universe. Galaxies are necessarily less abundant than stars given that they are literally comprised of stars but their significantly higher luminosity (often times billions or trillions times brighter than a single star) allows them to be seen from significantly further distances and therefore they make up a large percentage of observations because we are able to see galaxies that are orders of magnitutude further away then even the brightest stars. Quasars are even less common but make up a disproportinate amount of the sample due to their brightness. Quasars can be thousands of times brighter then our own milky way galaxy and have been observed up to ten's of billions of lightyears away as they appeared in the primordial universe.

## The Metric
Accuracy is the primary metric we have decided to evaluate the following predictive models. The reason for selecting accuracy as our evaluation metric is that for a survey of this nature, overall accuracy is the key perogative. The Difference between False Positives and False Negatives in this context is negligible and overall accuracy is the key concern. The objective is to obtain as accurate a survey of the universe as is attainable given the observations

## The Features
The Features include spectroscopic observations of slices of the electromagnetic spectra emitted from objects. Each of these "slices" is represented with a numeric value. 

#### Investigating Collinearity
![image](https://github.com/JackHalper/Phase-3/assets/137962760/e593baa7-5918-4e04-9a61-dd4b36652515)

It's obvious several features exhibit severe collinearity. Notably, 

