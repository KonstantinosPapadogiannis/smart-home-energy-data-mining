# 🏠 Εξόρυξη Δεδομένων: Ανάλυση Κατανάλωσης Ενέργειας Έξυπνου Σπιτιού

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Εργασία για το μάθημα **Εξόρυξη Δεδομένων** του Χαροκοπείου Πανεπιστημίου (Ιανουάριος 2026).

---

## 📖 Περιγραφή

Αυτό το project εφαρμόζει **τεχνικές εξόρυξης δεδομένων** στο dataset **"Individual Household Electric Power Consumption"** από το UCI Machine Learning Repository. Το σύνολο δεδομένων περιλαμβάνει πάνω από **2 εκατομμύρια μετρήσεις** από ένα νοικοκυριό για σχεδόν **4 χρόνια** (2006-2010).

### 🎯 Στόχοι

- **Προεπεξεργασία** και καθαρισμός πραγματικών δεδομένων ενέργειας
- **Ταξινόμηση**: Εντοπισμός ημερών υψηλής κατανάλωσης
- **Παλινδρόμηση**: Πρόβλεψη κατανάλωσης επόμενης ημέρας
- **Clustering**: Αναγνώριση προφίλ ημερήσιας κατανάλωσης
- **Association Rules**: Ανακάλυψη μοτίβων χρήσης συσκευών
- **Time Series**: Πρόβλεψη χρονοσειρών με ARIMA, Prophet, LSTM

---

## 📂 Δομή Project

```
data_mining/
├── data/
│   ├── df_daily_clean.csv              # Καθαρό ημερήσιο dataset (INCLUDED)
│   └── household_power_consumption.txt # Raw dataset (NOT INCLUDED - πολύ μεγάλο)
├── notebooks/
│   ├── data_preprocessing.ipynb        # Προεπεξεργασία δεδομένων
│   └── modeling.ipynb                  # Όλα τα μοντέλα (Classification, Regression, etc.)
├── report/
│   └── report.md                       # Πλήρης αναφορά με αποτελέσματα
├── results/
│   ├── *.png                           # Όλα τα plots/διαγράμματα
│   └── *.csv                           # Association rules results
├── requirements.txt                    # Python dependencies
├── SETUP_INSTRUCTIONS.md               # 📚 ΑΝΑΛΥΤΙΚΕΣ ΟΔΗΓΙΕΣ ΕΓΚΑΤΑΣΤΑΣΗΣ
├── .gitignore                          # Εξαιρέσεις Git
└── README.md                           # Αυτό το αρχείο
```

---

## 🚀 Γρήγορη Εκκίνηση

### 1️⃣ Clone το Repository

```bash
git clone git@github-konstantinos:KonstantinosPapadogiannis/smart-home-energy-data-mining.git
cd smart-home-energy-data-mining
```

### 2️⃣ Εγκατάσταση

```bash
# Δημιουργία virtual environment
python3 -m venv venv
source venv/bin/activate  # Linux/Mac
# ή
venv\Scripts\activate     # Windows

# Εγκατάσταση dependencies
pip install -r requirements.txt
```

### 3️⃣ Κατέβασμα Raw Dataset (Προαιρετικό)

Το raw dataset δεν περιλαμβάνεται (πολύ μεγάλο). Αν θες να τρέξεις το preprocessing:

1. Κατέβασε από: [UCI Repository](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)
2. Μετακίνησε το `household_power_consumption.txt` στο `data/`

**Εναλλακτικά:** Χρησιμοποίησε απευθείας το `df_daily_clean.csv` που ήδη υπάρχει!

### 4️⃣ Εκτέλεση Notebooks

```bash
jupyter notebook
```

Άνοιξε και τρέξε:
- `notebooks/modeling.ipynb` (κύριο notebook με όλα τα μοντέλα)
- `notebooks/data_preprocessing.ipynb` (προαιρετικό, αν έχεις το raw dataset)

**📚 Για αναλυτικές οδηγίες:** Διάβασε το [SETUP_INSTRUCTIONS.md](SETUP_INSTRUCTIONS.md)

---

## 🔬 Τεχνικές & Μοντέλα

### 1. Classification (Ταξινόμηση)
- **Μοντέλα:** Logistic Regression, Random Forest, Gradient Boosting
- **Στόχος:** Πρόβλεψη ημερών "Υψηλής" vs "Κανονικής" κατανάλωσης
- **Μετρικές:** Accuracy >85%, F1-score, ROC-AUC

### 2. Regression (Παλινδρόμηση)
- **Μοντέλα:** Ridge Regression, Random Forest Regressor
- **Στόχος:** Πρόβλεψη κατανάλωσης επόμενης ημέρας (kWh)
- **Μετρικές:** MAE, RMSE, R²

### 3. Clustering (Ομαδοποίηση)
- **Αλγόριθμος:** K-Means (k=5)
- **Στόχος:** Εντοπισμός προφίλ κατανάλωσης (καθημερινές, Σ/Κ, ανώμαλες)
- **Μετρικές:** Silhouette Score, Davies-Bouldin Index

### 4. Association Rules (Κανόνες Συσχέτισης)
- **Αλγόριθμος:** FP-Growth
- **Στόχος:** Ανακάλυψη μοτίβων χρήσης συσκευών
- **Μετρικές:** Support, Confidence, Lift

### 5. Time Series (Χρονοσειρές - Προαιρετικό)
- **Μοντέλα:** Baseline (Persistence), ARIMA, Prophet, **LSTM** ⭐
- **Στόχος:** Πρόβλεψη ημερήσιας κατανάλωσης (one-step ahead)
- **Μετρικές:** RMSE, MAPE
- **Αποτέλεσμα:** Το **LSTM** ξεπέρασε όλα τα άλλα μοντέλα!

---

## 📊 Αποτελέσματα (Highlights)

### Classification
- **Best Model:** Gradient Boosting Classifier
- **Test Accuracy:** ~99%
- **F1-Score:** ~0.99
- **ROC-AUC:** ~0.99

### Regression
- **Best Model:** Random Forest Regressor
- **Test RMSE:** 5.59 kWh
- **Test MAE:** 4.10 kWh
- **R²:** 0.47

### Clustering
- **k=5 clusters** με ξεκάθαρα προφίλ:
  - Χαμηλές καθημερινές
  - Μεσαίες καθημερινές
  - Υψηλές Σαββατοκύριακα
  - Πολύ υψηλές (ανώμαλες)

### Time Series
- **Best Model:** LSTM 🏆
- **Test RMSE:** 5.61 kWh (18% βελτίωση vs baseline!)
- **Test MAPE:** 17.89%

---

## 🛠️ Τεχνολογίες

- **Python 3.12**
- **Jupyter Notebook**
- **Pandas, NumPy** (data manipulation)
- **Scikit-learn** (ML models)
- **Statsmodels** (ARIMA)
- **Prophet** (Facebook time series)
- **TensorFlow/Keras** (LSTM)
- **Matplotlib, Seaborn** (visualizations)
- **mlxtend** (Association rules)

---

## 👥 Ομάδα

- **Κωνσταντίνος Παπαδόγιαννης** (2022141)
- **Anastasiia Zervas** (it2022119)

**Πανεπιστήμιο:** Χαροκόπειο Πανεπιστήμιο  
**Μάθημα:** Εξόρυξη Δεδομένων  
**Ημερομηνία:** Ιανουάριος 2026

---

## 📄 Άδεια

MIT License - Ελεύθερο για εκπαιδευτική χρήση.

---

## 🔗 Χρήσιμοι Σύνδεσμοι

- [UCI Dataset](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)
- [Full Report](report/report.md)
- [Setup Instructions](SETUP_INSTRUCTIONS.md)

---

## 📞 Επικοινωνία

Για ερωτήσεις ή προβλήματα, δημιούργησε ένα **Issue** στο GitHub.

---

⭐ Αν σου φάνηκε χρήσιμο, κάνε ένα **star** στο repository!