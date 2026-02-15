# 🤖 n8n AI Agent with Gemini + Vector Store (RAG Workflow)

## 📌 Overview
This project contains an **n8n workflow** that builds a conversational AI Agent using:

- Google Gemini Chat Model  
- In-memory vector database (RAG-style retrieval)  
- Conversation memory buffer  
- Gemini Search Tool (web/context lookup)  

The workflow also includes a **data ingestion pipeline** to insert company knowledge into the vector store, enabling the agent to answer questions about the company.

---

## 🧠 Architecture

The workflow is divided into **two logical systems**:

### **System 1 - Chat AI Agent with Vector DB**
Handles user chat requests and generates responses.

**Flow:**

Chat Trigger → AI Agent → Tools

**Tools used:**
- Gemini Chat Model (LLM)  
- Memory Buffer Window  
- Vector Store (retrieve company knowledge)  
- Gemini Search Tool (optional external context)

This allows the agent to:
- Answer company-related questions
- Maintain conversation context
- Retrieve relevant stored knowledge
- Search externally when needed

---

### **System 2 - Store Information in Vector DB**
Loads company information and stores embeddings for retrieval.

**Flow:**

Manual Trigger → Edit Fields → Data Loader → Embeddings → Vector Store

The `Edit Fields` node contains company information such as:

- Company description
- Products/services
- Contact emails
- Return policy

This text is converted into embeddings and inserted into the in-memory vector database.

---

## ✨ Features

- ✅ Conversational AI agent inside n8n  
- ✅ Retrieval-Augmented Generation (RAG) approach  
- ✅ Gemini embeddings for semantic search  
- ✅ Built-in chat memory  
- ✅ External search tool integration  
- ✅ Simple ingestion pipeline for knowledge updates  

---

## 🛠️ Requirements

- n8n (latest version recommended)
- Google Gemini API key
- Gemini Search API credentials (if using search tool)

---

## 🔑 Setup Instructions

### 1️⃣ Import the Workflow

1. Open n8n  
2. Go to **Workflows → Import**  
3. Upload the provided JSON file  
4. Save the workflow  

---

### 2️⃣ Configure Credentials

Update the following nodes with your credentials:

- **Google Gemini Chat Model**
- **Embeddings Google Gemini**
- **Gemini Search Tool**

---

### 3️⃣ Load Knowledge into Vector Store

1. Open the workflow  
2. Run **Manual Trigger** once  
3. This inserts the company information into the vector DB  

> ⚠️ You must do this before chatting with the agent.

---

### 4️⃣ Start Chatting with the Agent

1. Activate the workflow  
2. Send a message to the **Chat Trigger webhook**  
3. Ask questions such as:
     - What does Acme Inc. sell?
     - What is the return policy?
     - How can I contact support?

---

## 📂 Workflow Components

| Node | Purpose |
|------|--------|
| Chat Trigger | Receives user messages |
| AI Agent | Core orchestration of tools and reasoning |
| Gemini Chat Model | Language model for responses |
| Memory Buffer | Maintains conversation context |
| Vector Store (Retrieve) | Finds relevant stored knowledge |
| Gemini Embeddings | Converts text into embeddings |
| Gemini Search Tool | Optional external search |
| Edit Fields | Holds company knowledge text |
| Manual Trigger | Starts knowledge ingestion |

---

## 🧩 How It Works (RAG Concept)

1. Company data is embedded and stored in vector DB  
2. User sends a chat message  
3. Agent searches vector DB for relevant info  
4. Retrieved context is passed to Gemini  
5. Gemini generates the final answer  

---

## 🚀 Possible Improvements

- Replace in-memory vector DB with Pinecone, Supabase, or Qdrant  
- Add Google Sheets or database ingestion  
- Connect to Slack / Telegram / Web UI  
- Add structured output parser  
- Store chat history in database  

---

## 📜 License

Use freely for learning and experimentation.

---

## 🙌 Credits

Built using:

- **n8n**
- **Google Gemini API**
- **LangChain nodes for n8n**

---

## 📬 Contact
If you'd like to discuss this project or my experience:  
📧 **Email:** sujipn@gmail.com  
🔗 **LinkedIn:** http://linkedin.com/in/sujitha-pathmanathan
