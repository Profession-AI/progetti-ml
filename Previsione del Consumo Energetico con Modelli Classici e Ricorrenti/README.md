# Previsione del Consumo Energetico con Modelli Classici e Ricorrenti

## Descrizione del progetto

Fnergy Analytics è una società di consulenza quantitativa che ottimizza processi di produzione dell'energia elettrica. Il progetto ha l'obiettivo di sviluppare, usando Python e consegnando un notebook Google Colab, un sistema di previsione del consumo energetico basato su tecniche di Time Series Analysis, sia classiche (ARIMA/SARIMA) che basate su deep learning (LSTM). Il modello dovrà supportare decisioni di analisi e pianificazione energetica, fornendo previsioni affidabili sull'andamento futuro dei consumi.

Il lavoro è pensato per essere applicabile a serie storiche reali e dovrà includere analisi esplorativa delle serie temporali, verifica delle proprietà statistiche, addestramento e confronto di modelli con valutazione quantitativa delle performance predittive.

**Caso d'uso:** un analista deve stimare il consumo energetico nelle ore successive all'ultimo dato disponibile, per supportare decisioni di approvvigionamento sul mercato dell'energia. Il sistema dovrà:

- produrre previsioni a breve orizzonte temporale con stima dell'errore;
- confrontare l'affidabilità di approcci statistici classici vs reti neurali ricorrenti.

**Importanza per l'azienda:** miglioramento della qualità delle previsioni quantitative, riduzione dell'esposizione a decisioni basate su dati non modellati, e supporto alla costruzione di strategie sistematiche.

## Dataset

File: `clustered\_hourly\_values\_all.csv` (scaricabile dal seguente link: [https://github.com/Profession-AI/progetti-ml/blob/main/Previsione%20del%20Consumo%20Energetico%20con%20Modelli%20Classici%20e%20Ricorrenti/clustered_hourly_values_all.csv](https://github.com/Profession-AI/progetti-ml/blob/main/Previsione%20del%20Consumo%20Energetico%20con%20Modelli%20Classici%20e%20Ricorrenti/clustered_hourly_values_all.csv))

Il dataset contiene 30 serie temporali orarie derivate dal dataset raccolte nel Progetto "The Smart Metering Electricity Customer Behaviour Trials (CBTs)". Il dataset contiene dati relative al consume di energia elettrica fra il 2009 e il 2010 in più di 5000 case, negozi e altre attività in Irlanda. Ogni serie temporale bel file `clustered\_hourly\_values\_all.csv` rappresenta il consumo medio (kWh) di un cluster di utenze con profilo simile.

Per questo progetto si lavora su tre serie selezionate per le loro caratteristiche statistiche distinte:

- **cluster_26**: stagionalità giornaliera (24h) e settimanale (168h) entrambe marcate; i consumi variano significativamente tra fasce orarie e tra giorni feriali e weekend
- **cluster_9**: stagionalità giornaliera (24h) presente, stagionalità settimanale assente; comportamento simile in tutti i giorni della settimana
- **cluster_24**: nessuna stagionalità evidente; serie sostanzialmente piatta con variazioni non strutturate

## Obiettivi del progetto

### 1\. Analisi esplorativa e pulizia delle serie temporali

- Visualizzazione dell'andamento delle tre serie nel tempo
- Pulizia del dataset (gestione missing values, outliers…)
- Calcolo e visualizzazione di medie mobili con commento
- Feature engineering
- Preparazione dei dati per modelli sequenziali (definizione della finestra temporale, normalizzazione, suddivisione train/test)

> \*\*Nota:\*\* la suddivisione train/test deve essere strettamente sequenziale; i dati di test devono essere temporalmente successivi a quelli di training. Non è ammesso uno split casuale su serie temporali.

### 2\. Previsione con modelli classici

- Analisi ACF e PACF per la diagnosi della struttura di ciascuna serie
- Esecuzione di test appropriati per la scelta dell'approccio (es. stazionarietà, stagionalità)
- Addestramento di una baseline AR(1) come termine di confronto minimo
- Addestramento di modelli ARIMA o SARIMA su ciascuna delle tre serie, motivando le scelte in base alle caratteristiche della serie
- Valutazione delle previsioni con MAE, RMSE, MAPE
- Confronto visivo tra valori predetti e valori reali sul set di test

### 3\. Previsione con modelli ricorrenti

- Implementazione di una rete LSTM per la previsione del consumo su ciascuna delle tre serie
- Valutazione delle previsioni con MAE, RMSE, MAPE

### 4\. Ottimizzazione e confronto

- Ottimizzazione degli iperparametri con almeno uno strumento su uno o più modelli
- Confronto delle performance LSTM vs ARIMA/SARIMA vs baseline AR(1) sulla base delle stesse metriche
- Discussione su quale modello performa meglio su ciascuna serie e perché

### 5\. Conclusioni e raccomandazioni

- Sintesi dei risultati con indicazione del modello preferibile per ciascuna serie e motivazione della scelta
- Considerazioni sull'applicabilità operativa in un contesto di pianificazione energetica reale
- Proposte di estensioni future (es. feature aggiuntive, modelli ibridi, multi-step forecasting)

## Criteri di valutazione

- Completezza e chiarezza dell'analisi esplorativa
- Correttezza del processo di preparazione delle serie temporali e della separazione train/test
- Qualità del confronto tra i modelli: metriche rilevanti, interpretazione dei risultati e considerazioni sui limiti
- Chiarezza delle conclusioni e delle raccomandazioni operative
