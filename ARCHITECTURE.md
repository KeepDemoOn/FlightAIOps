# Architecture

```text
React Dashboard -> FastAPI -> LangGraph workflow
                         |-> Flight/Weather/Passenger/Capacity tools
                         |-> Policy RAG (PostgreSQL + pgvector)
                         |-> deterministic recovery validator
                         |-> human approval -> simulated execution -> audit log

Local LLM: Ollama       Cloud LLM: Azure OpenAI
Local DB: PostgreSQL+pgvector    Cloud DB: Azure PostgreSQL Flexible Server
```

The LLM explains and synthesizes; authoritative facts and critical arithmetic come from tools and deterministic Python logic. Execution is blocked until approval.
