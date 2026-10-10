# AirOps Copilot

Interview-ready Agentic AI demo for synthetic airline disruption recovery.

## Stack
React/TypeScript/Vite • FastAPI • LangGraph • Ollama/Azure OpenAI abstraction • PostgreSQL/pgvector • Docker • pytest • Bicep • Azure Container Apps.

## Local quick start
```bash
docker compose up --build
# API: http://localhost:8000/docs
# UI:  http://localhost:5173
```
For a dependency-light demo, the backend also runs with an in-memory repository when `DEMO_MODE=true`.

## Test/evaluation
```bash
cd backend
pytest -q
cd ..
python scripts/generate_test_data.py --scenario standard --seed 42
python scripts/seed_database.py --scenario standard
python evaluation/run_evaluation.py
```

## Azure
See `docs/AZURE_DEPLOYMENT.md`. Deployment uses Bicep and supports Azure OpenAI in the cloud while keeping Ollama for local development. All airline/passenger data is synthetic.

## Scenario names
Use the canonical scenario IDs everywhere: `standard`, `limited_capacity`, and `major_weather`.

## Database seeding
`python scripts/seed_database.py --scenario <scenario>` creates the demo PostgreSQL schema and loads the generated synthetic data plus the recovery policy.
