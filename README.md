# Production-grade-advance-RAG-with-LangGraph-Guardrails-LLM-Gateway-Evals-GCP
Production-Grade Advance RAG with LangGraph, GCP, and Groq

**System Architecture**

<img width="680" height="890" alt="image" src="https://github.com/user-attachments/assets/fe280066-c0cb-4d4f-8077-7b9bb3f540c0" />

This project is a production-grade, enterprise-level, scalable Retrieval-Augmented Generation (RAG) platform built using LangGraph, LangChain, and Google Cloud Platform (GCP). The system is designed to deliver highly accurate, context-aware, secure, and reliable AI responses by intelligently distinguishing between meaningful enterprise knowledge (“True Data”) and irrelevant or noisy information.

# The platform combines:
Multi-Agent AI orchestration
History-aware planning
Semantic retrieval and re-ranking
LLM gateways
Guardrails and evaluation frameworks
Cloud-native scalable infrastructure
Observability and tracing
Infrastructure as Code (IaC)

This architecture demonstrates how modern enterprise AI systems are designed for real-world production environments with scalability, reliability, security, and governance in mind.

User Query
    ↓
Streamlit Chat UI / Evaluation UI
    ↓
FastAPI API Layer
    ↓
NeMo Guardrails (Safety & Validation)
    ↓
LangGraph Multi-Agent Workflow
    ├── Planner Agent
    ├── Retriever Agent
    ├── Responder Agent
    └── MemorySaver
    ↓
Retriever Pipeline
    ├── Qdrant Vector Search
    ├── FlashRank Re-ranking
    └── Context Selection
    ↓
LLM Gateway (Portkey)
    ├── Llama 3.3 70B (Primary)
    └── Llama 3.1 8B (Fallback)
    ↓
Final AI Response
    ↓
Evaluation + Observability + Logging

# End-to-End Flow

**User Interaction**
Users interact through the Streamlit Chat UI or Evaluation Dashboard.

**API & Safety Layer**
Requests are routed through FastAPI, where NeMo Guardrails validates prompts, filters unsafe inputs, and enforces security policies.

**LangGraph Multi-Agent Orchestration**
The query enters the LangGraph workflow:
**Planner Agent** analyzes intent and decides the execution path.
**Retriever Agent** fetches relevant enterprise knowledge.
**Responder Agent** generates the final contextual answer.
**MemorySaver** maintains conversation history for context-aware interactions.

**Retrieval & Re-ranking**
Documents are retrieved from Qdrant Vector DB using embeddings and then re-ranked using FlashRank to remove noisy or irrelevant data.

**LLM Gateway & Response Generation**
Portkey Gateway routes requests to the appropriate LLM:
**Primary: Llama 3.3 70B**
**Fallback: Llama 3.1 8B**

**Observability & Evaluation**
LangSmith tracks agent workflows and prompt traces.
Logfire monitors logs and API traces.
RAGAS evaluates retrieval quality, faithfulness, and response accuracy.

**Cloud Deployment & Infrastructure**
The entire system is containerized using Docker and deployed on GCP Cloud Run with CI/CD via Cloud Build, infrastructure provisioning through Terraform, and secure networking using VPC Connector.
