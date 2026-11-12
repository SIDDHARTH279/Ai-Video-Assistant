# 🎬 AI Video Assistant

An AI-powered application that transforms YouTube videos and local audio/video recordings into structured, searchable knowledge.

AI Video Assistant helps you understand long videos and meetings without watching or listening to the entire recording. It automatically generates transcripts, summarizes content, extracts important information, and allows you to ask questions about the video using Retrieval-Augmented Generation (RAG).

## ✨ Features

- 🎥 **YouTube Video Processing:** Process videos directly using YouTube URLs.
- 📁 **Local File Support:** Upload local audio and video recordings.
- 🎙️ **Audio Transcription:** Convert speech into text using AI-powered speech recognition.
- 📝 **AI Summarization:** Generate meaningful summaries of long recordings.
- 📌 **Title Generation:** Automatically generate relevant titles.
- ✅ **Action Item Extraction:** Identify important tasks and follow-up activities.
- 🔑 **Key Decision Extraction:** Extract important decisions from conversations.
- ❓ **Open Questions:** Identify unresolved questions and discussion points.
- 💬 **Chat with Videos:** Ask questions and get contextual answers using RAG.

## 🏗️ Architecture

The application follows an end-to-end AI processing pipeline:

```text
       YouTube URL / Local Media
                  |
                  v
          Audio Processing
                  |
                  v
          Speech Transcription
                  |
                  v
             Transcript
                  |
                  v
           LLM Processing
                  |
          +-------+-------+
          |       |       |
          v       v       v
       Summary  Actions Decisions
                  |
                  v
            Text Chunking
                  |
                  v
             Embeddings
                  |
                  v
             Vector Store
                  |
                  v
           Similarity Search
                  |
                  v
           Context Retrieval
                  |
                  v
              LLM Chain
                  |
                  v
             AI Chatbot
```

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core development |
| Streamlit | User interface |
| LangChain | LLM orchestration |
| LangChain LCEL | Building AI processing chains |
| LLM API | Summarization and question answering |
| Speech-to-Text Model | Audio transcription |
| HuggingFace | Text embeddings |
| ChromaDB | Vector storage |
| FFmpeg | Audio/video processing |
| yt-dlp | YouTube media processing |

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/SIDDHARTH279/Ai-Video-Assistant.git

cd Ai-Video-Assistant
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it:

**Windows:**
```bash
venv\Scripts\activate
```

**Linux / macOS:**
```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file in the project root and add the API credentials required by your configured providers.

```env
# Add your required API keys here
```

Never upload your `.env` file or expose API credentials on GitHub.

### 5. Install FFmpeg

FFmpeg is required for audio/video processing.

**Windows:**
```bash
winget install Gyan.FFmpeg
```

Verify the installation:

```bash
ffmpeg -version
```

## 🚀 Run the Application

Start the Streamlit application:

```bash
streamlit run app.py
```

Open the local URL displayed in your terminal.

## 📖 How to Use

1. Launch the application.
2. Provide a YouTube URL or upload a local recording.
3. Start the processing pipeline.
4. Wait for transcription and AI analysis.
5. Explore the generated transcript and summary.
6. Review extracted action items, decisions and open questions.
7. Ask questions through the chat interface.

## 🧠 Key GenAI Concepts Implemented

- **LLM Integration:** Using large language models for intelligent text generation.
- **LangChain:** Managing LLM interactions and processing workflows.
- **LCEL:** Composing reusable chains using LangChain Expression Language.
- **Text Embeddings:** Converting textual information into numerical representations.
- **Vector Databases:** Storing and retrieving semantically relevant information.
- **RAG:** Grounding AI responses in the actual video transcript.
- **Semantic Search:** Retrieving relevant transcript chunks based on user queries.

## 🔮 Future Improvements

- Speaker identification and diarization.
- Timestamp-based transcript navigation.
- Export summaries as PDF reports.
- Support for additional languages.
- Persistent chat history.
- Improved retrieval accuracy and evaluation.

## 🤝 Contributions

Suggestions, feedback and contributions are always welcome!

Feel free to fork this repository and submit a pull request.

---

**Built with Python, LangChain and Generative AI.** 🚀

If you find this project useful, consider giving it a ⭐!
