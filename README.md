<!-- ================= HERO SECTION ================= -->

<h1 align="center">🧠 EMG Hand Gesture Classification</h1>

<p align="center">
  <b>From Muscle Signals → Intelligent Predictions</b><br>
  <i>Machine Learning • Deep Learning • Biomedical Signal Processing</i>
</p>

<p align="center">
  <a href="https://github.com/vikasshakalya/emg-classification/blob/main/NinaPro_DB5_Fixed_Final.ipynb">
    <img src="https://img.shields.io/badge/🚀%20Open%20Notebook-Jupyter-blue?style=for-the-badge"/>
  </a>
  <img src="https://img.shields.io/badge/Accuracy-96%25-success?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Model-SVM%20Best-orange?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Data-NinaPro-green?style=for-the-badge"/>
</p>

---

## ✨ What is this?

> A **complete EMG signal classification system** that converts raw muscle activity into hand gesture predictions using optimized signal processing, feature engineering, and ML/DL models.

---

## 🧩 Visual Pipeline

```mermaid
flowchart LR
A[⚡ Raw EMG Signals] --> B[🧹 Signal Filtering]
B --> C[🪟 Sliding Window]
C --> D[📊 Feature Engineering]
D --> E[🧠 ML / DL Models]
E --> F[📈 Evaluation]
F --> G[🎯 Gesture Prediction]
```

---

## 📂 Minimal Project Structure

```bash
📁 EMG-Classifier
 ┣ 📜 NinaPro_DB5_Fixed_Final.ipynb   ⭐ Full Implementation
 ┗ 📜 README.md
```

---

## ⚙️ Core Configuration

```yaml
Dataset: NinaPro DB5
Channels: 16 EMG sensors
Sampling Rate: 200 Hz
Window Size: 200 samples (1 sec)
Step Size: 25  → 87.5% overlap
```

---

## 📊 Feature Engineering (The Game Changer)

```python
# Each window → 192 features
features = [
  MAV, RMS, Variance,
  ZeroCrossings, WaveformLength,
  Skewness, Kurtosis,
  MeanFrequency, MedianFrequency, PeakPower
]
```

✨ Converts **raw 3200 values → 192 powerful features**
✨ Enables ML models to learn efficiently

---

## 🤖 Models Implemented

<div align="center">

| Type                | Models                         |
| ------------------- | ------------------------------ |
| 🔹 Machine Learning | SVM ⭐, Random Forest, KNN, LDA |
| 🔹 Deep Learning    | CNN, LSTM, CNN-LSTM            |

</div>

---

## 📈 Performance Snapshot

```diff
+ SVM            → ~96% Accuracy  🚀
+ Random Forest  → ~96% Accuracy
+ CNN            → ~92% Accuracy
- LSTM           → ~85% Accuracy
```

---

## 📊 Evaluation Metrics

```python
Accuracy         # Overall performance
F1 Score         # Precision vs Recall balance
Confusion Matrix # Class-wise analysis
Cross Validation # 10-Fold reliability
```

---

## 🧠 Key Insights

```bash
✔ Accuracy improved from 66% → 96%
✔ Step size optimization (100 → 25) boosted performance
✔ Feature engineering > Deep Learning (for small data)
✔ Classical ML outperformed DL
✔ Signal preprocessing is critical
```

---

## 🔗 Explore the Notebook

<p align="center">
  <a href="https://github.com/vikasshakalya/emg-classification/blob/main/NinaPro_DB5_Fixed_Final.ipynb">
    <img src="https://img.shields.io/badge/Open%20Full%20Project-Click%20Here-blue?style=for-the-badge"/>
  </a>
</p>

---

## 🌍 Real-World Applications

```bash
✔ Prosthetic Hand Control
✔ Gesture-Based Interfaces
✔ Assistive AI Systems
✔ Biomedical Signal Analysis
```

---

## 👨‍💻 Author

<p align="center">
  <b>Vikas Shakalya</b><br>
  AI Researcher • Founder @ Shakalya International
</p>

---

## ⭐ Show Some Support

<p align="center">
  <img src="https://img.shields.io/badge/⭐%20Star%20This%20Repo-If%20You%20Liked%20It-yellow?style=for-the-badge"/>
</p>

---
