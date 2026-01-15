# 😷 Face Mask Detection using Deep Learning

A real-time **Face Mask Detection System** built using **Deep Learning and Computer Vision**.  
The model classifies detected faces into **three categories**:
- ✅ With Mask  
- ❌ Without Mask  
- ⚠️ Mask Worn Incorrectly  

This project uses **OpenCV for face detection** and **InceptionV3** for accurate multi-class classification.

---

## 📌 Project Overview

The system detects human faces from images or live video streams and classifies mask usage in real time.  
Unlike many existing solutions, this model includes a **third class: `mask_weared_incorrect`**, improving real-world applicability.

---

## 🧠 Architecture

The system consists of **two main modules**:

### 1️⃣ Face Detection
- Uses OpenCV’s DNN-based face detector  
- Model: `res10_300x300_ssd_iter_140000.caffemodel`
- Detects faces and extracts bounding boxes

### 2️⃣ Face Mask Classification
- Base Model: **InceptionV3** (pre-trained on ImageNet)
- Custom classification head added
- Output Classes:
  - `with_mask` → 0
  - `without_mask` → 1
  - `mask_weared_incorrect` → 2

---

## 🔄 Data Processing Pipeline

1. Parse XML annotations  
2. Extract face bounding boxes  
3. Crop detected faces  
4. Resize images to `224 × 224`  
5. Apply preprocessing & augmentation  
6. Encode labels into integers  

---

## 🏗️ Model Details

**Base Model:** InceptionV3 (`include_top=False`)

**Custom Head:**
- Flatten  
- Dense(1024, ReLU)  
- Dropout(0.2)  
- Dense(512, ReLU)  
- Dense(3, Softmax)

---

## ⚙️ Training Configuration

| Parameter | Value |
|---------|------|
| Optimizer | Adam |
| Loss Function | Sparse Categorical Crossentropy |
| Epochs | 20 |
| Batch Size | 16 |
| Input Size | 224 × 224 |
| Augmentation | Rotation, Zoom, Flip, Shift |

---

## 📊 Results

- **Training Accuracy:** 94.3%  
- **Validation Accuracy:** 91.2%  
- **Real-Time Performance:** Yes  

### Confusion Matrix & Metrics
- High precision for `with_mask` and `without_mask`
- Improved classification using the third class

### ROC-AUC Scores
- With Mask: **0.98**
- Without Mask: **0.99**
- Mask Worn Incorrectly: **0.91**

---

## 📈 Comparison with Existing Models

| Model | Classes | Accuracy | Real-Time |
|------|--------|----------|-----------|
| MobileNetV2 | 2 | 89.2% | Yes |
| ResNet50 | 2 | 91.3% | No |
| SSD + MobileNet | 2 | 88.7% | Yes |
| **InceptionV3 (Ours)** | **3** | **91.2%** | **Yes** |

---

## 🧪 Environment

- Platform: Kaggle (GPU)
- Libraries:
  - TensorFlow
  - OpenCV
  - NumPy
  - Matplotlib

---

## 🚀 Applications

- Public surveillance systems  
- Workplace & campus monitoring  
- Healthcare and safety enforcement  
- Smart CCTV systems  

---

## 👨‍💻 Team Members

- **Pratik Siramwar**  
- **Shaswat Singh**

---

## 📚 References

- InceptionV3: *Szegedy et al., 2016*  
- OpenCV Face Detection Model  
- PrajnaSB Face Mask Dataset  
- Related research papers on mask detection

---

## 📌 Conclusion

This project demonstrates an efficient and accurate **real-time face mask detection system** with enhanced classification capability.  
By combining **transfer learning** with **OpenCV-based face detection**, the model achieves high accuracy while remaining lightweight and deployable in real-world environments.

---

⭐ If you like this project, give it a star!
