# my-ai-chat-rag-workflow

my-ai-chat-rag-workflow/
├── workflows/
│   └── ai-chat-rag-workflow.json
├── images/
│   ├── ai-agent-demo-1.png
│   └── ai-agent-demo-2.png
├── README.md

# 🤖 AI Chat + RAG Workflow using n8n, OpenAI, Supabase & PostgreSQL

This repository contains an [n8n](https://n8n.io) workflow that powers a **chat-based Retrieval-Augmented Generation (RAG)** system using:

- 🔗 **Supabase Vector Store** (for document embedding & retrieval)
- 🧠 **OpenAI Chat Model**
- 🗃️ **PostgreSQL** (for chat memory)
- 📂 **Google Drive** (for ingesting documents)
- 💬 **Chat Trigger & AI Agent** (for interaction)

---

## 📸 Screenshots

| Chat-triggered AI response | Vector DB setup |
|----------------------------|------------------|
| ![Chat Trigger](images/ai-agent-demo-1.png) | ![Supabase Vector](images/ai-agent-demo-2.png) |

---

## 🧩 How It Works

### 🔄 Flow Overview

1. **User sends a message** via a chat interface → triggers `chatTrigger`.
2. The message is passed to the **AI Agent**, powered by an **OpenAI Chat model**.
3. The agent:
   - Searches Supabase vector DB using document embeddings.
   - Pulls memory context from PostgreSQL.
   - Optionally loads & embeds new documents from Google Drive.
4. Returns intelligent responses using RAG.

---

### 🧱 Nodes Involved

- `When chat message received` – Listens for input via webhook.
- `AI Agent` – Core LangChain agent orchestration.
- `OpenAI Chat Model` – Powered by GPT (e.g., gpt-4.1-mini).
- `Supabase Vector Store` – Used for both inserting and retrieving embeddings.
- `Postgres Chat Memory` – Stores memory per session.
- `Google Drive` – Downloads documents (PDFs or text) for ingestion.
- `Default Data Loader` & `Embeddings OpenAI` – Used to parse & embed new documents.

---

## 📂 File Info

| File | Description |
|------|-------------|
| `workflows/ai-chat-rag-workflow.json` | The exported n8n workflow |
| `images/ai-agent-demo-1.png` | Screenshot of chat interaction |
| `images/ai-agent-demo-2.png` | Screenshot of Supabase DB with embeddings |

---

## 🚀 Getting Started

### 1. Prerequisites

- n8n desktop or cloud instance
- Supabase project
- PostgreSQL DB
- Google Drive access
- OpenAI API Key

### 2. Import the Workflow

1. Open your [n8n instance](https://n8n.io).
2. Go to **Workflows** → **Import** → Upload `ai-chat-rag-workflow.json`.
3. Configure credentials for:
   - Google Drive
   - Supabase
   - OpenAI
   - PostgreSQL

### 3. Test It

- Send a message through the webhook URL shown in `When chat message received`.
- The agent will respond intelligently using embedded data from your documents.

---

## 🛠️ Customize

- Replace the Google Drive file URL with your own.
- Update Supabase table or RPC function names.
- Adjust prompts or output formatting in the AI Agent.
- Add filters to refine what documents are embedded.

---

## 📜 License

MIT License

---

## 🙌 Acknowledgments

Built with ❤️ using:
- [n8n](https://n8n.io)
- [LangChain](https://www.langchain.com/)
- [OpenAI](https://platform.openai.com/)
- [Supabase](https://supabase.com/)
