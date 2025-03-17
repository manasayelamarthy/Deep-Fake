# Deep-Fake
# Deepfake Detection using Inception & GRU

##  Overview
This project aims to detect deepfake videos/images using a combination of **Inception-based CNN** for feature extraction and a **GRU (Gated Recurrent Unit) network** for temporal sequence modeling. The dataset used for training is sourced from **Kaggle** and includes real and fake video frames.

---

##  Dataset
The dataset used for this project was obtained from **Kaggle** and consists of:
- **Real Images/Videos** (authentic human faces)
- **Deepfake Images/Videos** (generated using AI-based face manipulation techniques)

**Dataset Details:**
- The dataset was preprocessed to extract frames from videos.
- Images were resized to `299x299` for compatibility with the **Inception model**.
- The dataset is split into **training (80%) and testing (20%)**.

**Kaggle Dataset Link:** 

---https://www.kaggle.com/datasets/manasayelamarthy27/deep-fake-dataset

##  Model Architecture
We used a **hybrid model** combining a **pre-trained Inception model** (for spatial feature extraction) and a **GRU network** (for sequence modeling).

### **1️. Inception Model**
- **Model Used:** InceptionV3 (pretrained on ImageNet)
- **Purpose:** Extracts spatial features from input frames.
- **Modifications:**
  - Removed the fully connected layers.
  - Extracted high-dimensional feature maps.
  - Passed features to the GRU network.

### **2️. GRU Network**
- **Purpose:** Captures temporal dependencies in video sequences.
- **Architecture:**
  - Input: Extracted features from Inception
  - **GRU Layer**: Processes sequential data from multiple frames
  - **Fully Connected Layer**: Maps GRU outputs to a binary classification (real or fake)

---

##  Training Process
- **Loss Function:** Binary Cross-Entropy Loss
- **Optimizer:** AdamW (with weight decay)
- **Learning Rate Scheduler:** ReduceLROnPlateau (reduces learning rate if validation accuracy stagnates)
- **Metrics Used:** Accuracy, Precision, Recall
- **Batch Size:** 32
- **Epochs:** 10

## Results
Accuracy : 0.678
