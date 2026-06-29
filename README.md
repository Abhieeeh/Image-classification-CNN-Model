# 🌟 Intel Image Classification using CNN

A deep learning project designed to classify natural scenes into six distinct categories using a custom **Convolutional Neural Network (CNN)** built with TensorFlow and Keras.

---

## 📌 Project Overview

This repository contains the implementation of a custom Convolutional Neural Network (CNN) trained on the **Intel Image Classification** dataset. The model automatically classifies input images of size $150 \times 150$ into one of the following classes:
* 🏢 **Buildings**
* 🌲 **Forest**
* 🏔️ **Glacier**
* ⛰️ **Mountain**
* 🌊 **Sea**
* 🛣️ **Street**

---

## 📂 Project Structure

```bash
├── Dataset/
│   └── dataset.md          # Download link & details for the Intel dataset
├── Notebook/
│   └── cnn_model.ipynb     # Jupyter Notebook containing dataset exploration, preprocessing, model training, and evaluation
├── workflow/
│   └── DL(CNN).pdf         # Supporting PDF documentation detailing the deep learning workflow
└── README.md               # Project documentation (this file)
```

---

## 📊 Dataset Details

* **Name:** Intel Image Classification
* **Source:** [Kaggle Dataset Link](https://www.kaggle.com/datasets/puneet6060/intel-image-classification)
* **Image Properties:**
  * Images are loaded and resized to a common dimension of $150 \times 150$ pixels.
  * Converted to **Grayscale** representation.
  * Pixel values are normalized using $1/255$ rescaling to range between $[0, 1]$.
* **Data Splits:**
  * **Training Set:** 11,228 images (80% training split)
  * **Validation Set:** 2,806 images (20% validation split)

---

## 🧠 Model Architecture

The custom sequential CNN model is structured with the following layers:

1. **Input Layer:** Accepts grayscale images of shape `(150, 150, 1)`.
2. **Data Augmentation:** Utilizes random horizontal flips and random zooms during training to prevent overfitting and improve generalization.
3. **Convolutional Block 1:** 
   * `Conv2D` layer with 32 filters ($3 \times 3$ kernel, ReLU activation)
   * `MaxPooling2D` layer ($2 \times 2$ pool size)
4. **Convolutional Block 2:** 
   * `Conv2D` layer with 64 filters ($3 \times 3$ kernel, ReLU activation)
   * `MaxPooling2D` layer ($2 \times 2$ pool size)
5. **Convolutional Block 3:** 
   * `Conv2D` layer with 64 filters ($3 \times 3$ kernel, ReLU activation)
   * `MaxPooling2D` layer ($2 \times 2$ pool size)
6. **Flatten Layer:** Reshapes the multi-dimensional feature maps into a 1D vector.
7. **Dense Layer 1:** Fully connected layer with 128 units and ReLU activation.
8. **Dense Layer 2:** Fully connected layer with 64 units and ReLU activation.
9. **Output Layer:** Fully connected layer with 6 units and Softmax activation (one for each landscape category).

### Model Parameters Summary:
* **Total parameters:** 2,432,006 (9.28 MB)
* **Trainable parameters:** 2,432,006
* **Non-trainable parameters:** 0

---

## ⚙️ Training Configuration

* **Optimizer:** Adam
* **Loss Function:** Sparse Categorical Crossentropy
* **Epochs:** 10
* **Callbacks:**
  * **Early Stopping:** Monitors validation loss with a patience of 3 epochs and restores the best weights.
  * **Model Checkpoint:** Saves the best performing model model parameters as `best_model.keras` based on validation accuracy.

---

## 🚀 How to Run the Project

### 1. Prerequisites
Ensure you have Python installed, along with the following libraries:
```bash
pip install tensorflow numpy pandas matplotlib seaborn scikit-learn
```

### 2. Download the Dataset
1. Visit the [Kaggle Intel Image Classification](https://www.kaggle.com/datasets/puneet6060/intel-image-classification) page.
2. Download the dataset and extract it.
3. Place the extracted image directory inside the `Dataset` folder. Ensure the paths in the notebook match your folder structure (e.g., `Dataset/data/seg_train`).

### 3. Run the Training Notebook
Launch Jupyter Notebook or JupyterLab, open `Notebook/cnn_model.ipynb`, and run all the cells to train and evaluate the CNN model.