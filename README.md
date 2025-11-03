# XAR-DNN
Official implementation of XAR-DNN: An Explainable and Adversarially Robust Deep Neural Network for IoT Intrusion Detection.
# XAR-DNN: An Explainable and Adversarially Robust Deep Neural Network for IoT Intrusion Detection

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![TensorFlow 2.13+](https://img.shields.io/badge/TensorFlow-2.13%2B-orange)](https://www.tensorflow.org/)

This repository contains the official implementation of **XAR-DNN**, a novel deep learning framework that unifies adversarial robustness and explainable AI (XAI) for trustworthy intrusion detection in IoT and IIoT environments.

> 📄 Paper: [XAR-DNN: An Explainable and Adversarially Robust Deep Neural Network for IoT Intrusion Detection](#) (Under submission to *Elsevier Journal of Information Security and Applications – JISA)

---

 📌 Key Contributions

- Adversarially Robust DNN: Trained with FGSM/PGD adversarial examples (ε = 0.1) to resist white-box attacks.
- Explainable Decisions: Uses SHAP to provide feature-level interpretability.
- Feature Stability Analysis (FSA): A novel metric to quantify reasoning consistency under attack.
- Cross-Dataset Validation: Evaluated on Edge-IIoTset, **NSL-KDD, and CIC-IDS-2018.
- Edge-Deployable: Only 42K parameters; 2.3 ms inference on Raspberry Pi 4.

---

 📊 Performance Summary

| Dataset         | Clean Acc (%) | FGSM (%) | PGD-10 (%) | Macro F1 | FSA (Mean) |
|-----------------|---------------|----------|------------|----------|------------|
| Edge-IIoTset| 95.74         | 95.09    | 93.90      | 0.88     | 0.53       |
| NSL-KDD     | 96.2          | 91.5     | 90.7       | —        | —          |
| CIC-IDS-2018| 94.8          | 89.9     | 88.4       | —        | —          |

All results are averaged over 5 runs with statistical significance confirmed via McNemar’s test (p < 0.05).

---

 🧪 Reproducing Results

 Prerequisites
-numpy
-pandas
-scikit-learn
-tensorflow>=2.10
-shap
-tqdm
-xgboost


Install dependencies:
```bash
pip install -r requirements.txt

Datasets
The framework supports three datasets:
Edge-IIoTset  --  Kaggle
NSL-KDD       --  UNB Official
CIC-IDS-2018  --  Kaggle (Preprocessed)


Code Structure
XAR-DNN-IoT-IDS/
├── README.md                 ← one-line install & citation
├── LICENSE                   ← MIT (open, no hassle)
├── requirements.txt          ← PyTorch + SHAP + friends
├── data/
│   ├── README.md             ← how to get/unpack Edge-IIoTset, etc.
│   └── .gitignore            ← never commit large *.csv
├── src/
│   ├── preprocess.py         ← z-score, label encode, 42 feats
│   ├── model.py              ← XAR-DNN torch code (42 k params)
│   ├── train.py              ← adversarial training loop (FGSM + PGD)
│   ├── explain.py            ← SHAP + FSA calculator
│   └── evaluate.py           ← McNemar, CIs, ROC, F1
├── checkpoints/
│   └── .gitkeep              ← placeholder for *.pt files
├── notebooks/
│   └── quick_demo.ipynb      ← end-to-end on 1k samples
└── CITATION.cff              ← auto-generated citation (GitHub shows it)


🙏 Acknowledgements
Datasets: Edge-IIoTset, NSL-KDD, CIC-IDS-2018
Frameworks: TensorFlow, SHAP, scikit-learn
Computing: NVIDIA Tesla T4 (Kaggle), Raspberry Pi 4 (edge validation)
