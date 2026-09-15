# Exam

> **Big data and text analysis**
>
> Data: *2024-09-10*
>
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luigimalaguti/bdta/blob/main/packages/exam-20240910/src/notebook.ipynb)

## Parte 0: Il Dataset

Il dataset (preso da [Kaggle](https://www.kaggle.com/datasets/mathchi/churn-for-bank-customers)) contiene dati relativi ai clienti di una banca. La variabile da predire è `Exited` e indica se il cliente ha abbandonato la banca.

Note: Il file csv che si trova al [link](https://bit.ly/3ATiuxi).

## Parte 1: Analisi (Punti 10)

### Domanda 01 (Punti 1)

Quante sono le istanze contenute nel dataset? Il dataset è completo (cioè per ogni istanza tutti i valori di ogni attributo sono sempre correttamente specificati - non esistono "missing values")? Il dataset è bilanciato per quanto riguarda la classe da predire?

### Domanda 02 (Punti 4)

Dopo aver discretizzato l'attributo `Age` in 5 gruppi, verificare se è vero che i clienti più anziani hanno meno probabilità di abbandonare la banca rispetto ai più giovani. Considerando i clienti con più di 60 anni, verificare se è vero che maggiore è il saldo (`Balance`) e minore è la probabilità che il cliente abbandoni la banca.

### Domanda 03 (Punti 3)

Riportare in una pivot table la media di `CreditScore` raggruppando per uomini e donne (sulle righe) e i valori di salario stimato discretizzati in 5 gruppi (sulle colonne). Si può dire che i clienti con `CreditScore` più elevato sono quelli con il salario più alto? Si notano differenze tra uomini e donne?

### Domanda 04 (Punti 2)

Considerando soltanto i clienti che hanno una carta di credito e più di 100000 euro di credito, confrontare in un istogramma la distribuzione del `CreditScore` dei clienti francesi e di quelli spagnoli. Chi ha `CreditScore` maggiore?

## Parte 2: Trasformazione e Predizione (Punti 20)

### Domanda 01 (Punti 4)

Si vuole predire l'abbandono dei clienti della banca. Ricaricare il dataset originale, eliminare eventuali attributi inutili (giustificare la scelta), eliminare le eventuali istanze che contengono valori nulli, trasformare opportunamente valori categorici e dividere il dataset in modo che 3/4 degli elementi siano contenuti in un nuovo dataset "train" e 1/4 nel dataset "test" preservando le proporzioni delle classi nella colonna target.

Allenare il train con il modello DecisionTree e valutare l'accuratezza ottenuta sia sul dataset train sia sul dataset test. Confrontare i risultati ottenuti con quelli ottenuti con una predizione basata sul modello KNeighborsClassifier. Effettuare alcune considerazioni sui risultati ottenuti, tenendo in considerazione i valori di accuracy, F1 score, l'analisi della confusion matrix e la predizione effettuata da un dummy classifier a scelta.

### Domanda 02 (Punti 1)

Confrontare l'accuratezza ottenuta nel punto precedente con l'accuratezza che si ottiene con una 10 Fold cross validation.

### Domanda 03 (Punti 5)

Considerando i dati del test set e utilizzando il modello DecisionTree, la probabilità di predire l'abbandono del cliente della banca è la stessa per uomini e donne? Valutare se l'accuratezza della predizione negli uomini è la stessa ottenuta nelle donne. Come varia l'accuratezza se elimino l'attributo `Gender`?

### Domanda 04 (Punti 2)

A partire dal dataset iniziale (in cui sono stati eliminati eventuali attributi inutili ed eventuali istanze con valori nulli) aggiungere una nuova feature nel dataset con il valore di `(EstimatedSalary * Tenure + Balance) / 2`. L'accuratezza del modello DecisionTree migliora? Come cambia l'accuratezza se i valori della nuova feature vengono discretizzati in 10 gruppi?

### Domanda 05 (Punti 2)

A partire dal dataset iniziale (in cui sono stati eliminati eventuali attributi inutili ed eventuali istanze con valori nulli) trovare i valori migliori dei parametri `criterion` e `max_depth` del classificatore DecisionTree. Come varia l'accuracy?

### Domanda 06 (Punti 03)

Creare una pipeline in cui gli attributi `Balance` e `EstimatedSalary` sono discretizzati in 6 intervalli, l'attributo `Tenure` è scalato nell'intervallo 0-1 e tutti gli altri attributi sono lasciati invariati. La pipeline deve applicare il modello DecisionTree con i parametri migliori trovati al punto 5. Valutare l'accuratezza della classificazione.

### Domanda 07 (Punti 3)

Creare una nuova pipeline che seleziona N componenti tra quelle ottenute dalla pipeline del punto 6 utilizzando la funzione TruncatedSVD e applica il modello DecisionTree. Attraverso la funzione di gridSearchCV, valutare il valore migliore per il numero di componenti (`n_components`) tra 2, 4 e 6 e il numero migliore di gruppi in cui discretizzare gli attributi `Balance` e `EstimatedSalary`.
