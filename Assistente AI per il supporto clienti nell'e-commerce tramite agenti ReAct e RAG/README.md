# Assistente AI per il supporto clienti nell'e-commerce tramite agenti ReAct e RAG

## Contesto del Progetto

GreenThumb Marketplace è un e-commerce di riferimento nel settore degli articoli per il giardinaggio. Ogni giorno riceve centinaia di richieste di natura eterogenea — domande sui prodotti, stato degli ordini, consigli agronomici, gestione dei resi — che oggi gravano interamente sul supporto umano. L'azienda intende introdurre un assistente AI capace di gestire autonomamente le richieste di primo livello, recuperare informazioni dal catalogo e consultare lo stato degli ordini, mantenendo coerenza lungo l'intera conversazione.

## Benefici del Progetto

L'introduzione di un agente conversazionale offre vantaggi concreti:

- Autonomia operativa: gestione automatica delle richieste di primo livello, con riduzione del carico sul personale.
- Coerenza conversazionale: una memoria strutturata che mantiene il contesto del dialogo e fornisce risposte pertinenti.
- Affidabilità e tracciabilità: ogni risposta è accompagnata da un livello di confidenza e dalle fonti consultate, abilitando l'escalation umana quando necessario.
- Scalabilità: una base architetturale pronta per crescere con i volumi di richieste.

## Dettagli del Progetto

Il sistema si fonda su un agente che adotta il loop ReAct, implementato con LangChain e LiteLLM. L'agente espone almeno tre tool: una ricerca semantica sul catalogo (RAG su vector store), la lettura dello stato di un ordine e l'escalation verso un operatore umano. La gestione del contesto combina una memoria a breve termine con strategia esplicita (trimming o summarization) e una memoria a lungo termine semantica (RAG) su una knowledge base aziendale fittizia. Le risposte sono prodotte in structured output, un oggetto JSON con i campi answer, confidence, sources e needs_human. L'agente viene valutato su un dataset di test con almeno una metrica RAGAS e una DeepEval, e infine reso disponibile come API tramite FastAPI o Chainlit in ambiente locale.

## Dataset

Lo studente prepara e include una knowledge base fittizia di almeno 30 documenti (schede prodotto, guide, policy resi) e un file orders.json con almeno 20 ordini.

## Obiettivi del Progetto

1. Implementare un agente con loop ReAct su LangChain e LiteLLM.
2. Esporre i tre tool di catalogo, stato ordine ed escalation umana.
3. Gestire memoria a breve e a lungo termine con strategie esplicite.
4. Produrre risposte in structured output JSON e valutarle con RAGAS e DeepEval.
5. Deployare l'agente come API locale.

## Deliverable

Un notebook Google Colab con codice documentato, comprensivo di un dataset di evaluation di almeno 15 conversazioni con commento dei risultati. Le convenzioni prevedono nomi di variabili, funzioni e classi in inglese e snake_case (CamelCase per le classi) e docstring per funzioni e classi.

## Motivazione del Progetto

Automatizzando il primo livello di supporto, GreenThumb Marketplace migliora i tempi di risposta e la soddisfazione dei clienti, libera il personale dalle richieste ripetitive e si dota di una base tecnologica solida e misurabile per l'assistenza conversazionale.
