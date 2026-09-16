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
