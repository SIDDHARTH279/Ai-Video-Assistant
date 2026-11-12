# 🎬 AI Video Assistant

An AI-powered Video & Meeting Assistant that turns long videos and meeting recordings into meaningful, searchable information.

Simply provide a YouTube URL or a local audio/video file, and the application will transcribe the content, generate summaries, extract action items and key decisions, and let you ask questions about the recording using Retrieval-Augmented Generation (RAG).

## ✨ Features

- **YouTube & Local File Support:** Process YouTube videos and local audio/video recordings.
- **Speech-to-Text:** Transcribe English audio using OpenAI Whisper.
- **Hinglish Support:** Transcribe Hinglish audio and translate it into English using Sarvam AI.
- **AI Summarization:** Generate concise, structured meeting summaries.
- **Title Generation:** Automatically generate meaningful titles from transcripts.
- **Action Item Extraction:** Identify important tasks and follow-up activities.
- **Key Decision Extraction:** Extract important decisions discussed during meetings.
- **Open Questions:** Identify unresolved questions from conversations.
- **Chat with Your Meeting:** Ask questions about your recording and get context-aware answers using RAG.
- **Interactive Dashboard:** Track processing stages and explore results through a Streamlit interface.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core development |
| Streamlit | Frontend and user interface |
| LangChain | LLM orchestration |
| LCEL | Building AI pipelines |
| Mistral AI | Summarization and information extraction |
| OpenAI Whisper | English speech transcription |
| Sarvam AI | Hinglish transcription and translation |
| HuggingFace Embeddings | Text embeddings |
| ChromaDB | Vector database |
| FFmpeg | Audio/video processing |
| Pydub | Audio conversion and chunking |
| yt-dlp | YouTube audio downloading |

## 🏗️ Project Architecture

The application follows a modular processing pipeline:

```text
YouTube URL / Local Audio-Video File
                  |
                  v
          Audio Processing
          (yt-dlp / FFmpeg)
                  |
                  v
            Audio Chunking
                (Pydub)
                  |
                  v
           Speech-to-Text
           /             \
       English          Hinglish
       Whisper           Sarvam AI
           \             /
                  |
                  v
             Transcript
                  |
                  v
          LLM Processing
            (Mistral AI)
                  |
          +-------+-------+
          |       |       |
          v       v       v
        Summary Actions Decisions
                  |
                  v
           Open Questions
                  |
                  v
             RAG Pipeline
                  |
          +-------+-------+
          |               |
      Embeddings       ChromaDB
          |               |
          +-------+-------+
                  |
                  v
           Context Retrieval
                  |
                  v
           Mistral AI + LCEL
                  |
                  v
          Contextual Answers
```

## 📂 Project Structure

```text
AI-Video-Assistant/
│
├── core/
│   ├── transcriber.py       # Speech-to-text processing
│   ├── summarizer.py        # Summary and title generation
│   ├── extractor.py         # Extract action items and decisions
│   ├── rag_engine.py        # RAG pipeline and question answering
│   └── vector_store.py      # Embeddings and ChromaDB operations
│
├── utils/
│   └── audio_processor.py   # Audio downloading and processing
│
├── app.py                   # Streamlit application
├── main.py                  # Main processing pipeline
├── Requirements.txt         # Project dependencies
├── .env                     # API credentials
└── .gitignore
```

## ⚙️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/AkarshVyas/AI-Video-Assistant-.git

cd AI-Video-Assistant-
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate the environment:

**Windows:**
```bash
venv\Scripts\activate
```

**Linux / macOS:**
```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r Requirements.txt
```

### 4. Install FFmpeg

FFmpeg must be installed separately and available in your system PATH.

**Windows (using Chocolatey):**
```bash
choco install ffmpeg
```

Verify installation:

```bash
ffmpeg -version
```

### 5. Configure Environment Variables

Create a `.env` file in the root directory:

```env
MISTRAL_API_KEY=your_mistral_api_key
SARVAM_API_KEY=your_sarvam_api_key

# Optional Whisper configuration
WHISPER_MODEL=small

# Optional Sarvam model configuration
SARVAM_STT_MODEL=saaras:v2.5
```

Get your API credentials:

- Mistral AI: https://console.mistral.ai/
- Sarvam AI: https://dashboard.sarvam.ai/

**Note:** Mistral AI is required for LLM operations. Sarvam AI is required when using Hinglish transcription. English transcription uses the locally running Whisper model.

## 🚀 Run the Application

Start the Streamlit application:

```bash
streamlit run app.py
```

Open the local URL displayed in your terminal (usually `http://localhost:8501`).

## 📖 How to Use

1. Launch the application.
2. Enter a YouTube URL or a local audio/video file path.
3. Select the transcription language (English or Hinglish).
4. Click the **Analyse** button.
5. Wait for the audio processing and AI pipeline to complete.
6. Explore the generated title, summary, transcript, action items, key decisions and open questions.
7. Use the chat interface to ask questions about your recording.

## 🧠 RAG Implementation

The project uses Retrieval-Augmented Generation to enable conversations with meeting transcripts.

The RAG workflow:

1. Split the transcript into smaller text chunks.
2. Generate embeddings using HuggingFace embedding models.
3. Store the embeddings in ChromaDB.
4. Retrieve the four most relevant chunks for a user query.
5. Pass the retrieved context and question to Mistral AI.
6. Generate a contextual answer based on the transcript.

The application also uses LangChain Expression Language (LCEL) to connect the retriever, prompt template, LLM and output parser into a single processing chain.

## 🔮 Future Improvements

- Speaker identification and diarization.
- Timestamp-based transcript navigation.
- Export summaries and reports in PDF format.
- Support for additional languages.
- Persistent conversation history.
- Improved retrieval and answer evaluation.

## 🤝 Contributing

Contributions, suggestions and feedback are welcome!

Feel free to fork the repository and submit a pull request.

## 📄 License

This project is available for learning and experimentation. Check the repository for licensing terms before redistributing or reusing its code.

---

**Built with Python, LangChain and Generative AI.** 🚀
