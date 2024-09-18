# Segmentazione della clientela per campagne di marketing mirate

FinTech Solutions S.p.A., leader nel settore dei servizi finanziari, ha deciso di lanciare una **nuova campagna di marketing** per promuovere la sua linea di carte di credito. Per ottimizzare l'efficacia della campagna, l'azienda ha deciso di segmentare i propri clienti in gruppi omogenei, basati sui comportamenti di spesa e utilizzo delle carte di credito. 

Questa segmentazione permetterà all'azienda di indirizzare **campagne di marketing personalizzate** a ciascun cluster di clienti, massimizzando così il ritorno sull'investimento e migliorando l'esperienza dell'utente.

## Obiettivo del Progetto

L'obiettivo principale è sviluppare un modello di **segmentazione dei clienti** basato sulle informazioni fornite dal dataset aziendale, contenente i dati di svariati possessori di carte di credito. La segmentazione aiuterà FinTech Solutions a identificare cluster specifici verso i quali indirizzare strategie di marketing mirate.

## Descrizione del Dataset

Il dataset a disposizione contiene le seguenti informazioni:

- **CUST_ID**: Identificativo univoco del titolare della carta di credito (categorico).
- **BALANCE**: Importo del saldo rimanente sul conto per gli acquisti.
- **BALANCE_FREQUENCY**: Frequenza di aggiornamento del saldo, con un punteggio tra 0 e 1 (1 = aggiornato frequentemente, 0 = non aggiornato frequentemente).
- **PURCHASES**: Quantità totale degli acquisti effettuati dal conto.
- **ONEOFF_PURCHASES**: Importo massimo degli acquisti effettuati in un'unica soluzione.
- **INSTALLMENTS_PURCHASES**: Importo degli acquisti effettuati a rate.
- **CASH_ADVANCE**: Anticipo in contanti dato dall'utente.
- **PURCHASES_FREQUENCY**: Frequenza degli acquisti, con un punteggio tra 0 e 1 (1 = acquisti frequenti, 0 = acquisti non frequenti).
- **ONEOFFPURCHASESFREQUENCY**: Frequenza con cui vengono effettuati acquisti in un'unica soluzione (1 = frequenti, 0 = non frequenti).
- **PURCHASESINSTALLMENTSFREQUENCY**: Frequenza con cui vengono effettuati acquisti a rate (1 = frequenti, 0 = non frequenti).
- **CASHADVANCEFREQUENCY**: Frequenza con cui viene richiesto l'anticipo in contanti.
- **CASHADVANCETRX**: Numero di transazioni effettuate con anticipo in contanti.
- **PURCHASES_TRX**: Numero totale di transazioni di acquisto effettuate.
- **CREDIT_LIMIT**: Limite massimo della carta di credito per ciascun utente.
- **PAYMENTS**: Importo totale dei pagamenti effettuati dall'utente.
- **MINIMUM_PAYMENTS**: Importo minimo dei pagamenti effettuati dall'utente.
- **PRCFULLPAYMENT**: Percentuale del pagamento completo pagato dall'utente.
- **TENURE**: Durata del servizio di carta di credito per l'utente (in anni).

## Valore Aggiunto

La segmentazione dei clienti attraverso tecniche di clustering offre numerosi benefici strategici:

1. **Ottimizzazione del Marketing**: Identificando specifici comportamenti e preferenze dei clienti, l'azienda può creare campagne promozionali **mirate**, migliorando il tasso di risposta e la conversione.
  
2. **Personalizzazione dell'Offerta**: I cluster possono essere utilizzati per sviluppare **offerte personalizzate** (es. promozioni per l'aumento del limite di credito, sconti sugli acquisti rateali) che meglio si adattano alle esigenze dei clienti.

3. **Efficienza Operativa**: Attraverso la segmentazione, l'azienda può focalizzare le risorse sui clienti più redditizi, ottimizzando i costi di acquisizione e fidelizzazione dei clienti.

4. **Identificazione di Opportunità di Crescita**: La segmentazione può far emergere gruppi di clienti con potenziale di crescita (es. coloro che utilizzano frequentemente acquisti rateali ma non il pagamento completo), permettendo all'azienda di proporre prodotti finanziari aggiuntivi.

## Fasi del Progetto

### 1. Analisi Esplorativa dei Dati (EDA)
Iniziare con un'analisi esplorativa del dataset per comprendere meglio la distribuzione delle variabili, individuare eventuali dati mancanti e valutare la necessità di trasformazioni sui dati.

### 2. Preprocessing dei Dati
- Gestione dei valori mancanti (per variabili come **MINIMUM_PAYMENTS**).
- Normalizzazione e standardizzazione delle variabili quantitative, come **BALANCE**, **PURCHASES** e **CASH_ADVANCE**.
  
### 3. Segmentazione tramite Clustering
- Utilizzo di algoritmi di clustering (come K-Means o DBSCAN) per identificare gruppi di clienti omogenei.
- Valutazione delle performance del clustering attraverso metriche come **silhouette score** e **elbow method**.

### 4. Interpretazione dei Cluster
Analisi e descrizione dei diversi cluster in termini di:
- **Spese medie** (bilancio, acquisti in unica soluzione, acquisti a rate).
- **Abitudini di pagamento** (percentuale di pagamenti minimi, pagamenti completi).
- **Frequenza di utilizzo** della carta (anticipi in contanti, frequenza degli acquisti).

### 5. Sviluppo delle Strategie di Marketing
Sulla base dei risultati del clustering, verranno sviluppate **strategie di marketing specifiche per ciascun cluster**. Ad esempio:
- Promozioni per incentivare gli acquisti rateali in clienti che mostrano interesse per questa modalità.
- Offerte personalizzate per i clienti con alta frequenza di anticipi in contanti, con suggerimenti per servizi finanziari aggiuntivi.

## Conclusione

La segmentazione della clientela permette a FinTech Solutions S.p.A. di migliorare l'efficacia delle sue campagne di marketing, personalizzando le offerte per gruppi specifici di utenti. Questo porterà a una maggiore fidelizzazione dei clienti, aumenterà le transazioni e ottimizzerà l'utilizzo dei prodotti finanziari offerti.



# Link al dataset

https://proai-datasets.s3.eu-west-3.amazonaws.com/credit_card_customers.csv

# Modalità di consegna: notebook di google colab