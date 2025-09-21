# EmpathyBot: Sentiment-Driven Voice Chat

A sentiment-driven chatbot that detects emotions from user text or voice input and responds with empathetic voice feedback.

---

## 🚀 Features
- Emotion detection (anger, joy, optimism, sadness)
- Text and voice input (speech-to-text with Wav2Vec2)
- Text-to-speech (gTTS)
- Semantic search using embeddings + FAISS
- Streamlit web app interface

---

## 📂 Project Structure
```bash
sentiment-voice-chatbot/
│
├── app.py                     # Main Streamlit app entry point
│
├── modules/                   # Core functionality modules
│   ├── __init__.py
│   ├── DataPreprocessor.py   # Load & clean dataset
│   ├── Embedder.py          # Create embeddings + FAISS index
│   ├── emotion_detection.py   # Classify emotions
│   ├── speech_to_text.py      # Convert voice to text (Wav2Vec2)
│   └── text_to_speech.py      # Convert text to speech (gTTS)
│
├── notebooks/                 # Experiments and prototyping
│   └── Sentiment_Driven_Chat.ipynb
│
├── requirements.txt           # Python dependencies
└── README.md                  # Project documentation
