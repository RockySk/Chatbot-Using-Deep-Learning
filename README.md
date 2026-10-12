# Chatbot Using Deep Learning

A simple web-based chatbot built with Python, Flask, NLTK, and TensorFlow/Keras. The project trains a neural network on custom intents and exposes the model through a browser chat interface.

## Project Overview

This project demonstrates how to:

- create a custom chatbot intent dataset in JSON
- preprocess text using NLTK tokenization and lemmatization
- train a deep learning model with Keras
- serve the chatbot through a Flask web app
- interact with the model in a browser UI

## Features

- Chat interface built with Flask templates
- Intent-based response generation
- TensorFlow/Keras neural network for classification
- NLTK-based text preprocessing
- Model and vocabulary files persisted as `.h5`, `.pkl` artifacts

## Project Structure

```text
Chatbot-Using-Deep-Learning/
├── app.py                 # Flask chatbot backend and route handlers
├── train.py               # Model training script
├── intents.json           # Chatbot intents and response data
├── chatbot_model.h5       # Pre-trained Keras model
├── words.pkl              # Vocabulary used in prediction
├── classes.pkl            # Intent classes used in prediction
├── requirements.txt       # Python dependencies
├── static/
│   └── style.css          # Frontend styling
├── templates/
│   └── index.html         # Chat UI
└── README.md              # Project documentation
```

## Requirements

- Python 3.9 or 3.10 recommended
- pip
- Virtual environment support

## Installation

1. Open a terminal in the project folder.

2. Create and activate a virtual environment:

```bash
python -m venv .venv
```

On Windows:

```bash
.venv\Scripts\activate
```

On macOS/Linux:

```bash
source .venv/bin/activate
```

3. Upgrade pip and install dependencies:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

4. Download the required NLTK data (this is usually triggered during training, but it is also safe to run manually):

```python
import nltk
nltk.download("punkt")
nltk.download("wordnet")
nltk.download("omw-1.4")
```

## Training the Model

If the model files are missing or you want to retrain the chatbot, run:

```bash
python train.py
```

This will:

- read the intents from `intents.json`
- build the vocabulary and classes
- train the deep learning model
- save the model to `chatbot_model.h5`
- generate `words.pkl` and `classes.pkl`

> The repository already includes a trained model, so you may not need to retrain unless you modify the intents or want to improve the model.

## Running the App

Start the Flask server:

```bash
python app.py
```

Then open your browser and go to:

```text
http://127.0.0.1:5000/
```

You can then chat with the bot in the browser.

## How the App Works

- `app.py` loads the trained model and utilities.
- `predict_class()` converts user input to a bag-of-words vector and predicts the best matching intent.
- `getResponse()` chooses a response from the matching intent in `intents.json`.
- The browser UI sends text to `/get` and displays the bot reply.

## Customizing the Chatbot

You can improve or expand the bot by editing `intents.json`.

Each intent has the following structure:

```json
{
  "tag": "greetings",
  "patterns": ["hi", "hello", "hey"],
  "responses": ["Hello! How can I help you?"],
  "context": [""]
}
```

To update the bot:

1. add or edit intents in `intents.json`
2. retrain with `python train.py`
3. restart the Flask app

## Troubleshooting

### Module not found errors

If you get import errors, make sure your virtual environment is active and dependencies are installed:

```bash
pip install -r requirements.txt
```

### TensorFlow/Keras compatibility issues

This project is based on older Keras/TensorFlow patterns. If you are using a very new Python version, consider using Python 3.9 or 3.10 for best compatibility.

### NLTK data not found

Run this in Python:

```python
import nltk
nltk.download("punkt")
nltk.download("wordnet")
nltk.download("omw-1.4")
```

## License

This project is intended for learning and educational use.

## Author

Sourabh Kulkarni
