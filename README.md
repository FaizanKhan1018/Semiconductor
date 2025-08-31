Semiconductor Wafer Defect Augmentation & Analysis

Author: Faizan Khan

This repository contains a comprehensive Kaggle-style Jupyter Notebook (model56748.ipynb) where I explored semiconductor wafer map data, performed EDA, and developed augmentation strategies to simulate macroscale wafer maps with nanoscale defect overlays. While the raw dataset is not included, the notebook captures all relevant code, processing logic, and artifact generation.

Overview

Goal: Understand wafer defect patterns across two scales and synthesize realistic datasets for modeling.

Key Steps:

Load wafer maps and associated failure codes from .npy and .pkl files.

Perform exploratory data analysis: shapes, label distribution, and imbalance (9 unique failure codes, evenly represented).

Visualize macroscale maps and inspect pixel-level distributions.

Simulate nanoscale defects—grain boundaries, cracks, and voids—using OpenCV.

Augment both datasets (rotations, flips, noise), overlay nanoscale features on macroscale maps.

Handle class imbalance via oversampling and augmentation of defect and non-defect patterns.

Save the resulting augmented images as .npy files, ready for modeling pipelines.

Repository Contents
├── model56748.ipynb                   # Main exploratory and augmentation notebook
├── augmented_dataset/                 # Output datasets
│   ├── augmented_macroscale_images.npy
│   ├── augmented_nanoscale_images.npy
└── README.md                          # This documentation file

Detailed Workflow
1. Loading Data

Features: Wafer map arrays (.npy)

Labels: Tuple from a .pkl — includes label matrix and a failureCode series with 9 classes (0–8), each balanced equally.

2. Exploratory Data Analysis (EDA)

Dataset shapes identified and metadata printed for transparency.

Visualized label count distribution (all failure codes equally frequent).

Displayed image samples and plotted pixel distributions/histograms.

3. Synthetic Nanoscale Defect Generation

Grain boundaries: random dark blobs using OpenCV circles

Voids: small bright spots (white circles)

Cracks: random dark lines

Nanoscale patterns are superimposed over macroscale wafer maps for realism.

4. Data Augmentations

Macroscale maps: rotation, flips, brightness variations, Gaussian noise.

Nanoscale overlays: zoom, shift, rotation for variability.

5. Balancing & Augmentation Strategy

Defect (1.0) and non-defect (0.0) pixel classes counted; background (255.0) excluded.

Used oversampling + augmentation to rebalance classes.

Combined balanced images saved into .npy arrays.

Results & Artifacts

Augmented dataset: 300 grayscale wafer images (256 × 256 × 1)

Balanced classes: non-defect vs defect emphasized

Visual examples (automatically generated via notebook):

Raw macroscale wafer images

Simulated microscale defect overlays

Final combined augmented images

Usage Instructions

Clone this repository:

git clone https://github.com/FaizanKhan1018/Semiconductor.git
cd Semiconductor


Open and run model56748.ipynb in Jupyter or Kaggle; update input paths as needed.

The notebook prepares and saves augmentations in augmented_dataset/.

Potential Extensions

Use the dataset to train classification models for defect prediction or wafer failure codes.

Apply segmentation architectures (e.g., U-Net) to localize defects.

Explore GAN-based synthesis for enhanced realism and variation.

About the Author

Faizan Khan is actively exploring semiconductor defect analysis using computer vision and data augmentation techniques. This project reflects a deeper dive into creating synthetic datasets and analyzing wafer failure patterns — perfect for research or academic modeling pipelines.

License

This work is shared under the MIT License. Feel free to use and build upon it!
