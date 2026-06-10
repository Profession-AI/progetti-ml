# Hardening e deploy in produzione di un agente bancario

## Contesto aziendale

Atlantis Bank ha sviluppato un agente AI di assistenza clienti con accesso a dati sensibili (saldi,
movimenti, trasferimento fondi) e a una knowledge base interna. L'agente è funzionante ma non
è mai stato sottoposto a red teaming sistematico, le difese sono limitate, non c'è monitoraggio in
produzione e i deploy avvengono manualmente. Prima di estenderlo ad altre linee di business, il
team di sicurezza richiede un intervento end-to-end di hardening, observability e CI/CD.

## Obiettivi del progetto

Lo studente parte da un agente bancario fittizio (RAG su KB interna + tool get_account_balance,
list_transactions, transfer_funds) e deve:

1. Threat model: mappare l'agente contro l'OWASP Top 10 for Agentic Applications (2026) con
   severity rating.
2. Red teaming: eseguire almeno 8 attacchi manuali (prompt injection diretto/indiretto,
   multi-turn crescendo, jailbreak con encoding, data exfiltration, abuso del tool
   transfer_funds) e un red teaming automatizzato con almeno due tool tra DeepTeam, PyRIT,
   Garak, Promptfoo.
3. Difese da zero: implementare in puro Python input filter, output validator con regex per PII
   (IBAN, CF, carta), classificatore di intent malevolo e canary token.
4. Difese con framework: integrare NeMo Guardrails (Colang DSL), Guardrails AI e Microsoft
   Presidio per PII. Confrontare con le difese manuali su attacchi bloccati, latenza e falsi positivi.
5. Architettura di sicurezza: permission model least-privilege, sandboxing del tool
   transfer_funds con Docker, human-in-the-loop obbligatorio sul trasferimento fondi.
6. Evaluation: dataset di almeno 20 conversazioni, metriche RAGAS (faithfulness,
   context_precision) e DeepEval (tool_correctness, task_completion) più una custom
   policy_adherence.
7. Observability: Langfuse con dashboard di latenza, costi e tool calls; almeno due alert.
8. Deploy: API FastAPI async (streaming SSE, endpoint di approvazione HITL, health check),
   Dockerfile multi-stage, docker-compose.
9. CI/CD: pipeline GitHub Actions che esegue test, evaluation, blocca il deploy se le metriche
   scendono sotto soglia; versioning del system prompt con SemVer.

## Deliverable

Notebook Colab che funge da report integrato con: threat model, risultati red teaming, tabelle
comparative delle difese, codice dell'architettura di sicurezza, risultati evaluation, screenshot
Langfuse, workflow CI/CD. Repository GitHub collegato per codice sorgente, Dockerfile,
docker-compose, .github/workflows/.

## Note

1. Nomi di variabili, funzioni e classi sempre in inglese, snake_case (CamelCase solo per classi).
2. Tutte le chiavi API vanno lette da variabili d'ambiente, mai committate.
3. Tutti i dati clienti sono fittizi e gli attacchi vanno condotti esclusivamente in ambiente di test.
4. Docstring obbligatorie per funzioni di sicurezza, guardrails custom e validator.
