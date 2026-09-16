# Adaptive CNN with Image-Difficulty Guided Augmentation for Waste Classification

## 📌 Project Overview

This mini project presents a CNN-based waste classification system using
image-difficulty guided adaptive augmentation.

The system classifies waste images into six categories:

- Cardboard
- Glass
- Metal
- Paper
- Plastic
- Trash

The project was implemented using TensorFlow/Keras in Google Colab.

---

## 🎯 Objective

The main objective is to investigate whether augmentation strength can be
adapted according to the difficulty of individual training images.

Instead of applying the same augmentation strategy to every image, the
training images are divided into Easy, Medium and Hard categories based
on difficulty scores obtained from a baseline CNN.

---

## 📊 Dataset

The project uses the TrashNet dataset.

Classes:

1. Cardboard
2. Glass
3. Metal
4. Paper
5. Plastic
6. Trash

The dataset was split into training, validation and testing sets.

Training images used:

1766

Validation images used:

377

---

## 🧠 Proposed Method

The overall pipeline is:

Dataset
↓
Baseline CNN
↓
Difficulty Score Calculation
↓
Easy / Medium / Hard Classification
↓
Difficulty-Guided Augmentation
↓
Adaptive Training Dataset
↓
Adaptive CNN
↓
Evaluation

---

## 🔍 Difficulty Estimation

Difficulty is estimated using the baseline model's prediction confidence.

For correctly classified images:

Difficulty = 1 - Prediction Confidence

Incorrectly classified images are assigned a high difficulty value.

The training images are then divided into:

- Easy: 70%
- Medium: 20%
- Hard: 10%

---

## 🔄 Adaptive Augmentation

### Easy Images

- Random horizontal flip
- Light rotation

### Medium Images

- Random horizontal flip
- Rotation
- Random brightness
- Random contrast

### Hard Images

- Random horizontal flip
- Rotation
- Stronger brightness adjustment
- Stronger contrast adjustment
- Central crop
- Resize

The original 1766 training images and 1766 adaptive images were combined,
producing 3532 training images.

---

## 🏗️ CNN Architecture

The CNN consists of:

- Conv2D – 32 filters
- MaxPooling
- Conv2D – 64 filters
- MaxPooling
- Conv2D – 128 filters
- MaxPooling
- Flatten
- Dense – 128 neurons
- Dropout – 0.5
- Softmax output – 6 classes

Total parameters:

11,169,734

---

## 📈 Experimental Results

| Model | Accuracy |
|---|---:|
| Baseline CNN | 53.65% |
| CNN + Standard Augmentation | 70.31% |
| Original Adaptive CNN | 58.85% |
| Corrected Adaptive CNN | 29.69% |

### Corrected Adaptive CNN Metrics

| Metric | Result |
|---|---:|
| Accuracy | 29.69% |
| Precision | 30.88% |
| Recall | 29.69% |
| F1-Score | 28.97% |

---

## 📌 Important Finding

The particular difficulty-guided augmentation strategy implemented in this
project did not improve test performance compared with standard augmentation.

The experiment demonstrates that difficulty-aware augmentation requires
careful selection of difficulty measures and augmentation strengths.

---

## 🛠️ Technologies Used

- Python
- TensorFlow
- Keras
- NumPy
- Matplotlib
- Scikit-learn
- Google Colab

---

## 📁 Repository Contents

```text
Adaptive_CNN_Waste_Classification.ipynb
README.md
report/
results/
screenshots/
