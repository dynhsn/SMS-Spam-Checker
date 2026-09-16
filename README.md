# SMS Spam Checker

A machine learning-based SMS spam detection application built with Python, Scikit-learn, and Tkinter. This project classifies incoming messages as spam or legitimate (ham) using the Multinomial Naive Bayes algorithm.

## Overview

This project implements an end-to-end SMS spam detection system that:
- Loads the SMS Spam Collection Dataset (5,572 messages)
- Preprocesses and vectorizes text using CountVectorizer
- Trains a Multinomial Naive Bayes classifier
- Provides a graphical user interface (GUI) for real-time prediction
- Includes text-to-speech functionality to announce results

## Features

- ✅ **Data Preprocessing**: Handles dirty CSV data with empty columns
- ✅ **Text Vectorization**: Uses CountVectorizer for feature extraction
- ✅ **Machine Learning Model**: Multinomial Naive Bayes classifier
- ✅ **High Accuracy**: Achieves ~97.85% test accuracy
- ✅ **GUI Application**: Tkinter-based desktop application for user interaction
- ✅ **Text-to-Speech**: Windows SAPI integration for audio feedback
- ✅ **Model Persistence**: Saves and loads the trained model using pickle

## Technologies Used

- Python 3.12.7
- Scikit-learn (Machine Learning)
- Pandas & NumPy (Data manipulation)
- Tkinter (GUI)
- win32com.client (Text-to-speech)
- Pickle (Model serialization)

## Dataset

Uses the SMS Spam Collection Dataset containing 5,572 labeled SMS messages. The dataset includes two columns:
- `class`: Label indicating 'ham' (legitimate) or 'spam'
- `message`: The SMS text content

## Project Structure

SMS-Spam-Checker/ ├── Spam Detector.ipynb # Main Jupyter notebook ├── README.md # Project documentation ├── spam.csv # Dataset file ├── spam.pkl # Trained model (generated) └── requirements.txt # Dependencies


## Installation

### Prerequisites
- Python 3.7 or higher
- Windows OS (for text-to-speech feature)

### Dependencies

```txt
pandas>=1.0.0
numpy>=1.19.0
scikit-learn>=0.24.0
Install with:

bash

Copy
pip install pandas numpy scikit-learn
How It Works
1. Data Loading and Cleaning
python

Copy
data = pd.read_csv("spam.csv", encoding="latin-1")
data.drop(['Unnamed: 2', 'Unnamed: 3', 'Unnamed: 4'], axis=1, inplace=True)
2. Label Encoding
python

Copy
data['class'] = data['class'].map({'ham': 0, 'spam': 1})
3. Text Vectorization
python

Copy
cv = CountVectorizer()
X = cv.fit_transform(data['message'])
4. Train-Test Split
python

Copy
x_train, x_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
5. Model Training
python

Copy
model = MultinomialNB()
model.fit(x_train, y_train)
6. Evaluation
Test Accuracy: 97.85%
7. GUI Application
The application provides:

Text input field for user messages
"Click" button to trigger prediction
Visual and audio feedback on results
Usage
Running the Notebook
bash

Copy
jupyter notebook Spam\ Detector.ipynb
Using the GUI Application
After running the notebook to train and save the model:

python

Copy
# The GUI will automatically launch
python Spam\ Detector.ipynb  # or run cells 60-64
Enter your message in the input field and click "Click" to get prediction results. The application will:

Display text output: "This is a Spam mail" or "This is not a Spam mail"
Speak the result using Windows text-to-speech
Example Usage
python

Copy
msg = "You Won 500$"
result(msg)  # Output: "This is a Spam mail"
Model Performance
Accuracy
97.85%
Training Samples
4,457
Test Samples
1,115
Features
8,672
Key Code Components
Prediction Function
python

Copy
def result(msg):
    data = [msg]
    vect = cv.transform(data).toarray()
    my_prediction = model1.predict(vect)
    if my_prediction[0] == 1:
        speak("This is a Spam mail")
        print("This is a Spam mail")
    else:
        speak("This is not a Spam mail")
        print("This is not a Spam mail")
Text-to-Speech Integration
python

Copy
from win32com.client import Dispatch

def speak(text):
    speak = Dispatch("SAPI.SpVoice")
    speak.Speak(text)
Limitations
Windows Only: Text-to-speech feature requires Windows OS (win32com.client)
Single Algorithm: Only uses Multinomial Naive Bayes (could extend to other models)
No Advanced Preprocessing: Doesn't include stopword removal, stemming, or lemmatization
Desktop Application: GUI is Windows-based and not web-deployable
Future Enhancements

 Add more ML algorithms (Logistic Regression, SVM, Random Forest)

 Implement advanced text preprocessing (NLTK/SpaCy)

 Create a web interface using Flask/Django

 Add cross-platform text-to-speech support

 Include confusion matrix and classification report visualizations

 Deploy as a mobile application
Acknowledgments
Dataset: SMS Spam Collection Dataset (UCI Machine Learning Repository)
Framework: Scikit-learn for machine learning
GUI: Tkinter for desktop interface
License
MIT License - Feel free to use and modify for learning purposes.

Note: This project is designed for educational purposes. For production use, consider implementing additional security measures, comprehensive testing, and deployment infrastructure.
