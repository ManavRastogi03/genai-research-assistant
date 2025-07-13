# 🧠 Task: Smart Assistant for Research Summarization

---

## 🎯 Objective

Build an AI-powered assistant that can read and deeply understand user-uploaded documents (PDF or TXT). The assistant should support both free-form question answering and logical reasoning, ensuring all answers are grounded in the source content.

---

## 📚 Problem Statement

Reading lengthy documents such as research papers or technical manuals is time-consuming. Simple summarizers or keyword search tools lack comprehension. This tool bridges that gap by enabling users to:

- Ask intelligent questions requiring inference
- Receive contextual answers with source justification
- Be tested with logic-based questions auto-generated from the document

---

## ✅ Functional Requirements

### 1. 📄 Document Upload
- Accepts `.pdf` and `.txt` files
- Assumes input is structured English (e.g., reports, research papers)

### 2. 💬 Interaction Modes

#### a. Ask Anything
- Free-form user questions
- Assistant answers using contextual evidence from the document

#### b. Challenge Me
- Generates 3 logic/inference-based questions
- Accepts user answers
- Evaluates and provides feedback + justification

### 3. 📌 Contextual Understanding
- All responses are grounded in uploaded content
- No hallucination or fabricated responses
- Each answer includes reference (e.g., “Supported by paragraph 3 of section 1”)

### 4. 🧠 Auto Summary (≤150 words)
- After upload, a concise summary of the document is generated instantly

### 5. 🌐 Application Architecture
- Web-based interface running locally
- Frontend: Streamlit
- Backend: FastAPI
- Focus on seamless UX and smooth flow

---

## ✨ Bonus Features (Implemented)

- 🔁 Memory Handling – Supports follow-up questions with context awareness
- 🔍 Answer Highlighting – Shows source snippet backing each answer

---

## 🧱 Architecture / Reasoning Flow

```mermaid
graph TD
    A[📄 Upload PDF/TXT] --> B[Text Extractor]
    B --> C[Text Cleaning + Chunking]
    C --> D[Vector Index (FAISS)]
    C --> E[Auto Summary Generator (LLM)]
    D --> F{User Mode}
    F -->|Ask Anything| G[Retriever → LLM → Answer + Justification]
    F -->|Challenge Me| H[Question Generator → Answer Evaluation → Feedback]
```

- Uses Retriever-Augmented Generation (RAG)
- Top-k relevant chunks passed to the model to reduce hallucinations

---

## 🛠 Tech Stack

| Layer         | Technology         |
|---------------|--------------------|
| UI            | Streamlit          |
| Backend       | FastAPI            |
| LLM           | Gemini API / GPT-4 |
| Chunking      | LangChain          |
| Vector Search | FAISS / ChromaDB   |
| Parsing       | PyMuPDF            |
| Memory        | LangChain Memory   |

---

## 🧪 Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/ManavRastogi03/genai-research-assistant.git
cd genai-research-assistant
```

### 2️⃣ Create a Virtual Environment

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Add Your API Key

Create a `.env` file:

```env
GEMINI_API_KEY=your_gemini_api_key_here
```

### 5️⃣ Run the App

```bash
# Start backend
cd backend
uvicorn main:app --reload

# Start frontend
cd ../fronted
streamlit run app.py
```

---

## 📁 Project Structure

```
genai-research-assistant/
├── backend/
│   ├── main.py
│   ├── config.py
│   ├── document_processor.py
│   ├── llm_service.py
│   ├── api_models.py
│   └── embeddings.py
│
├── fronted/
│   └── app.py
│
├── utils/
│   └── text_utils.py
│
├── static/
│   └── style.css
│
├── data/
│   └── uploads/
│
├── .env.example
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🎓 Example Use Case

- Upload a PDF research paper.
- Read the auto-generated summary.
- Ask: **"What were the challenges discussed in section 2?"**
- Get a cited answer like:  
  _“As per paragraph 2 of Section 2...”_
- Try the “Challenge Me” quiz to test your understanding.

---

## 📊 Evaluation Criteria

| Category                            | Weight |
|-------------------------------------|--------|
| ✅ Response Quality + Justification  | 30%    |
| 🧠 Challenge Me Functionality        | 20%    |
| 🎨 UI/UX & Smooth Flow               | 15%    |
| 🧹 Code Structure & Documentation    | 15%    |
| 🌟 Creativity / Bonus Features       | 10%    |
| 🚫 Minimal Hallucination / Context   | 10%    |

---

---

## 📜 License

MIT © [ManavRastogi03](https://github.com/ManavRastogi03)
