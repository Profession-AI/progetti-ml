# Sistema multi-agente per la due diligence di startup

## Contest del Progetto

Helix Ventures è un fondo di venture capital early-stage che ogni mese valuta decine di startup. La due diligence iniziale — analisi di mercato, team, prodotto e finanza — richiede oggi due o tre giorni di lavoro per analista. L'azienda vuole automatizzare questa fase con un sistema multi-agente che, dati il nome e il sito di una startup, produca un memo strutturato in meno di mezz'ora.

## Benefici del Progetto

L'orchestrazione di agenti specializzati porta benefici misurabili:

- Riduzione dei tempi: la due diligence passa da giorni a minuti, accelerando il flusso di valutazione del fondo.
- Copertura strutturata: ogni dimensione dell'analisi è presidiata da un agente con ruolo e responsabilità definiti.
- Robustezza: il memo viene prodotto anche in presenza di errori o sezioni mancanti, grazie a strategie di degradazione controllata.
- Confronto metodologico: due implementazioni parallele permettono di valutare framework alternativi su basi oggettive.

## Dettagli del Progetto

Il sistema parte dalla definizione dei requisiti, individuando da quattro a sei agenti (ad esempio Coordinator, Market Analyst, Tech Reviewer, Team Analyst, Memo Writer) con ruolo, goal, backstory, tool e perimetro di responsabilità. Viene implementato due volte, una con CrewAI e una con LangGraph, applicando un pattern di orchestrazione Supervisor con almeno un punto di parallelismo. Lo stato condiviso è tipizzato con Pydantic e gestisce almeno un conflitto di scrittura tramite una reducer function. Almeno un tool è esposto tramite un MCP Server custom in Python. La gestione degli errori prevede retry, fallback e graceful degradation. Il sistema è esposto come API FastAPI con gli endpoint POST /due_diligence e GET /health, containerizzata con Docker, e le esecuzioni sono tracciate con Langfuse o LangSmith.

## Obiettivi del Progetto

1. Progettare il sistema partendo dai requisiti e dal design degli agenti.
2. Implementare il sistema in CrewAI e in LangGraph con orchestrazione Supervisor.
3. Definire uno stato condiviso tipizzato con gestione dei conflitti di scrittura.
4. Esporre un tool tramite MCP Server custom e gestire gli errori in modo resiliente.
5. Deployare l'API containerizzata e tracciarne le esecuzioni.

## Deliverable

Un notebook Colab contenente documento di design, le due implementazioni, il codice dell'MCP Server, il materiale di deploy (Dockerfile e API) e un confronto motivato tra i framework su righe di codice, leggibilità, debugging e costi. Le ricerche web possono essere mockate per garantire la riproducibilità, ma il codice deve poter usare Tavily reale tramite variabile d'ambiente. I nomi sono in inglese e snake_case (CamelCase per le classi), con docstring obbligatorie per agenti, tool e funzioni dello stato condiviso.

## Motivazione del Progetto

Automatizzando la due diligence iniziale, Helix Ventures aumenta la capacità di analisi del fondo, riduce il rischio di omissioni e libera gli analisti per le valutazioni a maggior valore aggiunto, consolidando un processo decisionale più rapido e ripetibile.
