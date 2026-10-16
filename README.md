# Badminton Knowledge Assistant using LangChain

## Project Overview

This project implements a Badminton Knowledge Assistant using LangChain, Retrieval-Augmented Generation (RAG), and an LLM-powered agent.

The assistant answers questions about badminton using a PDF knowledge base. It can also perform mathematical calculations, provide the current date, and maintain conversation history across separate conversation threads.

## Objectives

- Build a RAG pipeline using a badminton PDF document.
- Generate embeddings and store document chunks in ChromaDB.
- Retrieve relevant information to answer user questions.
- Create an agent that automatically selects the appropriate tool.
- Implement exactly three tools.
- Demonstrate conversation memory and separate conversation threads.

## Technologies Used

- Python
- Google Colab
- LangChain
- Google Gemini API
- Hugging Face Sentence Transformers
- ChromaDB
- LangGraph
- PyPDF

## System Architecture

1. **Document Loading:** Load the badminton knowledge base from a PDF using PyPDFLoader.
2. **Text Splitting:** Divide the document into smaller chunks using RecursiveCharacterTextSplitter.
3. **Embedding Generation:** Convert text chunks into vector embeddings using `sentence-transformers/all-MiniLM-L6-v2`.
4. **Vector Database:** Store embeddings in ChromaDB.
5. **Retrieval:** Retrieve relevant document chunks based on the user's query.
6. **RAG Pipeline:** Use retrieved context to generate grounded answers with the Gemini LLM.
7. **Tool Creation:** Integrate the RAG pipeline with two additional tools.
8. **Agent Creation:** Allow the agent to select the appropriate tool automatically.
9. **Conversation Memory:** Use LangGraph's InMemorySaver to maintain conversation state using thread IDs.

## Tools Implemented

### 1. RAG Tool
Answers badminton-related questions using the provided PDF knowledge base.

### 2. Calculator Tool
Evaluates mathematical expressions and returns the result.

### 3. Current Date Tool
Returns the current date.

The agent selects the appropriate tool based on the user's question.

## Conversation Memory

The project demonstrates conversation memory using separate thread IDs.

- `conversation_2`: Remembers information shared within that conversation.
- `conversation_3`: Maintains a separate conversation history.
- `conversation_1`: Demonstrates tool usage within a conversation.

This helps demonstrate how conversation state can be isolated between different threads.

**Note:** InMemorySaver stores memory in runtime memory. The conversation state is not permanently saved when the runtime is restarted.

## Setup and Execution

### 1. Open the Notebook

Open `Agentic_AI.ipynb` in Google Colab.

### 2. Install Dependencies

Run the installation cell in the notebook.

### 3. Upload the Knowledge Base

Upload the badminton PDF to Google Drive and update the PDF path in the notebook if required.

### 4. Configure the API Key

Add your Google Gemini API key to Google Colab Secrets with the name `Key`.

Never publish your API key in the notebook, source code, or GitHub repository.

### 5. Run the Notebook

Execute the notebook cells in order to load the document, create embeddings, initialize the vector database, configure the LLM, create the tools and agent, and demonstrate memory.

A valid API key and available API quota are required for LLM-dependent operations.

## Example Questions

- What is a smash in badminton?
- What is a high serve in badminton?
- What is 125 multiplied by 48?
- What is today's date?
- My name is Shravani. What is my name?
- My name is Priya. What is my name in this conversation?

## Project Structure

```text
Badminton-Knowledge-Assistant/
├── 28_Assignment_5.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

The badminton PDF is a separate input file and is not included in this repository.

## Future Improvements

- Add support for more sports knowledge bases.
- Improve retrieval quality and response evaluation.
- Add persistent conversation storage.
- Develop a user-friendly interface.
- Add robust error handling for API quota limits.

## Conclusion

This project demonstrates the integration of RAG, vector search, LLM-based tool selection, and conversation memory to create a domain-specific knowledge assistant using LangChain.
