# Exam

> **Big data and text analysis**
>
> Data: *2026-01-08*
>
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luigimalaguti/bdta/blob/main/packages/exam-20260108/src/notebook.ipynb)

## Parte 0: Il Dataset

Preso da [Kaggle](https://www.kaggle.com/datasets/uciml/adult-census-income), il dataset Bank Marketing è scaricabile attraverso il [link](https://bit.ly/4sjlIjQ) e contiene dati demografici e lavorativi di cittadini statunitensi, come età, istruzione, occupazione, stato civile, ore lavorate a settimana e capitale investito. L'obiettivo è predire se il reddito annuale di una persona supera i 50.000$, indicato dalla colonna target income (>50K / ≤50K).

## Parte 1: Analisi (Punti 10)

### Domanda 01 (Punti 1)

Quante sono le istanze contenute nel dataset? Il dataset è completo (cioè per ogni istanza tutti i valori di ogni attributo sono sempre correttamente specificati - non esistono "missing values")? Il dataset è bilanciato per quanto riguarda la classe da predire?

### Domanda 02 (Punti 2)

Verificare se i lavoratori con laurea (Bachelors, Masters, Doctorate) e età inferiore a 40 anni hanno una probabilità maggiore di reddito >50K rispetto ai lavoratori più anziani con lo stesso livello di istruzione.

### Domanda 03 (Punti 3)

Discretizzare la variabile hours.per.week in 3 fasce (≤30, 31-50, >50). Creare una tabella pivot che mostri la percentuale di redditi >50K per fascia oraria e genere (sex). Chi lavora più ore ha sempre un reddito più alto? Ci sono disparità tra uomini e donne?

### Domanda 04 (Punti 4)

Analizzare la relazione tra capitale investito (capital.gain) e livello di reddito: confrontare media e mediana di capital-gain per le due classi di reddito e visualizzare in un boxplot la distribuzione dei valori di capital.gain sulle due classi.

## Parte 2: Trasformazione e Predizione (Punti 20)

### Domanda 01 (Punti 4)

Si vuole predire la classe di reddito (`income`). Ricaricare il dataset originale, eliminare eventuali attributi inutili (giustificare la scelta), eliminare le istanze che contengono valori nulli, eliminare eventuali righe duplicate, trasformare opportunamente i valori categorici e dividere il dataset in train (3/4 del dataset) e test (1/4), preservando le proporzioni delle classi nella colonna target. Confrontare la predizione ottenuta sia sul dataset train sia sul dataset test dai classificatori ExtraTreeClassifier, KNeighborsClassifier e da un dummy classifier a scelta. Effettuare alcune considerazioni sui risultati ottenuti, tenendo in considerazione i valori di F1 e della confusion matrix.

### Domanda 02 (Punti 4)

Verificare, nelle predizioni sul dataset di test ottenute dal classificatore ExtraTreeClassifier, se la probabilità di reddito >50K predetta per gli uomini è diversa da quella predetta per le donne. Valutare se l'accuratezza di predizione ottenuta eliminando la colonna `sex` è diversa. Cosa si può osservare da questa valutazione?

### Domanda 03 (Punti 2)

A partire dal dataset utilizzato al punto 1, trovare i valori migliori dei parametri `criterion` e `max_depth` del classificatore ExtraTreeClassifier. Come variano le performance?

### Domanda 04 (Punti 3)

Creare una pipeline in cui, a partire dal dataset utilizzato al punto 1, i valori degli attributi `age` e `hours.per. week` sono discretizzati in 5 intervalli, le variabili `capital.gain` e `capital.loss` sono scalate nell'intervallo 0-1 e tutti gli altri attributi sono lasciati invariati. Applicare il classificatore ExtraTreeClassifier con i valori migliori dei parametri analizzati nel punto 3 e confrontare i risultati.

### Domanda 05 (Punti 3)

Creare una pipeline che, a partire dal dataset iniziale, trasforma le colonne testuali in valori numerici, scala le colonne numeriche attraverso lo Standard Scaler e applica il classificatore ExtraTreeClassifier.

### Domanda 06 (Punti 4)

Ridurre la dimensione del dataset aggiungendo SelectKBest alla pipeline del punto precedente. Valutare con GridSearchCV i valori migliori di `k` di SelectkBest e dei parametri `criterion` e `max_depth` del classificatore ExtraTreeClassifier. Confrontare i risultati con quelli ottenuti precedentemente.
