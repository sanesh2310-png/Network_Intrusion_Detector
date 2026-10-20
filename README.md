# Network Intrusion Detection using Machine Learning


**Program:** IBM SkillsBuild Cyber Security Bootcamp 2026 (BharatCares)

## Project Description

This project builds machine learning models that classify network connections as **normal** or **attack**. Three models are trained and compared on the KDD Cup 99 network intrusion dataset: Logistic Regression, Decision Tree and Random Forest. The models are evaluated with accuracy, precision, recall and F1-score, and the best model is analysed further with a confusion matrix and feature importance.

## Dataset

- **Name:** KDD Cup 1999 network intrusion dataset (10% subset, "SA" variant)
- **Link:** https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_kddcup99.html
- **Size used:** 100,655 connections, 41 features
- **Labels:** converted to binary (0 = normal, 1 = attack). About 97% of records are normal and 3% are attacks, so the data is imbalanced.
- The dataset is downloaded automatically by scikit-learn the first time the notebook runs, so no manual download is needed (internet access is required once).

## Technologies Used

- Python 3
- pandas, NumPy
- scikit-learn
- matplotlib, seaborn
- Jupyter Notebook / Google Colab

## Project Structure

```
.
├── Deeksha_NetworkIntrusionDetector.ipynb   # main notebook (code and results)
├── requirements.txt                         # Python dependencies
├── Deeksha_ProjectReport.docx               # full project report
└── README.md                                # this file
```

## Setup and Run Instructions

### Option 1: Google Colab (easiest)

1. Open https://colab.research.google.com
2. Go to **File → Upload notebook** and select `Deeksha_NetworkIntrusionDetector.ipynb`.
3. Click **Runtime → Run all**.

All required libraries are already available in Colab.

### Option 2: Run locally

```bash
git clone https://github.com/sanesh2310-png/network-intrusion-detector
cd network-intrusion-detector

python -m venv venv
# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activate

pip install -r requirements.txt
jupyter notebook
```

Open `Deeksha_NetworkIntrusionDetector.ipynb` and choose **Kernel → Restart & Run All**.

## Methodology

1. Load the KDD Cup 99 dataset from scikit-learn and decode the text columns.
2. Convert labels to binary (normal vs attack).
3. Explore the data and check the class balance.
4. Encode the categorical columns (`protocol_type`, `service`, `flag`) with label encoding.
5. Split the data 80/20 with stratification and standardize the features.
6. Train Logistic Regression, Decision Tree and Random Forest models.
7. Evaluate with accuracy, classification report, confusion matrix and feature importance.

## Results

| Model | Accuracy |
|---|---|
| Logistic Regression | 99.94% |
| Decision Tree | 99.98% |
| Random Forest | **99.99%** |

- Test set: 20,131 connections (19,456 normal, 675 attack).
- The Random Forest detected 672 of the 675 attacks (missing 3) with no false alarms, an Attack recall of about 99.6%.
- The most important features were `count` and `srv_count`, followed by `protocol_type`, `src_bytes` and `service`.

## Key Information

- The dataset is highly imbalanced, so accuracy alone can be misleading and recall on the Attack class is the more important measure.
- KDD Cup 99 is an older dataset, so these near-perfect results may not carry over to modern real-world network traffic.
- The project runs entirely offline after the dataset is downloaded once, and needs no API keys or accounts.
