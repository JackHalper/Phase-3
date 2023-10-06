# Phase 3 Project - Star Classification

## Overview 

The University of Washington (“The Client”) has come to us to assist in classifying celestial objects observed by the their newly upcoming sky-survey.
The University of Washington has hand-classified celestial objects in the past, however, with the new volume of observations coming in with their new extremely powerful ground based telescopes they would like to automate the classification process.

## The Data
The University of Washington has kindly provided us with 100,000 spectrograph classified observations of numerous celestial objects. 
These data were captured by the Sloan Digital Sky Survey (SDSS) and represent a small sample of the overall survey which began in 2000. These data were captures with a 2.5 meter ground-based telescope located in Apache, New Mexico. The Data include a variety of spectroscopic observations of electromagnetic radiation celestial objects emit. Redshift, a proxy for distance which measures how much the wavelengths of the radition have lengthened as they traverse the continually expanding universe is a particularly important feature of this sample dataset. The celestial objects are classified in three distinct classes: Stars, Galaxies, and Quasars.


## The Metric
Accuracy is the primary metric we have decided to evaluate the following predictive models. The reason for selecting accuracy as our evaluation metric is that for a survey of this nature, overall accuracy is the key perogative. The Difference between False Positives and False Negatives in this context is negligible and overall accuracy is the key concern. The objective is to obtain as accurate a survey of the universe as is attainable given the observations


## The Features

