# Plant Disease Classification Using Convolutional Neural Network (CNN)

## Project Overview

As part of my Deep Learning learning journey, I developed a Convolutional Neural Network (CNN) model to classify tomato leaf diseases from images. The objective was to understand the complete deep learning workflow—from dataset preparation to model evaluation—rather than simply using a pre-trained model.

This project helped me gain practical experience in computer vision, image preprocessing, CNN architecture design, model training, debugging, and performance evaluation using TensorFlow and Keras.

---

# Problem Statement

Plant diseases significantly reduce crop yield and quality. Manual identification requires agricultural expertise and can be time-consuming.

The goal of this project was to build a CNN model capable of automatically classifying tomato leaf images into their corresponding disease categories.

---

# Dataset

Dataset Used:
Tomato Leaf Disease Dataset

Total Images:
18,178

Number of Classes:
10

Disease Categories:

* Tomato Bacterial Spot
* Tomato Early Blight
* Tomato Late Blight
* Tomato Leaf Mold
* Tomato Septoria Leaf Spot
* Tomato Spider Mites
* Tomato Target Spot
* Tomato Yellow Leaf Curl Virus
* Tomato Mosaic Virus
* Healthy Tomato Leaf

---

# Initial Dataset Analysis

Before training the model, I analyzed the dataset structure.

Observations:

* Images were organized into separate folders based on disease labels.
* Each folder contained between approximately 1,500 and 4,000 images.
* The dataset was imbalanced, with the Healthy class containing significantly more images than some disease classes.

This imbalance was noted as a possible reason for future model improvements.

---

# Dataset Organization

To prepare the dataset for training, I manually created three folders:

Dataset/

* Training/
* Validation/
* Testing/

Dataset Split:

Training:
70%

Validation:
15%

Testing:
15%

This ensured that the model was evaluated on completely unseen images after training.

---

# Development Environment

Programming Language:
Python

Development Tool:
Jupyter Notebook

Deep Learning Framework:
TensorFlow 2.21.0

Libraries Used:

* TensorFlow
* Keras
* NumPy
* Matplotlib

---

# Image Preprocessing

Every image was resized to:

128 × 128 pixels

Reason:

All images must have identical dimensions before they can be processed by the CNN.

Pixel values were normalized using:

Rescaling(1./255)

This converted pixel values from:

0–255

to

0–1

which improves training stability.

---

# CNN Architecture

The model was built from scratch using TensorFlow Keras.

Architecture:

Input Layer

↓

Rescaling Layer

↓

Conv2D

↓

Batch Normalization

↓

MaxPooling2D

↓

Conv2D

↓

Batch Normalization

↓

MaxPooling2D

↓

Conv2D

↓

Global Average Pooling

↓

Dense Layer

↓

Dropout

↓

Output Layer (Softmax)

This architecture allows the model to gradually learn low-level and high-level visual features from tomato leaf images.

---

# Model Compilation

Optimizer:

Adam

Loss Function:

Sparse Categorical Crossentropy

Reason:

Since the dataset contains 10 mutually exclusive classes represented by integer labels.

Evaluation Metric:

Accuracy

---

# Initial Challenges

During the first training attempt, several challenges were encountered.

## Large Image Size

Initially, larger image sizes increased training time significantly.

Solution:

Reduced image size to 128 × 128.

---

## Training Time

Training was slow because the model was trained from scratch.

Solution:

Reduced epochs during initial experimentation.

---

## Dataset Imbalance

Healthy leaf images greatly outnumbered some disease classes.

Possible impact:

Model may become biased toward larger classes.

This was identified as an area for future improvement.

---

# Training Process

The model was trained for 5 epochs.

Training observations:

Epoch 1

Training Accuracy:

71.2%

Validation Accuracy:

22.5%

Observation:

The model had just started learning basic image features.

---

Epoch 2

Training Accuracy:

82.9%

Validation Accuracy:

86.9%

Observation:

The model learned disease patterns effectively, resulting in a significant improvement.

---

Epoch 3

Training Accuracy:

87.0%

Validation Accuracy:

52.3%

Observation:

Validation accuracy dropped considerably.

Possible reason:

Model began overfitting the training data.

---

Epoch 4

Training Accuracy:

90.2%

Validation Accuracy:

72.3%

Observation:

Validation performance recovered as training stabilized.

---

Epoch 5

Training Accuracy:

91.9%

Validation Accuracy:

72.3%

Observation:

Training accuracy continued improving while validation accuracy remained relatively stable.

This indicated slight overfitting.

---

# Model Evaluation

Final Training Accuracy:

91.93%

Validation Accuracy:

72.32%

Test Accuracy:

86.23%

Test Loss:

0.3997

The test accuracy was evaluated using completely unseen images, demonstrating that the model generalized reasonably well despite being trained from scratch.

---

# Model Saving

The trained model was exported as:

plant_disease_cnn.keras

This enables future inference without retraining the model.

---

# Prediction Pipeline

After training, the model was tested on individual images.

Prediction workflow:

Leaf Image

↓

Resize to 128 × 128

↓

Convert to Numerical Array

↓

Expand Batch Dimension

↓

CNN Prediction

↓

Softmax Probabilities

↓

Highest Probability

↓

Predicted Disease

↓

Confidence Score

The model successfully classified unseen tomato leaf images and returned both the predicted disease class and confidence percentage.

---

# Key Learning Outcomes

Through this project, I gained practical experience in:

* Image dataset preparation
* Data splitting strategies
* CNN architecture design
* Image preprocessing
* TensorFlow and Keras workflow
* Model compilation
* Deep learning training process
* Model evaluation
* Overfitting analysis
* Saving and loading trained models
* Image prediction pipeline

Most importantly, I learned not only how to train a CNN model but also how to understand each stage of the deep learning workflow.

---

# Current Limitations

Although the model achieved encouraging results, several improvements can be made.

Current limitations:

* Dataset imbalance
* Basic CNN architecture
* No attention mechanism
* No transfer learning
* No Grad-CAM visualization
* No confusion matrix analysis

---

# Future Improvements

Planned upgrades include:

* Data Augmentation
* Class Weight Balancing
* Attention-Based CNN (CBAM)
* MobileNetV2 / EfficientNet Transfer Learning
* Confusion Matrix
* Classification Report
* Grad-CAM Explainability
* Web-based Prediction Interface

---

# Conclusion

This project provided a complete end-to-end experience in building a Convolutional Neural Network for image classification. Instead of relying on transfer learning, the model was implemented from scratch to understand every stage of the deep learning pipeline, including preprocessing, architecture design, training, evaluation, and inference.

The final model achieved an 86.23% test accuracy on unseen tomato leaf images, demonstrating the effectiveness of CNNs for plant disease classification while also highlighting opportunities for future optimization through attention mechanisms and transfer learning.
