# Skin Lesion Classification: Melanoma vs. Nevus

This repository contains a complete computer vision pipeline for classifying dermoscopic images of skin lesions into two categories: benign Melanocytic Nevus and malignant Melanoma. 

This project was developed to automate skin cancer screening using feature-based classification inspired by the clinical "ABCD" rule (Asymmetry, Border, Color, Diameter).

## Project Overview

The pipeline processes raw dermoscopic images, isolates the lesion, extracts clinical features, and applies machine learning to predict malignancy. To prioritize medical safety, the model is tuned to maximize **Recall** for Melanoma, ensuring fewer malignant cases are missed.

### Key Features & Pipeline
* **Image Pre-processing:** Implemented Gray World color constancy to remove lighting artifacts and CLAHE for contrast enhancement.
* **Lesion Segmentation:** Utilized K-Means clustering ($k=2$) combined with morphological operations to isolate the lesion from healthy skin.
* **Feature Extraction:** Extracted 18 numerical features representing:
  * Shape & Border (Area, Perimeter, Compactness)
  * Color Variegation (RGB Mean and Standard Deviation)
  * Texture (GLCM and Local Binary Patterns/LBP)
* **Classification:** Trained a Random Forest classifier with balanced class weights to handle dataset imbalance.

## Dataset
This project uses a filtered subset of the **ISIC 2019** dataset, focusing exclusively on the `Melanoma` and `Melanocytic Nevus` classes. 
* You can download the full dataset from the [Kaggle](https://www.kaggle.com/datasets/salviohexia/isic-2019-skin-lesion-images-for-classification).

## Results

The model achieved an overall accuracy of **77%**, with a strong emphasis on detecting malignant cases. 

| Class | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- |
| Nevus (Benign) | 0.87 | 0.82 | 0.84 |
| Melanoma (Malignant) | 0.56 | 0.64 | 0.60 |

*Detailed analysis, including the ROC curve, confusion matrix, and feature importance (showing LBP and Color Std Dev as top drivers), can be found in the attached `Report.pdf`.*

## How to Run

1. Clone this repository.
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
