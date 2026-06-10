# Assistente AI per il supporto clienti di un e-commerce

## Contesto aziendale

GreenThumb Marketplace è un e-commerce di articoli per il giardinaggio. Riceve centinaia di
richieste al giorno di natura eterogenea: domande sui prodotti, stato degli ordini, consigli
agronomici, gestione resi. L'azienda vuole introdurre un assistente AI che risponda
autonomamente alle richieste di primo livello, recuperi informazioni dal catalogo e consulti lo
stato degli ordini, mantenendo coerenza nella conversazione.

## Obiettivi del progetto

1. Implementare un agente con loop ReAct usando LangChain e LiteLLM.
2. Esporre almeno tre tool: ricerca sul catalogo (RAG su un vector store), lettura stato ordine,
   escalation a operatore umano.
3. Gestire memoria a breve termine con una strategia esplicita (trimming o summarization) e
   memoria a lungo termine semantica (RAG) su una knowledge base aziendale fittizia.
4. Produrre risposte in structured output (JSON con answer, confidence, sources,
   needs_human).
5. Valutare l'agente su un dataset di test con almeno una metrica RAGAS e una DeepEval.
6. Deployare l'agente come API con FastAPI o Chainlit in locale.

## Dataset

Lo studente prepara e include una knowledge base fittizia di almeno 30 documenti (schede
prodotto, guide, policy resi) e un file orders.json con almeno 20 ordini.

## Esempio di interazione

Richiesta

```json
POST /chat
{
  "message": "Quando arriva l'ordine 1042? Posso piantare adesso i bulbi di tulipano?"
}
```

Risposta

```json
{
  "answer": "L'ordine 1042 arriva domani. I tulipani vanno piantati in autunno (ottobre-novembre): conservali in luogo fresco fino a settembre.",
  "confidence": "high",
  "sources": ["guides/bulbi_autunnali.md"],
  "needs_human": false
}
```

## Note

1. Nomi di variabili, funzioni e classi sempre in inglese, snake_case (CamelCase solo per classi).
2. Usa docstring per documentare funzioni e classi.
3. Includi un dataset di evaluation di almeno 15 conversazioni e commenta i risultati.
