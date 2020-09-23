# Prostate cANcer graDe Assessment (PANDA) Challenge from [Kaggle](https://www.kaggle.com/c/prostate-cancer-grade-assessment).
**July 2020**

## Overview

Automated deep learning systems have shown some promise in accurately grading prostate cancer (PCa).
The target in this challenge is to improve on these efforts using the most extensive multi-center dataset on Gleason grading yet. 
The training set consists of around 11,000 whole-slide images of digitized H&E-stained biopsies originating from two centers, Radboud University Medical Center and Karolinska Institute. 

## Dataset

The dataset contains tabular data of image id, data provider, isup grade, gleason score and a tiff file attached to each image id.

The training set consists of around 11,000 full diagnostic biopsy images in tiff format. 

The grading process consists of finding and classifying cancer tissue into so-called Gleason patterns (3, 4, or 5) based on the architectural growth patterns of the tumor. After the biopsy is assigned a Gleason score, it is converted into an ISUP grade on a 1-5 scale.

## Image preprocessing

The tiff file contains 3-layer image with varied resolutions. 
I used the second layer with medium resolution in this model. The image was cut into small tiles of size $$128 \times 128$$ and ordered from the tile with most signal to the tile with least signal or blank tile. The first 16 tiles were picked and pasted together to be the input to train the model.

![image](./c32fba73ac1af46b2ccfd549172f1227.png)

**Python libraries:** _numpy, pandas, matplotlib, skimage_

## Model

A transfer learning model based on EfficientNetB3 was built.

Adam optimizer and Quadratic weighted Kappa loss were used to train the model.

**Python libraries:** _tensorflow, tensorflow-addons, scikit-learn, efficientnet, pygame_

## Inference and evaluation

Higher resolution input images and ensemble models can be used to boost the score.

