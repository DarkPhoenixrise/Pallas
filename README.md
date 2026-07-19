# Pallas

> **A Critic-Oriented Retrieval-Augmented Generation (RAG) Assistant built for grounded, reliable document question answering.**

Pallas is a fully local Retrieval-Augmented Generation (RAG) chatbot that combines semantic retrieval with an LLM-powered critic to improve response quality.

Unlike traditional RAG systems that generate an answer once, Pallas evaluates every response using a second reasoning stage. If the critic detects missing information, weak grounding, or hallucinations, the system regenerates the answer before presenting it to the user.

The entire pipeline runs locally using open-source models through Ollama.

---

## Features

- Fully local execution
- PDF document ingestion
- Recursive text chunking
- Semantic embeddings
- ChromaDB vector database
- Query expansion
- Top-K semantic retrieval
- Context-aware answer generation
- LLM-based Critic Module
- Iterative self-correction
- Grounded document-based responses
- Configurable retrieval pipeline

---

## Architecture

```
                 PDF Documents
                       │
                       ▼
             Text Extraction (PyMuPDF)
                       │
                       ▼
              Recursive Chunking
                       │
                       ▼
        Embeddings (nomic-embed-text)
                       │
                       ▼
                 ChromaDB Storage
                       │
──────────────────────────────────────────────
                       │
                  User Question
                       │
                       ▼
               Query Expansion
                       │
                       ▼
               Semantic Embedding
                       │
                       ▼
             Top-K Context Retrieval
                       │
                       ▼
               Context Construction
                       │
                       ▼
            Llama 3 Answer Generator
                       │
                       ▼
              Critic Evaluation
                 │            │
                 │            │
              Accept      Regenerate
                 │            │
                 └──────► Final Answer
```

---

## Tech Stack

| Component | Technology |
|------------|------------|
| Language | Python |
| LLM | Llama 3 |
| Embedding Model | nomic-embed-text |
| Vector Database | ChromaDB |
| PDF Parsing | PyMuPDF |
| Runtime | Ollama |
| Retrieval | Semantic Search |
| Critic | LLM Self-Evaluation |

---

## Installation

Clone the repository.

```bash
git clone https://github.com/yourusername/Pallas.git

cd Pallas
```

Install dependencies.

```bash
pip install -r requirements.txt
```

Install the required Ollama models.

```bash
ollama pull llama3
ollama pull nomic-embed-text
```

---

## Running

Index documents.

```bash
python src/ingest.py
```

Start the chatbot.

```bash
python src/pipeline.py
```

---

## Example

### Question

```
What are the Fundamental Duties mentioned in the Constitution?
```

### Response

```
(a) To abide by the Constitution...

(b) To cherish the ideals...

...

Source:
Chapter 4
Chunk 87
```

---

## Performance

| Metric | Measured Performance |
|---------|---------------------|
| Retrieval Accuracy | 85% |
| Groundedness | High |
| Hallucination Reduction | Significant |
| Response Consistency | Improved |

---

## Future Improvements

- Hybrid Retrieval (BM25 + Dense Retrieval)
- Cross-Encoder Reranking
- Web Search Integration
- Streaming Responses
- Multi-document Collections
- Multi-modal Document Support
- Citation Highlighting
- Agentic Retrieval
- Quantized Local Models

---

## Repository Structure

```
src/
├── chunker.py
├── critic.py
├── embeddings.py
├── generator.py
├── ingest.py
├── pipeline.py
├── retriever.py
└── utils.py
```

---

## License

Released under the MIT License.
