# EmpathyBot: Sentiment-Driven Voice Chat

EmpathyBot is a sentiment-aware conversational system that accepts text or voice input, identifies the emotional context of the user's message, and generates an empathetic response.

The project combines Retrieval-Augmented Generation (RAG) with few-shot prompting. Relevant examples are retrieved from a FAISS vector database and incorporated into the prompt provided to the google/flan-t5-large language model. This allows the system to generate responses that are informed by semantically similar examples and adapted to the detected emotion.

The application supports both text-based and voice-based interaction through a Streamlit interface.

---

## 🚀 Features
- Emotion detection (anger, joy, optimism, sadness)
- Retrieval-Augmented Generation using semantic similarity search
- Few-shot prompt construction using retrieved examples
- Response generation with google/flan-t5-large
- Sentence embeddings using sentence-transformers/all-MiniLM-L6-v2
- FAISS vector database for efficient similarity search
- Text and voice input support
- Speech-to-text conversion using Wav2Vec2
- Text-to-speech response generation using gTTS
- Streamlit web app interface

---
## System Workflow

The chatbot processes each interaction through the following stages:

 1. User Input
The user interacts with the system by providing either:
- A text message, or
- A voice recording.


2. Speech-to-Text (Optional)
If the input is a voice recording, it is converted into text using a **Wav2Vec2-based Automatic Speech Recognition (ASR)** model.


 3. Emotion Detection
The transcribed or typed text is analyzed using an emotion classification model to identify the user's emotional state (e.g., happiness, sadness, anger, fear, etc.).


 4. Embedding Generation
The user message is converted into a dense vector representation using the **all-MiniLM-L6-v2** sentence embedding model.


 5. Semantic Retrieval
The generated embedding is used to search a **FAISS** vector database, retrieving the most semantically similar examples to the user's message.


 6. Few-Shot Prompt Construction
The system constructs a few-shot prompt by combining:
- The retrieved similar examples,
- The detected emotion, and
- The current user message.

This provides contextual guidance for the language model.


 7. Response Generation
The constructed prompt is passed to **google/flan-t5-large**, which generates an empathetic and contextually appropriate response.


 8. Voice Output (Optional)
If voice output is enabled, the generated response is converted into speech using **gTTS (Google Text-to-Speech)**.


# Workflow Diagram

```text
          User Input
      (Text or Voice)
                │
                ▼
     Speech-to-Text (Wav2Vec2)
        (Voice only)
                │
                ▼
        Emotion Detection
                │
                ▼
      Embedding Generation
      (all-MiniLM-L6-v2)
                │
                ▼
       Semantic Retrieval
            (FAISS)
                │
                ▼
   Few-Shot Prompt Construction
                │
                ▼
      Response Generation
     (google/flan-t5-large)
                │
                ▼
   Voice Output (Optional)
            (gTTS)
```

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
```
---

## Technologies Used
* Python
* Streamlit
* Hugging Face Transformers
* Sentence Transformers
* FLAN-T5
* Wav2Vec2
* FAISS
* gTTS
* PyTorch
* Pandas
* NumPy

---
## Acknowledgments

This project uses open-source models, datasets, and libraries provided by Hugging Face, Google, Meta AI, the Sentence Transformers project, and the broader Python machine-learning community.
