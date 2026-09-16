# 📧 Email & SMS Spam Detector

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-MultinomialNB-orange.svg)](https://scikit-learn.org/)
[![GUI](https://img.shields.io/badge/GUI-Tkinter-brightgreen.svg)]()
[![Voice](https://img.shields.io/badge/Audio-SAPI.SpVoice-blueviolet.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)]()

An interactive Machine Learning desktop application and notebook workflow that classifies text messages and emails as **Spam** or **Ham (Legitimate)** with **97.85% test accuracy**. Built using Natural Language Processing (NLP), **Multinomial Naive Bayes**, a lightweight **Tkinter GUI**, and **text-to-speech audio feedback** via Windows SAPI.

---

## 📌 Project Overview

This project implements an end-to-end NLP pipeline for SMS/Email spam classification based on the classic SMS Spam Collection dataset (`spam.csv`). In addition to model training and evaluation, the project includes:
- Serialization with `pickle` for model reusability.
- A functional desktop graphical user interface built with Python's built-in `tkinter`.
- An integrated auditory feedback system powered by `win32com.client` (Windows Speech API / `SAPI.SpVoice`) that speaks the prediction out loud.

---

## 🚀 Key Features

- **Data Preprocessing & Cleaning**:
  - Automatically handles multi-encoding CSV files (`latin-1`).
  - Eliminates extraneous unlabelled columns (`Unnamed: 2`, `Unnamed: 3`, `Unnamed: 4`).
  - Encodes target labels (`ham -> 0`, `spam -> 1`).
- **Feature Extraction**:
  - Uses `CountVectorizer` to tokenize and convert raw text messages into a bag-of-words matrix containing **8,672 vocabulary features**.
- **High-Accuracy Classification**:
  - Employs **Multinomial Naive Bayes (`MultinomialNB`)**, well-suited for discrete word-frequency text distributions.
  - Achieves **~97.85% accuracy** on an 80/20 train-test split (`random_state=42`).
- **Interactive Tkinter Desktop GUI**:
  - User-friendly message input field with immediate visual output.
- **Text-to-Speech Output**:
  - Uses Windows SAPI (`win32com.client.Dispatch("SAPI.SpVoice")`) to announce classification results vocally in real time.

---

## 📊 Dataset & Model Architecture

### Pipeline Breakdown
```
Raw Message Input ──▶ CountVectorizer (Bag-of-Words: 8,672 features)
                             │
                             ▼
                 Multinomial Naive Bayes (MultinomialNB)
                             │
                             ▼
              Prediction [0: Ham | 1: Spam]
                    /                 \
                   ▼                   ▼
           Tkinter Desktop GUI    Voice Feedback (SAPI)
```

### Dataset Statistics
- **Total Samples:** 5,572 messages
- **Training Samples:** 4,457 (80%)
- **Test Samples:** 1,115 (20%)
- **Vocabulary Size:** 8,672 terms
- **Test Accuracy:** **97.85%**

---

## 🛠️ Tech Stack & Dependencies

| Category | Tools / Libraries |
| :--- | :--- |
| **Language** | Python 3.8+ |
| **Data Manipulation** | `pandas`, `numpy` |
| **Machine Learning & NLP** | `scikit-learn` (`CountVectorizer`, `MultinomialNB`, `train_test_split`) |
| **Model Persistence** | `pickle` |
| **Desktop GUI** | `tkinter` |
| **Audio / Speech** | `pywin32` (`win32com.client`) |

---

## ⚙️ Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/dynhsn/Spam-Detector.git
cd Spam-Detector
```

### 2. Create and Activate a Virtual Environment (Optional but Recommended)
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux / macOS
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install pandas numpy scikit-learn pywin32
```

*(Note: `tkinter` and `pickle` are included with standard Python installations.)*

---

## 📂 Project Structure

```text
Spam-Detector/
├── Spam Detector.ipynb     # Jupyter Notebook containing EDA, training, and GUI
├── spam.csv                # SMS Spam dataset (latin-1 encoded)
├── spam.pkl                # Serialized trained MultinomialNB model
└── README.md               # Project documentation
```

---

## 🖥️ Running the Application

### Option A: Via Jupyter Notebook
Open the notebook and run all cells sequentially:
```bash
jupyter notebook "Spam Detector.ipynb"
```
The final cell launches the Tkinter desktop GUI dialog.

### Option B: Quick CLI / Python Inference Snippet
```python
import pickle
from sklearn.feature_extraction.text import CountVectorizer

# Load trained model
with open('spam.pkl', 'rb') as f:
    model = pickle.load(f)

# Predict sample message
msg = ["Congratulations! You have won a $1,000 Walmart Gift Card. Click here to claim."]
# Note: Transform using the fitted CountVectorizer instance
# pred = model.predict(vectorizer.transform(msg))
```

---

## 💡 Example Predictions

| Sample Text | Predicted Class | Action Taken |
| :--- | :---: | :--- |
| *"Ok lar... Joking wif u oni..."* | **Ham (0)** | Console: `This is not a Spam mail`<br>Voice: "This is not a Spam mail" |
| *"Free entry in 2 a wkly comp to win FA Cup final tkts..."* | **Spam (1)** | Console: `This is a Spam mail`<br>Voice: "This is a Spam mail" |
| *"You Won 500$"* | **Spam (1)** | Console: `This is a Spam mail`<br>Voice: "This is a Spam mail" |

---

## ⚠️ Notes for Non-Windows Platforms

The text-to-speech functionality in this notebook utilizes Windows-specific SAPI COM components (`win32com.client`). If you are running on macOS or Linux:
- You can substitute `win32com` with a cross-platform library like `pyttsx3`:
  ```python
  import pyttsx3
  engine = pyttsx3.init()
  def speak(text):
      engine.say(text)
      engine.runAndWait()
  ```

---

## 👤 Author

**Dayyan Hasan**
- **GitHub:** [@dynhsn](https://github.com/dynhsn)
- **LinkedIn:** [Dayyan Hasan](https://www.linkedin.com/in/dayyanhasan57)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).