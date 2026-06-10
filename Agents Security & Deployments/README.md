# Agents Security & Deployments

## Contesto del Progetto

Atlantis Bank ha sviluppato un agente AI di assistenza clienti con accesso a dati sensibili — saldi, movimenti, trasferimento fondi — e a una knowledge base interna. L'agente è funzionante ma non è mai stato sottoposto a red teaming sistematico: le difese sono limitate, manca il monitoraggio in produzione e i deploy avvengono manualmente. Prima di estenderlo ad altre linee di business, il team di sicurezza richiede un intervento end-to-end di hardening, observability e CI/CD.

## Benefici del Progetto

L'intervento di sicurezza porta vantaggi determinanti per un contesto regolamentato:

- Protezione dei dati sensibili: difese a più livelli contro prompt injection, esfiltrazione e abuso dei tool.
- Conformità e controllo: human-in-the-loop obbligatorio sulle operazioni critiche e modello di permessi a privilegio minimo.
- Affidabilità in produzione: monitoraggio continuo, alert e una pipeline che blocca i deploy non conformi.
- Misurabilità: valutazione quantitativa di sicurezza e qualità delle risposte.

## Dettagli del Progetto

Lo studente parte da un agente bancario fittizio (RAG su KB interna e tool get_account_balance, list_transactions, transfer_funds) e ne cura la messa in sicurezza completa. Il lavoro comprende un threat model contro la OWASP Top 10 for Agentic Applications (2026) con severity rating; una campagna di red teaming con almeno otto attacchi manuali (prompt injection diretto e indiretto, multi-turn crescendo, jailbreak con encoding, data exfiltration, abuso del tool transfer_funds) e un red teaming automatizzato con almeno due strumenti tra DeepTeam, PyRIT, Garak e Promptfoo. Vengono implementate difese da zero in puro Python (input filter, output validator con regex per PII su IBAN, CF e carta, classificatore di intent malevolo e canary token) e difese basate su framework (NeMo Guardrails con DSL Colang, Guardrails AI e Microsoft Presidio), confrontate sulle metriche di attacchi bloccati, latenza e falsi positivi. L'architettura di sicurezza prevede un permission model least-privilege, il sandboxing del tool transfer_funds con Docker e human-in-the-loop obbligatorio sul trasferimento fondi.

## Obiettivi del Progetto

1. Costruire il threat model OWASP con severity rating.
2. Eseguire red teaming manuale e automatizzato.
3. Implementare difese custom e difese con framework, confrontandole.
4. Definire l'architettura di sicurezza con least-privilege, sandboxing e HITL.
5. Valutare il sistema con un dataset di almeno 20 conversazioni, metriche RAGAS (faithfulness, context_precision), DeepEval (tool_correctness, task_completion) e una custom policy_adherence.
6. Configurare l'observability con Langfuse (dashboard di latenza, costi e tool calls e almeno due alert).
7. Deployare un'API FastAPI async (streaming SSE, endpoint di approvazione HITL, health check) con Dockerfile multi-stage e docker-compose.
8. Realizzare una pipeline CI/CD GitHub Actions che esegue test ed evaluation, blocca il deploy sotto soglia e versiona il system prompt con SemVer.

## Deliverable

Un notebook Colab che funge da report integrato con threat model, risultati del red teaming, tabelle comparative delle difese, codice dell'architettura di sicurezza, risultati di evaluation, screenshot Langfuse e workflow CI/CD, affiancato da una repository GitHub pubblica per codice sorgente, Dockerfile, docker-compose e cartella .github/workflows/. Tutte le chiavi API sono lette da variabili d'ambiente e mai committate; tutti i dati clienti sono fittizi e gli attacchi vanno condotti esclusivamente in ambiente di test. I nomi sono in inglese e snake_case (CamelCase per le classi), con docstring obbligatorie per funzioni di sicurezza, guardrails custom e validator.

## Motivazione del Progetto

Irrobustendo l'agente con un intervento end-to-end, Atlantis Bank protegge i dati dei clienti, rafforza la conformità normativa e si dota di un processo di deploy controllato e osservabile, condizione necessaria per estendere l'agente in sicurezza ad altre linee di business.
