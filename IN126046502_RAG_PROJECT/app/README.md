📘 Dynamic RAG-Based Customer Support Assistant

A dynamic AI-powered customer support system built using **LangGraph + RAG**, where users can upload PDFs at runtime and query them using an intelligent workflow-based assistant.
Each session is isolated, meaning the system only uses the documents uploaded by the user.

🚀 Features

📄 **Dynamic PDF Uploads**
  Upload one or multiple PDFs during runtime.

🔒 **Session Isolation**
  Each user session has its own ChromaDB collection.

🔁 **LangGraph Workflow**
  Structured pipeline:
  `Input → Route → Retrieve → Evaluate → Generate / Clarify / Escalate`

🧠 **Context-Aware Answers**
  Responses are generated only from uploaded documents.

⚠️ **Fallback Protection**
  Prevents hallucinations when data is not available.

🧑‍💻 **Human-in-the-Loop (HITL)**
  Escalates unclear or sensitive queries to a reviewer.

💻 **Streamlit UI**
  Simple interface for upload and chat.


## 📁 Project Structure
project_root/
├── app/
│ ├── main.py
│ ├── config.py
│ ├── graph/
│ ├── rag/
│ ├── llm/
│ ├── hitl/
│ ├── ui/
│ └── utils/
├── chroma_db/
├── .env
├── requirements.txt
└── README.md

## Setup & Run
1 **Install Requirements:**
pip install -r requirements.txt
2 **Set Environment Variables:** Copy .env.example to .env and assign your GROQ_API_KEY and LANGCHAIN_API_KEY:
cp .env.example .env
3 **Start the Application:** Run the Streamlit wrapper via main script:
python app/main.py
Or directly:

streamlit run app/ui/streamlit_app.py


## 🔄 Workflow Example ##
1. Upload PDF
User uploads document
System creates session-based vector DB
2. Ask Valid Question

Example: “What is the PTO policy?”

Retrieve → Evaluate → Generate
Returns accurate answer with context
3. Vague Question

Example: “Hi, I need help”

Routed to clarification node
System asks for more details
4. Outside Context Question

Example: “Who won the World Cup?”

No relevant data found
System returns fallback response
5. Escalation Case

Example: Billing/legal complaint

Routed to HITL system
Sent for human review
