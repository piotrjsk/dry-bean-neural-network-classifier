# Dry Bean Neural Network Classifier: PyTorch MLP Architecture Benchmarking

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep_Learning-EE4C2C.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data_Processing-150458.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E.svg)

## Project Overview

This repository contains a modular PyTorch deep learning pipeline and experimental benchmark for multiclass classification of dry bean species. 

The primary objective of this project is to evaluate Multi-Layer Perceptron (MLP) architectures, comparing the effects of network depth, neuron density, non-linear activation functions (`ReLU`, `Tanh`, `LeakyReLU`), optimization algorithms (`SGD`, `Adam`), and L2 regularization (`Weight Decay`) combined with an automated **Early Stopping** mechanism to prevent overfitting.

## Domain Context: The Dry Bean Dataset

The dataset, sourced from the Kaggle, consists of **13,611 high-resolution images** of 7 registered dry bean cultivars: *Seker, Barbunya, Bombay, Cali, Dermason, Horoz, and Sira*.

A total of **16 morphological features** were extracted from computer vision segmentation, divided into:
* **12 Dimensional Features:** Area, Perimeter, Major/Minor Axis Length, Aspect Ratio, Eccentricity, Convex Area, Equivalent Diameter, Extent, Solidity, Roundness, and Compactness.
* **4 Shape Form Factors:** Quantitative shape factors (`SF1` through `SF4`) measuring geometric complexity.

Accurately classifying bean varieties based on physical properties enables automated quality control and sorting in agricultural processing.

## Methodology & Architecture

1. **Data Pipeline & Preprocessing:**
   * **Feature Scaling:** Applied `StandardScaler` to handle scale variance across geometric measurements.
   * **Data Splitting:** Stratified split into **Training (70%)**, **Validation (15%)**, and **Test (15%)** sets to preserve class balance across all 7 bean varieties.
   * **PyTorch Integration:** Built custom PyTorch `Dataset` and `DataLoader` pipelines with dynamic batching.

2. **Model Experiments & Hyperparameter Tuning:**
   * **Baseline MLP:** Single hidden layer network for performance benchmarking.
   * **Deep MLP Architectures:** Expanded hidden layers with varied capacity (e.g., 64 and 32 neurons per layer).
   * **Activation Function Benchmark:** Systematic comparison of `ReLU`, `Tanh`, and `LeakyReLU`.
   * **Optimizer & Regularization Analysis:** Evaluated convergence dynamics between standard `SGD` and adaptive `Adam` optimizers, alongside L2 weight penalty (`weight_decay=1e-4`).
   * **Early Stopping Callback:** Monitored validation loss with patience parameters to halt training at optimal generalization.

## Experiment Results & Insights

Models were trained and evaluated on cross-entropy loss and classification accuracy across validation subsets.

**Summary of Architecture Experiments:**
| Model | Architecture Details | Activation | Optimizer | Val Loss | Val Accuracy | Convergence |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Baseline MLP** | [16 -> 32 -> 7] | ReLU | SGD | 0.3120 | 89.45% | Epoch 100 |
| **Model 2** | [16 -> 64 -> 32 -> 7] | ReLU | Adam | 0.2015 | 92.10% | Early Stop (Ep 34) |
| **Model 5 (Best)** | [16 -> 64 -> 32 -> 7] | Tanh | Adam | **0.1926** | **93.00%** | **Early Stop (Ep 28)** |

### Key Insight: Activation Dynamics & Convergence Rate
While `ReLU` provided steady baseline performance, switching to **`Tanh` activation with the `Adam` optimizer** yielded faster convergence and higher validation accuracy. Combined with Early Stopping, Model 5 reached optimal weights in **28 epochs**, achieving over **93% validation accuracy** while successfully eliminating overfitting risk.

## Repository Structure
```text
.
├── dry_bean_classification.ipynb      # Primary Jupyter Notebook with PyTorch experiments
├── requirements.txt                   # Dependency requirements
├── .gitignore                         # Git exclusion rules
├── README.md                          # Project documentation
│
└── data/
    └── dry_bean_dataset.xlsx          # Dry Bean Excel Dataset
```

## Key Technical Skills Demonstrated
* **Deep Learning Framework:** PyTorch model design using `nn.Module`, custom training/validation loops, gradient management, and tensor transformations.
* **Regularization & Optimization:** Implementation of custom Early Stopping callbacks, L2 regularization (`weight_decay`), and comparative optimizer benchmarking.
* **Data Processing & Preprocessing:** Scikit-Learn scaling pipelines, stratified sampling, and feature normalization.

## How to Run

```bash
# Clone the repository
git clone https://github.com/piotrjsk/dry-bean-neural-network-classifier.git
cd dry-bean-neural-network-classifier

# Install dependencies
pip install -r requirements.txt

```

---
*Developed by Piotr Jasiak & Mateusz Panek | [LinkedIn Profile](https://www.linkedin.com/in/piotrjasiak)*