# 🏥 Prescription OCR Classification

Fine-tuning **EfficientNet-B0** to classify 78 medicine names from handwritten medical prescription images.

## 📊 Results

| Metric | Score |
|---|---|
| Val Accuracy | 93.46% |
| Test Accuracy | 85.64% |
| F1 Score (weighted) | 0.8524 |
| Epochs | 13 / 15 (early stopping) |

## 📁 Dataset

[OCR-Processed Handwritten Prescriptions](https://www.kaggle.com/datasets/nadaarfaoui/ocr-processed-handwritten-prescriptions) — 4,680 prescription images across 78 medicine name classes, split into train / val / test sets.

## 🧠 Model

- **Architecture:** EfficientNet-B0 pretrained on ImageNet
- **Head:** replaced final linear layer → 78-class output
- **Optimizer:** AdamW (lr=3e-4, weight_decay=1e-4)
- **Scheduler:** CosineAnnealingLR
- **Loss:** CrossEntropyLoss
- **Early stopping:** patience = 4 epochs

## 🗂️ Project Structure
```
prescription-ocr-classification/
├── notebook.ipynb       # Full training pipeline
├── requirements.txt     # Python dependencies
└── README.md
```

## 🚀 Quick Start
```bash
git clone https://github.com/goktani/prescription-ocr-classification
cd prescription-ocr-classification
pip install -r requirements.txt
```

Then open `notebook.ipynb` and update `DATASET_ROOT` to your local dataset path.

## ⚙️ Configuration

All hyperparameters are defined in **Cell 3** of the notebook:

| Parameter | Value |
|---|---|
| Image size | 224 × 224 |
| Batch size | 32 |
| Learning rate | 3e-4 |
| Epochs | 15 (early stopping) |
| Patience | 4 |

## 🔧 Potential Improvements

- EfficientNet-B2/B3 for higher capacity
- MixUp / CutMix augmentation to reduce val→test gap
- Label smoothing in CrossEntropyLoss
- Test-time augmentation (TTA) at inference

## 📄 License

MIT
