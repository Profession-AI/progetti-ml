# Sistema multi-agente per la due diligence di startup

## Contesto aziendale

Helix Ventures è un fondo di venture capital early-stage che valuta ogni mese decine di startup.
La due diligence iniziale (analisi di mercato, team, prodotto, finanza) richiede oggi 2-3 giorni di
lavoro per analista. L'azienda vuole automatizzare questa fase con un sistema multi-agente che,
dato il nome e il sito di una startup, produca un memo strutturato in meno di mezz'ora.

## Obiettivi del progetto

1. Progettare il sistema partendo dai requisiti: definire 4-6 agenti (es. Coordinator, Market
   Analyst, Tech Reviewer, Team Analyst, Memo Writer) con ruolo, goal, backstory, tool e
   perimetro di responsabilità.
2. Implementare il sistema due volte, una con CrewAI e una con LangGraph, applicando un
   pattern di orchestrazione Supervisor con almeno un punto di parallelismo.
3. Definire uno stato condiviso tipizzato con Pydantic, gestendo almeno un conflitto di scrittura
   con una reducer function.
4. Esporre almeno un tool tramite un MCP Server custom implementato in Python.
5. Gestire errori con retry, fallback e graceful degradation (il memo va prodotto anche se
   manca una sezione).
6. Esporre il sistema come API FastAPI con POST /due_diligence e GET /health, containerizzata
   con Docker.
7. Tracciare le esecuzioni con Langfuse o LangSmith e includere uno screenshot di una traccia.

## Deliverable

Notebook Colab con: documento di design, implementazione CrewAI, implementazione
LangGraph, codice dell'MCP Server, deploy (Dockerfile e API), confronto motivato tra i due
framework su righe di codice, leggibilità, debugging e costi.

## Esempio di interazione

Richiesta

```json
POST /due_diligence
{
  "startup_name": "NeuroSpark",
  "startup_url": "https://neurospark.example.com"
}
```

Risposta

```json
{
  "completed_sections": ["market", "tech", "team", "financial"],
  "final_memo": "# Due Diligence — NeuroSpark\n## Executive Summary\n...",
  "execution_metadata": { "total_tokens": 48230, "duration_seconds": 142 }
}
```

## Note

1. Nomi di variabili, funzioni e classi sempre in inglese, snake_case (CamelCase solo per classi).
2. Le ricerche web possono essere mockate per garantire riproducibilità del notebook, ma il
   codice deve poter usare Tavily reale tramite variabile d'ambiente.
3. Docstring obbligatorie per agenti, tool e funzioni dello stato condiviso.
