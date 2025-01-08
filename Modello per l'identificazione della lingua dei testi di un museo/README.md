# Modello per l'Identificazione della Lingua di Testi per un Museo

## Caso d'Uso Aziendale: MuseumLangID

### Introduzione all'Azienda
MuseumLangID è un'iniziativa di un museo internazionale che ospita una vasta collezione di opere d'arte e manufatti. Le descrizioni degli oggetti sono spesso scritte in diverse lingue, e il personale del museo ha bisogno di uno strumento automatizzato per identificare rapidamente la lingua di questi testi.

### Problema
La gestione delle informazioni multilingue è una sfida significativa per il museo. Attualmente, la lingua di ogni descrizione deve essere identificata manualmente, il che richiede tempo e può portare a errori. Con l'espansione delle collezioni, il numero di testi da analizzare aumenta, rendendo necessario un approccio automatizzato e scalabile.

### Obiettivo del Progetto
L'obiettivo è sviluppare un modello di machine learning basato su tecniche di Natural Language Processing (NLP) per identificare la lingua di testi forniti dal museo. Questo modello dovrà:

1. Riconoscere automaticamente la lingua di un testo.
2. Supportare almeno 3 lingue principali.
3. Essere facile da integrare con il sistema esistente del museo.

### Benefici Attesi
- **Automazione:** Eliminare la necessità di identificazione manuale delle lingue.
- **Efficienza:** Processare rapidamente grandi volumi di testi.
- **Accuratezza:** Ridurre gli errori umani nell'identificazione delle lingue.

### Specifiche del Progetto
#### **Dataset**
Il dataset è disponibile a questo link: [https://raw.githubusercontent.com/Profession-AI/progetti-ml/refs/heads/main/Modello%20per%20l'identificazione%20della%20lingua%20dei%20testi%20di%20un%20museo/museo_descrizioni.csv](https://raw.githubusercontent.com/Profession-AI/progetti-ml/refs/heads/main/Modello%20per%20l'identificazione%20della%20lingua%20dei%20testi%20di%20un%20museo/museo_descrizioni.csv). Contiene varie descrizioni in più lingue, con una colonna che rappresenta il codice della lingua, che è il target da prevedere.

#### **Tecnologie**
- Linguaggio di programmazione: Python
- Librerie richieste:
  - `scikit-learn`
  - `nltk`
  - `numpy`
  - `pandas`

#### **Funzionalità Chiave**
1. **Preprocessing dei Dati:**
   - Pulizia del testo (rimozione di caratteri speciali, normalizzazione).
   - Tokenizzazione e rappresentazione dei testi in un formato numerico (ad esempio, Bag of Words o TF-IDF).

2. **Sviluppo del Modello:**
   - Creazione di un modello di classificazione delle lingue basato su algoritmi di machine learning (ad esempio, Naive Bayes, Support Vector Machine o Random Forest).
   - Addestramento e validazione del modello sul dataset fornito.

3. **Valutazione:**
   - Utilizzare metriche come accuratezza, precisione, richiamo e F1-score per valutare le prestazioni del modello.

### Consegna

Dovrai consegnare un notebook che riporta la creazione del modello, i vari test per validare le sue performance e anche un commento a tali risultati.

