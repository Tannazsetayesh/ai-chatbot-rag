
# Anika IRS AI Chatbot

This project demonstrates the development of a Retrieval-Augmented Generation (RAG) chatbot capable of answering questions using authoritative IRS Internal Revenue Manual (IRM) documents. The notebook implements the full RAG pipeline—from data collection and preprocessing to embedding, indexing, and large language model (LLM)-based response generation.

## Project Objectives

- Acquire unstructured HTML content from the IRS website
- Clean, parse, and intelligently chunk text data
- Embed and index content for semantic search
- Build a conversational AI assistant that retrieves relevant context and generates accurate answers with inline citations
- Deploy and interact with the system in a Google Colab notebook environment

## Key Features

- Crawler to download HTML documents (IRS IRM)
- HTML parsing using BeautifulSoup
- Intelligent text chunking using sentence boundaries
- Embedding generation using Vertex AI or other models
- Pinecone integration for vector search
- LLM-based query answering via Gemini or text-bison
- Interactive UI using ipywidgets

## Pipeline Overview

1. **Data Acquisition**
   - Download HTML files from `https://www.irs.gov/irm/part1`
   - Store files in a Google Cloud Storage (GCS) bucket

2. **Data Preparation**
   - Parse HTML and extract clean text
   - Chunk documents by sentence or heading while preserving context
   - Enrich with metadata (e.g., title, chunk index, source)

3. **Embedding and Indexing**
   - Use Vertex AI or any supported embedding model to convert chunks into vectors
   - Index chunks into Pinecone with metadata for retrieval

4. **Query Processing**
   - Embed user query
   - Retrieve top-k relevant chunks from Pinecone
   - Feed chunks and query into an LLLM for grounded response generation

5. **Interface**
   - Use ipywidgets in Google Colab to build a simple UI
   - Display real-time query responses directly in notebook

## Technologies Used

- Python
- Google Cloud Storage
- Vertex AI (Gemini, text-bison)
- Pinecone Vector Database
- BeautifulSoup
- LangChain
- ipywidgets
- tqdm

## Setup Instructions

1. **Environment**
   - Run the notebook in Google Colab (recommended)
   - Install dependencies

2. **Google Cloud**
   - Enable Vertex AI and Storage APIs
   - Set up a GCS bucket for storing downloaded HTML
   - Use the Vertex AI Python SDK for model access and embedding

3. **Pinecone**
   - Set up a Pinecone project
   - Create an index and note the environment and API key

4. **Notebook Execution**
   - Download HTML files
   - Parse and chunk documents
   - Generate embeddings and upsert to Pinecone
   - Ask queries using the RAG chatbot interface

## Testing

The notebook includes a test suite of IRS-specific queries to validate:
- Embedding quality
- Retrieval accuracy
- LLM response quality

These tests ensure that the chatbot can correctly find and cite relevant context from the indexed IRS documentation.

## Limitations

- Only public documents are supported
- Gemini model must be accessed through supported Vertex AI APIs

## Author

Tannaz Setayesh  
Email: tanaz.setayesh@gmail.com

## License

This project is licensed under the MIT License. See the LICENSE file for details.
