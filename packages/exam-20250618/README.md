# Exam

> **Big data and text analysis**
>
> Data: *2025-06-18*
>
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luigimalaguti/bdta/blob/main/packages/exam-20250618/src/notebook.ipynb)

## Parte 0: Il Dataset

Preso da [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn), il dataset è scaricabile attraverso il [link](http://bit.ly/4n56Sec) e contiene informazioni sui clienti di una compagnia telefonica, indicando se hanno abbandonato il servizio (Churn).

## Parte 1: Analisi (Punti 10)

### Domanda 01 (Punti 1)

Quante sono le istanze contenute nel dataset? Il dataset è completo (cioè per ogni istanza tutti i valori di ogni attributo sono sempre correttamente specificati - non esistono "missing values")? Il dataset è bilanciato per quanto riguarda la classe da predire?

### Domanda 02 (Punti 2)

Verificare se i clienti con contratto a lungo termine (`Contract="Two year"`) hanno in media una spesa mensile (`MonthlyCharges`) inferiore rispetto a quelli con contratti mensili o annuali.

### Domanda 03 (Punti 3)

Discretizzare `tenure` (anzianità del cliente) in 3 gruppi (bassa, media, alta). Creare una tabella pivot che mostri la percentuale di abbandono (`Churn`) per gruppo di anzianità e tipo di contratto. I clienti con anzianità bassa e contratto mensile hanno una probabilità maggiore di abbandonare?

### Domanda 04 (Punti 4)

Determinare se l'adozione di almeno un servizio extra (`OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`) riduce il tasso di abbandono. Creare una nuova feature che conta il numero di servizi aggiuntivi attivi per cliente e verificare con un grafico se il tasso di abbandono diminuisce all'aumentare del numero di servizi attivi.

## Parte 2: Trasformazione e Predizione (Punti 20)

### Domanda 01 (Punti 4)

Si vuole predire l'abbandono dei clienti (`Churn`). Ricaricare il dataset originale, eliminare eventuali attributi inutili (giustificare la scelta) e istanze che contengono valori nulli, trasformare opportunamente valori categorici e dividere il dataset in 75% train e 25% test, preservando le proporzioni delle classi nella colonna target.
Confrontare la predizione ottenuta sia sul dataset train sia sul dataset test dai classificatori LogisticRegression, RandomForestClassifier e da un dummy classifier a scelta. Effettuare alcune considerazioni sui risultati ottenuti, tenendo in considerazione i valori di accuracy, F1 e della confusion matrix.

### Domanda 02 (Punti 5)

La predizione di RandomForestClassifier è influenzata dal genere? Valutare sui dati di test se la probabilità di abbandono calcolata sulle donne è la stessa per gli uomini. Valutare se l'accuratezza di predizione ottenuta negli uomini è la stessa ottenuta nelle donne. Eliminare l'attributo gender e valutare se l'accuratezza ottenuta negli uomini è la stessa ottenuta nelle donne.

### Domanda 03 (Punti 2)

A partire dal dataset utilizzato al punto 1, trovare i migliori parametri di `max_depth` e `n_estimators` in RandomForestClassifier. Come cambia l'F1-score?

### Domanda 04 (Punti 3)

A partire dal dataset originale, dopo aver applicato un Label Encoder alle feature categoriche, considerare le 5 feature più correlate (positivamente o negativamente) a `Churn` e verificare se la predizione di RandomForestClassifier migliora.

### Domanda 05 (Punti 3)

Creare una pipeline che, a partire dal dataset originale, discretizza MonthlyCharges in 5 gruppi, applica OneHotEncoder alle variabili categoriche e usa StandardScaler sulle variabili numeriche. Applicare il RandomForestClassifier con i valori migliori dei parametri analizzati nel punto 3 e confrontare i risultati.

### Domanda 06 (Punti 3)

Aggiungere alla pipeline del punto 5 la funzione SelectKBest. Utilizzare la funzione di gridSearchCV per selezionare il `K` migliore e anche i valori migliori dei parametri `max_depth` e `n_estimators` di RandomForestClassifier (scegliere a piacere alcuni valori).
