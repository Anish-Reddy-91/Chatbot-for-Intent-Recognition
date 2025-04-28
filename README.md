# Chatbot for Intent Recognition
This repository contains Python scripts for building and deploying a chatbot that recognizes user intents and responds appropriately using an LSTM-based neural network. The projects include a Flask-based web application and a Streamlit-based interface, both powered by the same trained model.
## Projects Overview
1. **Flask-Based Chatbot Web Application**
   - Implements a chatbot using a Sequential Keras model with an Embedding layer (16 dimensions), LSTM (32 units), and Dense layers for multi-class intent classification.
   - Processes user inputs from a JSON dataset (`intents.json`) using `Tokenizer` and `LabelEncoder`, with padded sequences for uniform input length.
   - Deploys via Flask with a styled HTML interface, hosted publicly using `pyngrok`. Supports real-time user-bot interaction with AJAX-based message handling.
2. **Streamlit-Based Chatbot Interface**
   - Utilizes the same LSTM model for intent recognition, trained on `intents.json` with 200 epochs for high accuracy.
   - Provides a simple Streamlit UI for user input and bot responses, ideal for quick testing and deployment.
   - Features a conversational loop for command-line testing, with an option to quit, ensuring flexibility in interaction modes.
## Compatible Datasets
- **Custom Intent JSON**: The scripts use `intents.json` with a structure of intents, patterns, and responses. Create your own JSON file with similar format (e.g., `{"intents": [{"tag": "greeting", "patterns": ["hi", "hello"], "responses": ["Hello!", "Hi there!"]}]}`).
- **ChatterBot Corpus**: Available on [GitHub](https://github.com/gunthercox/chatterbot-corpus). Adapt the YAML files to JSON format for intent-based training.
- **ATIS Dataset**: Available on [Kaggle](https://www.kaggle.com/datasets/hassanamin/atis-airlinetravelinformationsystem). Convert to JSON format for intent classification tasks.
## Dependencies
- Python 3.11.0
- TensorFlow, NumPy, Scikit-learn, Flask, Streamlit, pyngrok
## Instructions
- Install dependencies:
  ```bash
  pip install tensorflow numpy scikit-learn flask streamlit pyngrok
  ```
- Place `intents.json` in the project directory.
- For Flask app:
   - Set up pyngrok with an auth token (replace "insert_ngrok_auth_token_here" in app.py with your token).
   - Run:
  ```bash
  python app.py
  ```
   - Access the public URL provided by pyngrok.
- For Streamlit app:
   - Run:
  ```bash
  streamlit run streamlit_chatbot.py
  ```
- Update the dataset path in the scripts if using alternative datasets.
## Notes
- The model is trained for 200 epochs to ensure robust intent recognition; adjust epochs for larger datasets.
- Save `tokenizer.pickle` and `label_encoder.pickle` for consistent preprocessing in deployment.
- Ensure pyngrok auth token is configured for Flask public hosting.
- The chatbot supports extensible intents by modifying `intents.json`.
