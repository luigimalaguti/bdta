# Exam

> **Big data and text analysis**
>
> Data: *2025-01-10*
>
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luigimalaguti/bdta/blob/main/packages/exam-20250110/src/notebook.ipynb)

## Parte 0: Il Dataset

Preso da [Kaggle](https://www.kaggle.com/datasets/beridzeg45/diamonds-prices-prediction), il dataset è scaricabile attraverso il [link](http://bit.ly/4jaJgD6) e contiene dati relativi ad alcuni tipi di diamanti. Sono presenti le seguenti feature:

- `Shape`: forma del diamante.
- `Cut`: qualità del taglio del diamante (in ordine crescente: Very Good, Excellent, Ideal, Astor).
- `Color`: grado di colore del diamante da D (incolore) a Z.
- `Clarity`: grado di chiarezza basato sulle imperfezioni.
- `Carat Weight`: peso del diamante in carati.
- `Length/Width Ratio`: proporzione tra lunghezza e larghezza.
- `Depth %`: profondità del diamante come percentuale della sua larghezza.
- `Table %`: larghezza della facciata superiore in percentuale.
- `Polish`: qualità della finitura superficiale del diamante.
- `Symmetry`: precisione della forma del diamante.
- `Girdle`: spessore del bordo del diamante.
- `Culet`: dimensione della sfaccettatura inferiore.
- `Length`: lunghezza del diamante in millimetri.
- `Width`: larghezza del diamante in millimetri.
- `Height`: altezza del diamante in millimetri.
- `Price`: prezzo del diamante in dollari ($).
- `Type`: tipo di diamante (target).
- `Fluorescence`: livello di fluorescenza UV del diamante.

## Parte 1: Analisi (Punti 10)

### Domanda 01 (Punti 1)

Quante sono le istanze contenute nel dataset? Il dataset è completo (cioè per ogni istanza tutti i valori di ogni attributo sono sempre correttamente specificati - non esistono "missing values")? Il dataset è bilanciato per quanto riguarda la classe da predire?

### Domanda 02 (Punti 2)

Calcolare in una nuova colonna il volume approssimato del diamante come `Length * Width * Height` e verificare con un opportuno grafico se c'è una relazione tra il volume e il prezzo: i diamanti più grandi sono quelli più costosi?

### Domanda 03 (Punti 3)

Considerare soltanto i record con valore non nullo di `Cut` e discretizzare la variabile `Carat Weight` in 5 gruppi. Verificare attraverso una tabella pivot se è vero che il prezzo medio aumenta all'aumentare della qualità del taglio e del peso in carati.

### Domanda 04 (Punti 4)

Si vuole analizzare il prezzo a carato per ogni tipo di diamante: creare una nuova feature che rappresenta il prezzo per carato (`Price / Carat Weight`) e visualizzare attraverso dei boxplot come varia questo prezzo per ogni tipo (`Type`) di diamante.

## Parte 2: Trasformazione e Predizione (Punti 20)

### Domanda 01 (Punti 4)

Si vuole predire la tipologia di diamante (`Type`). Ricaricare il dataset originale, eliminare eventuali attributi inutili (giustificare la scelta), eliminare gli attributi con più del 50% di valori nulli, eliminare le istanze che contengono valori nulli, trasformare opportunamente valori categorici e dividere il dataset in modo che 3/4 degli elementi siano contenuti in un nuovo dataset "train" e 1/4 nel dataset "test" preservando le proporzioni delle classi nella colonna target.

Confrontare la predizione ottenuta sia sul dataset train sia sul dataset test dai classificatori DecisionTree, KNeighborsClassifier e da un dummy classifier a scelta. Effettuare alcune considerazioni sui risultati ottenuti, tenendo in considerazione i valori di F1 (con *average="weighted"*) e della confusion matrix.

### Domanda 02 (Punti 1)

Confrontare i valori di F1 ottenuti nel punto precedente con quelli che si ottengono con una 10 Fold cross validation.

### Domanda 03 (Punti 4)

Attraverso la tecnica Permutation Feature Importance (PFI) e considerando il classificatore KNeighborsClassifier, analizzare la feature importance del dataset utilizzato al punto 1. Applicare 5 permutazioni per ogni feature. Quali risultano essere le 2 feature più importanti?

### Domanda 04 (Punti 2)

A partire dal dataset utilizzato al punto 1, trovare i valori migliori dei parametri `weights` e `n_neighbors` del classificatore KNeighborsClassifier. Come varia il valore di F1?

### Domanda 05 (Punti 3)

Creare una pipeline in cui, a partire dal dataset utilizzato al punto precedente, i valori degli attributi `Length`, `Width`, `Height` sono discretizzati in 5 intervalli, la variabile `Price` è scalata nell'intervallo 0-1 e tutti gli altri attributi sono lasciati invariati. Applicare il KNeighborsClassifier con i valori migliori dei parametri analizzati nel punto precedente e confrontare i risultati.

### Domanda 06 (Punti 3)

Creare una pipeline che, a partire dal dataset iniziale a cui sono stati rimossi gli attributi con più del 50% di valori nulli, trasforma le colonne testuali in valori numerici, applica il SimpleImputer per sostituire i valori nulli, trasforma tutte le feature attraverso lo Standard Scaler e applica il KNeighborsClassifier.

### Domanda 07 (Punti 3)

Aggiungere alla pipeline del punto precedente (dopo lo Standard Scaler) la decomposizione TruncatedSVD. Valutare il valore migliore per il numero di componenti di TruncatedSVD tra 2, 4 e 6 e i valori migliori di n_neighbors e weights del KNeighborsClassifier.
