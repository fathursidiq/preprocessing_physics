# preprocessing_physics
# 🫀 ECG Wave Segmentation with Physics-Informed Preprocessing

This repository explores multiple physics-based preprocessing techniques—**Euler Differentiation**, **Hilbert Transform**, and **Gauss-Legendre Integration**—to enhance the segmentation of ECG waveforms (P, QRS, and T) using an LSTM model.

---

## 🔬 Overview

Electrocardiogram (ECG) signals contain three primary waveforms:

- **P-wave**: low-frequency, low-amplitude
- **QRS-complex**: sharp, high-frequency
- **T-wave**: smooth, moderate amplitude

Each wave is preprocessed using a tailored mathematical method to match its physical characteristics before being segmented using an LSTM model.

---

## ⚙️ Preprocessing Methods

| Method               | Description                                         | Best for          |
|----------------------|-----------------------------------------------------|-------------------|
| Euler Differentiation| Highlights sharp slope changes                      | QRS-complex       |
| Hilbert Transform    | Enhances amplitude & phase info (envelope)         | P & T waves       |
| Gauss-Legendre       | Smooth integration, retains morphology             | All segments      |
| High-pass Filtering  | Removes baseline drift                             | All               |

---

## 🧪 Model & Training

- Architecture: 2-layer LSTM
- Input: Preprocessed 1D ECG signal
- Output: Predicted wave labels (P, QRS, T)
- Evaluation Metrics: Accuracy, Test Loss, Inference Time

<p align="center">
  <img src="results/loss_curves.png" width="600"/>
  <br><i>Figure: Loss convergence across preprocessing techniques</i>
</p>

---

## 🕒 Runtime Comparison

| Method         | CPU Time (ms) | GPU Memory (MB) |
|----------------|---------------|------------------|
| No Preprocessing | 40.2 ms     | 110 MB          |
| Euler            | 41.5 ms     | 112 MB          |
| Hilbert          | 43.0 ms     | 115 MB          |
| Gauss-Legendre   | 45.0 ms     | 120 MB          |

---

## 📁 File Guide

| File | Description |
|------|-------------|
| `src/preprocessing.py` | All signal transformation methods |
| `src/model_lstm.py`    | LSTM-based segmentation model |
| `main.py`              | Run complete pipeline (preprocess → segment → plot) |

---

## 📦 Installation

```bash
git clone https://github.com/username/ecg-segmentation-preprocessing.git
cd ecg-segmentation-preprocessing
pip install -r requirements.txt
