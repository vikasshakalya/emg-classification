<div align="center">

<!-- Banner / Title -->
<h1>🦾 EMG Hand Gesture Classification</h1>

<p><em>Decoding muscle signals into intelligent gesture predictions using classical ML and deep learning — powered by the NinaPro DB5 dataset.</em></p>

<!-- Badges -->
<p>
  <a href="https://github.com/vikasshakalya/emg-classification/blob/main/NinaPro_DB5_Fixed_Final.ipynb">
    <img src="https://img.shields.io/badge/Open%20Notebook-Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Open Notebook"/>
  </a>&nbsp;
  <img src="https://img.shields.io/badge/Best%20Accuracy-96%25-brightgreen?style=for-the-badge" alt="Accuracy"/>
  &nbsp;<img src="https://img.shields.io/badge/Top%20Model-SVM-FF6F00?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Top Model"/>
  &nbsp;<img src="https://img.shields.io/badge/Dataset-NinaPro%20DB5-0288D1?style=for-the-badge" alt="Dataset"/>
  &nbsp;<img src="https://img.shields.io/badge/Language-Python%203-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
</p>

</div>

---

## 📖 Table of Contents

- [Overview](#-overview)
- [How It Works](#-how-it-works)
- [Project Structure](#-project-structure)
- [Signal Processing & Configuration](#%EF%B8%8F-signal-processing--configuration)
- [Feature Engineering](#-feature-engineering)
- [Models & Results](#-models--results)
- [Evaluation Metrics](#-evaluation-metrics)
- [Key Insights](#-key-insights)
- [Real-World Applications](#-real-world-applications)
- [Author](#-author)

---

## 🔍 Overview

Surface electromyography (sEMG) records the electrical activity produced by muscles during contraction. This project builds a **full end-to-end classification pipeline** that transforms 16-channel raw EMG signals from two Myo armbands into confident hand-gesture predictions.

The pipeline was designed to be clean, reproducible, and highly accurate — going from a naive **66 % baseline** all the way to a **96 % top-1 accuracy** through careful signal processing and feature engineering.

> 📓 Everything is implemented in a single, well-documented Jupyter notebook: [`NinaPro_DB5_Fixed_Final.ipynb`](https://github.com/vikasshakalya/emg-classification/blob/main/NinaPro_DB5_Fixed_Final.ipynb)

---

## ⚙️ How It Works

```mermaid
flowchart LR
    A["⚡ Raw EMG\n(16 channels, 200 Hz)"] --> B["🧹 Band-pass Filter\n20 – 90 Hz"]
    B --> C["🪟 Sliding Window\n200 samples, step 25"]
    C --> D["📊 Feature Extraction\n192 features / window"]
    D --> E["🤖 ML / DL Models\nSVM · RF · KNN · CNN · LSTM"]
    E --> F["📈 Evaluation\nAccuracy · F1 · CV"]
    F --> G["🎯 Gesture Prediction"]
```

---

## 📂 Project Structure

```
emg-classification/
├── NinaPro_DB5_Fixed_Final.ipynb   # ⭐ Complete pipeline (data → models → results)
└── README.md
```

The notebook is self-contained and structured into clearly labelled sections:

| Section | Contents |
|---------|----------|
| **1 – Setup** | Library imports & global configuration |
| **2 – Data Loading** | CSV upload & label reconstruction |
| **3 – EDA** | Class distributions & signal visualisations |
| **4 – Preprocessing** | Band-pass filtering & sliding windows |
| **5 – Feature Engineering** | 10 time/frequency domain features × 16 channels |
| **6 – ML Models** | SVM, Random Forest, KNN, LDA |
| **7 – DL Models** | CNN, LSTM, CNN-LSTM |
| **8 – Evaluation** | Confusion matrices, F1, 10-fold CV |

---

## 🛠️ Signal Processing & Configuration

```yaml
Dataset       : NinaPro DB5 — Subject 1 (Exercises E1, E2, E3)
EMG Channels  : 16  (two Myo armbands)
Sampling Rate : 200 Hz
Band-pass     : 20 – 90 Hz  (Butterworth, order 4)
Window Size   : 200 samples  →  1 second of signal
Step Size     : 25 samples   →  87.5 % overlap
```

> **Why 87.5 % overlap?**  
> Reducing the step from 100 → 25 samples generates 4× more training windows from the same recording, which proved to be the single biggest driver of accuracy improvement.

---

## 📊 Feature Engineering

Ten time- and frequency-domain descriptors are computed **per channel per window**, yielding a compact but highly informative feature vector:

| # | Feature | Domain |
|---|---------|--------|
| 1 | Mean Absolute Value (MAV) | Time |
| 2 | Root Mean Square (RMS) | Time |
| 3 | Variance | Time |
| 4 | Zero Crossing Rate | Time |
| 5 | Waveform Length | Time |
| 6 | Skewness | Time |
| 7 | Kurtosis | Time |
| 8 | Mean Frequency | Frequency |
| 9 | Median Frequency | Frequency |
| 10 | Peak Power | Frequency |

**10 features × 16 channels = 192-dimensional feature vector per window.**  
This compression — from 3,200 raw values down to 192 descriptors — is what lets classical ML models outperform raw-signal deep learning on this dataset.

---

## 🤖 Models & Results

### Machine Learning

| Model | Accuracy |
|-------|----------|
| **SVM (RBF kernel)** ⭐ | **~96 %** |
| Random Forest | ~96 % |
| LDA | ~91 % |
| KNN | ~88 % |

### Deep Learning (trained on raw windowed signals)

| Model | Accuracy |
|-------|----------|
| CNN | ~92 % |
| CNN-LSTM | ~89 % |
| LSTM | ~85 % |

```diff
+ SVM / Random Forest  → ~96 %   ✅  Best overall
+ CNN                  → ~92 %   ✅  Best deep learning
- LSTM                 → ~85 %   ⚠️  Underperforms on small dataset
```

---

## 📏 Evaluation Metrics

| Metric | Purpose |
|--------|---------|
| **Accuracy** | Overall classification correctness |
| **Macro F1 Score** | Balance between precision and recall across all classes |
| **Confusion Matrix** | Per-class error analysis |
| **10-Fold Cross-Validation** | Robust estimate of generalisation |

---

## 💡 Key Insights

- 📈 **Accuracy jumped from 66 % → 96 %** — almost entirely through preprocessing and feature engineering, not by switching models.
- 🪟 **Sliding window step size matters enormously** — going from step 100 to step 25 was the single highest-impact change.
- 🔬 **Feature engineering beats raw deep learning** when data volume is limited; 192 hand-crafted features gave SVM an edge over end-to-end CNNs.
- ⚡ **Band-pass filtering is non-negotiable** — without it, low-frequency motion artefacts and high-frequency noise severely degrade performance.
- 🏆 **Classical ML is not dead** — SVM with a well-crafted feature set matched or surpassed every deep learning model tested here.

---

## 🌍 Real-World Applications

This kind of pipeline is directly applicable to:

- 🦾 **Prosthetic hand control** — real-time gesture decoding for upper-limb amputees
- 🖥️ **Gesture-based HCI** — touchless interfaces for AR/VR and accessibility tools
- 🏥 **Rehabilitation monitoring** — tracking muscle recovery after injury or stroke
- 🤖 **Assistive robotics** — muscle-driven control of robotic arms and exoskeletons
- 🔬 **Clinical neuromuscular research** — objective biomarkers for motor disorders

---

## 👨‍💻 Author

<div align="center">

**Vikas Shakalya**  
*AI Researcher · Founder @ Shakalya International*

<a href="https://github.com/vikasshakalya">
  <img src="https://img.shields.io/badge/GitHub-vikasshakalya-181717?style=for-the-badge&logo=github"/>
</a>

</div>

---

<div align="center">

*If this project helped you, a ⭐ star goes a long way — thank you!*

</div>
