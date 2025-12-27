# Molecular Binding Prediction with 1D-CNN

A deep learning project focused on predicting chemical binding affinity for drug discovery. This project utilizes a 1D Convolutional Neural Network (CNN) to analyze encoded molecular representations against target proteins.

## Phase 1: Data Engineering & Initial Modeling
- **Dataset Handling**: Processed large-scale chemical datasets (~3.7GB Parquet files) using **PyArrow** streaming to bypass memory constraints.
- **Data Architecture**: Implemented stochastic sampling to create reproducible 100k-row training subsets for rapid prototyping.
- **Preprocessing**: Utilized a tokenized encoding schema (142 features per molecule) representing chemical structures.

## Model Architecture
The current model is a **1D-CNN** designed to extract local chemical patterns:
- **Embedding Layer**: Maps integer-encoded tokens into 64-dimensional dense vectors.
- **Conv1D & GlobalMaxPooling**: Identifies key structural motifs across the 142-token sequence.
- **Dense/Dropout Layers**: Interprets global features with regularization to prevent overfitting.
- **Output**: Multi-label classification (3 proteins) using Sigmoid activation.

## Current Results (Week 1)
| Metric | Score |
| :--- | :--- |
| **Initial AUC** | 0.51 (Baseline) |
| **Current Val-AUC** | **0.64** |
| **Loss** | 0.0114 |

*Observation: The model shows a clear learning curve, moving from random guessing (0.50 AUC) to 0.64 within 3 epochs, indicating structural chemical patterns are being successfully captured.*

## Tech Stack
- **Languages**: Python
- **Libraries**: TensorFlow/Keras, Pandas, Scikit-Learn, PyArrow
- **Environment**: Anaconda / VS Code
