# 🧠 genai-research-assistant

An AI-powered assistant that intelligently summarizes, queries, and quizzes research documents (PDF/TXT) with contextual understanding using Gemini AI and LangChain.

---

## 🚀 Overview

The `genai-research-assistant` enables users to:

- 📄 Upload structured research or technical documents
- 🧠 Receive an automatic summary (≤150 words)
- 💬 Ask comprehension-based questions
- 🎯 Be challenged with logic-based questions
- 📌 Get grounded answers with in-document references

Designed with clean UX, minimal hallucination, and robust reasoning.

---

## 🛠 Features

- 📄 **Document Upload** – Accepts PDF or TXT files (≤10MB)
- 🧠 **Auto Summarization** – LLM-powered summary on upload
- 💬 **Ask Anything** – Free-form contextual Q&A grounded in the text
- 🎯 **Challenge Me** – Logic/inference-based MCQs with evaluation
- 📌 **Answer Justification** – Cites exact section/snippet from the document
- 🔁 **Memory Handling** *(Bonus)* – Follow-up question awareness
- ✨ **Answer Highlighting** *(Bonus)* – Visual snippet display

---

## 🧱 System Design

```mermaid
graph TD
A[📄 User Uploads Document] --> B[📑 Document Processor]
B --> C[🧹 Cleaner + Text Chunker]
C --> D[📊 FAISS Vector Index]
C --> E[🧠 LLM Summary Generator]
D --> F{Interaction Mode}
F -->|💬 Ask Anything| G[LLM + Context Retriever → Answer + Reference]
F -->|🎯 Challenge Me| H[Question Generator → User Answer → Evaluator]
Embeddings are created from text chunks

Chunks are queried for relevance via semantic search

Only top-k chunks are passed to the LLM to minimize hallucination

📦 Tech Stack
Layer	Technology
UI	Streamlit
Backend	FastAPI
LLM	Gemini API / GPT-4
Chunking	LangChain
Vector Search	FAISS or ChromaDB
PDF Parsing	PyMuPDF
Evaluation	LLM-based scoring

🧪 Getting Started
1️⃣ Clone the Repository
bash
Copy
Edit
git clone https://github.com/ManavRastogi03/genai-research-assistant.git
cd genai-research-assistant
2️⃣ Create & Activate Virtual Environment
bash
Copy
Edit
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
3️⃣ Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt
4️⃣ Add API Key
Create a .env file in the root directory:

env
Copy
Edit
GEMINI_API_KEY=your_gemini_api_key_here
5️⃣ Run the App
bash
Copy
Edit
# Start backend
cd backend
uvicorn main:app --reload

# Start frontend
cd ../fronted
streamlit run app.py
Then open: http://localhost:8501

📁 Folder Layout
arduino
Copy
Edit
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
🎓 Example Use Case
Upload a PDF research paper.

Read the summary instantly.

Ask: "What were the key findings in section 2?"

Receive a grounded answer with citation like:
“As per paragraph 2 of Section 2...”

Use "Challenge Me" mode to test your comprehension.

✅ Evaluation Checklist
Criteria	Weight
📖 Response Accuracy & Justification	30%
🧠 Challenge Me Evaluation Logic	20%
🎨 UI/UX Flow & Simplicity	15%
🧹 Code Quality & Documentation	15%
🌟 Creative / Bonus Features	10%
🚫 Low Hallucination & Context Use	10%

📜 License
MIT © ManavRastogi03