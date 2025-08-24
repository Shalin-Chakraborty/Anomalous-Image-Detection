# 🧠 Anomaly Detection in Images using Autoencoder

## 📌 Introduction

This project develops an intelligent system to detect anomalous images—such as spam or irrelevant pictures—within a folder. It utilizes an autoencoder neural network to learn normal image patterns and identify outliers based on reconstruction errors. The system is built using TensorFlow and Keras and includes image preprocessing, model training, and anomaly detection.

---

## 🖼️ Image Loading and Preprocessing

### ✅ Functionality

Images are loaded and preprocessed using the following steps:

- **Reading Images**: Loads images with valid extensions (`.jpg`, `.jpeg`, `.png`, `.gif`, `.bmp`) from the specified folder.
- **Resizing**: Resizes all images to a consistent shape of `128x128` pixels.
- **Normalization**: Scales pixel values to the range `[0, 1]` for improved model performance.

### 🔀 Data Splitting

- The dataset is split into **80% training** and **20% testing** to ensure balanced evaluation.
- This allows the model to learn from the majority of the data while being tested on unseen samples.

---

## 🧬 Autoencoder Model

### 🏗️ Architecture

The autoencoder consists of two main components:

- **Encoder**: Compresses the input image into a latent space representation using:
  - Flattening
  - Dense layers for dimensionality reduction
- **Decoder**: Reconstructs the image from the latent space using:
  - Dense layers for dimensionality expansion
  - Reshaping to match the original image format

### 📐 Latent Dimension

- The latent space dimension is set to `32`, which can be tuned based on image complexity.

### ⚙️ Compilation

- **Optimizer**: Adam
- **Loss Function**: Mean Squared Error (MSE)

### 🏋️ Training

- Trained for `20 epochs` with a `batch size of 32`
- Includes data shuffling and a validation split to monitor generalization

---

## 🚨 Anomaly Detection

### 📊 Reconstruction Errors

- After training, the autoencoder reconstructs test images.
- Reconstruction error is computed as the **mean squared error** between original and reconstructed images.

### 📏 Threshold Setting

- Anomaly threshold is defined as:
  - threshold = mean_error + 0.5 * std_error


- This helps distinguish normal images from anomalies.

### 🕵️ Anomaly Identification

- Images with reconstruction errors above the threshold are flagged as **anomalies**.
- These are considered significantly different from learned patterns and can be reviewed or deleted.

---

## ✅ Conclusion

This project successfully implements an autoencoder-based system for detecting anomalous images. Key strengths include:

- Robust preprocessing pipeline
- Effective autoencoder architecture
- Dynamic thresholding for anomaly detection

### 🚀 Future Enhancements

- Experiment with convolutional autoencoders for spatial feature learning
- Fine-tune latent dimensions and training parameters
- Add advanced preprocessing (e.g., denoising, augmentation)

---
