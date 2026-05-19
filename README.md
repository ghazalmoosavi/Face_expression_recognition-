# Face Expression Recognition with ResNet50

A deep learning project for multi-class image classification using a pretrained ResNet50 model to recognize human facial expressions from images.

<p align="center">
  <img src="https://img.shields.io/badge/PyTorch-DeepLearning-red?style=for-the-badge&logo=pytorch">
  <img src="https://img.shields.io/badge/Task-Image%20Classification-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Model-ResNet50-success?style=for-the-badge">
  <img src="https://img.shields.io/badge/Classes-7-brightgreen?style=for-the-badge">
</p>

---

## Overview

This project focuses on facial expression recognition using transfer learning with ResNet50. The model is trained to classify images into seven emotion categories:

- angry
- disgust
- fear
- happy
- neutral
- sad
- surprise

The notebook includes data preparation, preprocessing, class balancing, model training, and evaluation on train, validation, and test splits.

---

## Project Goal

The main goal of this project is to build a reliable emotion classification model that can identify facial expressions from images. Such a system can be useful in areas like human-computer interaction, emotion-aware interfaces, behavioral research, and educational tools.

---

## Dataset

The dataset used in this notebook is organized into separate training and validation folders. CSV files are generated from the image directory structure to make loading and preprocessing easier.

### Dataset Split

| Split      | Samples |
|------------|--------:|
| Training   | 28,821  |
| Validation | 3,533   |
| Test       | 3,533   |

The test set is created by splitting the original validation set.

### Classes

| Label    | Class Index |
|----------|------------:|
| angry    | 0 |
| disgust  | 1 |
| fear     | 2 |
| happy    | 3 |
| neutral  | 4 |
| sad      | 5 |
| surprise | 6 |

---

## Preprocessing

Images are preprocessed using the following steps:

- resize to `224 × 224`
- convert to tensor
- normalize using ImageNet statistics

### Data Augmentation

Training data is augmented with:

- horizontal flip
- random rotation

These augmentations help improve generalization and reduce overfitting.

---

## Model Architecture

The model uses a pretrained **ResNet50** backbone from ImageNet and replaces the final classification layer with a custom output layer for 7 emotion classes.

### Why ResNet50

- strong feature extraction capability
- effective for transfer learning
- works well on medium-sized image classification tasks
- pretrained weights speed up convergence

---

## Handling Class Imbalance

Since facial expression datasets are often imbalanced, the notebook calculates class weights from the training set and uses them in `CrossEntropyLoss`. This helps the model pay more attention to underrepresented classes.

---

## Training Configuration

| Setting        | Value |
|----------------|------:|
| Model          | ResNet50 |
| Input Size     | 224 × 224 |
| Batch Size     | 128 |
| Epochs         | 25 |
| Optimizer      | Adam |
| Learning Rate  | 1e-4 |
| Loss Function  | Weighted CrossEntropyLoss |
| Metrics        | Accuracy, F1 Score |

---

## Evaluation Metrics

The model is evaluated using:

- Accuracy
- F1 Score
- Cross-Entropy Loss

These metrics provide a balanced view of overall classification performance.

---

## Results

### Final Performance

| Phase       | CrossEntropyLoss | Accuracy | F1 Score |
|-------------|-----------------:|---------:|--------:|
| Train       | 0.018            | 0.99     | 0.99    |
| Validation  | 1.50             | 0.71     | 0.71    |
| Test        | 1.70             | 0.69     | 0.69    |

The model achieves strong training performance and moderate generalization on validation and test data.

---

## Visualizations

The notebook includes:

- class distribution plots
- sample image visualization
- training and validation curves for loss, accuracy, and F1 score

These plots help track performance and inspect dataset balance.

---

## Potential Applications

This project can be used as a base for:

- emotion-aware interfaces
- human-computer interaction systems
- educational and research tools
- behavioral analysis
- emotion classification experiments


