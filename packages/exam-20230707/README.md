# Exam

> **Big data and text analysis**
>
> Data: *2023-07-07*
>
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luigimalaguti/bdta/blob/main/packages/exam-20230707/src/notebook.ipynb)

## Parte 0: Il Dataset

Il datataset (preso e modificato da [Kaggle](https://www.kaggle.com/datasets/rishikeshkonapure/home-loan-approval) contiene dati relativi a persone che sono riuscite a estinguere il prestito (Loan_Status).

Note: Il file csv che si trova al [link](https://bit.ly/2023BDTA1).

> **Note personali.**
>
> Nel dataset di Kaggle `Loan_Status` riguarda l'ottenimento o meno del prestito, ovvero se la richiesta è stata approvata o meno. Quindi, molto probabilmente, la classificazione riguarda l'approvazione del prestito più che alla restituzione come in molte domande del testo.
>
> Laddove necessario, il testo viene modificato con <s>una riga sul testo</s> in modo da sapere cosa viene modificato, mentre la correzione al testo è mostrata <u>come sottolineato</u>.

## Parte 1: Analisi (Punti 10)

### Domanda 01 (Punti 1)

Quante sono le istanze contenute nel dataset? Il dataset è completo (cioè per ogni istanza tutti i valori di ogni attributo sono sempre correttamente specificati - non esistono "missing values")? Il dataset è bilanciato per quanto riguarda la classe da predire?

### Domanda 02 (Punti 4)

Verificare se in generale le persone con la laurea (Education = "Graduate") hanno più difficoltà a <s>restituire</s> <u>ottenere</u> il prestito rispetto a quelle senza. Realizzare una pivot table attraverso la quale mostrare quanti sono gli uomini / donne (sulle righe), con / senza laurea (colonne) e individuare per ognuna di queste categorie la percentuale di persone che non sono in grado di <s>restituire</s> <u>ottenere</u> il prestito. L'essere laureato incide diversamente nei due generi?

### Domanda 03 (Punti 3)

Ci si aspetta che l'ammontare del prestito (LoanAmount) concesso abbia una qualche relazione con la durata del prestito (Loan_Amount_Term). Calcolare il rapporto tra le due grandezze e fare un grafico della distribuzione dei valori.

### Domanda 04 (Punti 2)

Ci si aspetta che sia più difficile <s>restituire</s> <u>ottenere</u> prestiti con durata più limitata. Questa intuizione è in qualche modo supportata dai dati? Motivare la risposta.

## Parte 2: Trasformazione e Predizione (Punti 20)

### Domanda 01 (Punti 3)

Si vuole predire il valore di Loan_Status sulla base degli attributi presenti nel dataset. Ricaricare il dataset originale, eliminare eventuali attributi inutili (giustificare la scelta), eliminare le istanze che contengono valori nulli, rendere tutti gli attributi numerici, e dividerlo in modo che 3/4 degli elementi siano contenuti in un nuovo dataset "train" e 1/4 nel dataset "test".

Allenare il train con il modello Decision Tree e valutare l'accuracy ottenuta calcolata sia sul dataset train sia sul dataset test. Confrontare i risultati ottenuti con quelli ottenuti con una predizione basata sul modello KNeighborsClassifier. Effettuare alcune considerazioni sui risultati ottenuti, tenendo in considerazione anche l'analisi della confusion matrix e la predizione effettuata da un dummy classifier.

### Domanda 02 (Punti 4)

Trovare i parametri migliori del classificatore DecisionTree. Agire sui parametri criterion e min_samples_leaf. Verificare se l'accuratezza che si ottiene con la nuova configurazione supera quella con i parametri di default ottenuta al punto 1.

### Domanda 03 (Punti 5)

Valutare la demographic parity del classificatore Decision Tree rispetto al valore di Education, ovvero se la probabilità di predire 0 è la stessa nelle persone laureate e non laureate. Valutare l'equalized odds, ovvero se l'accuratezza ottenuta nelle persone laureate è la stessa ottenuta nelle persone non laureate. Eliminare l'attributo Education dal train e valutare se se l'accuratezza ottenuta nelle persone laureate è la stessa ottenuta nelle persone non laureate.

### Domanda 04 (Punti 3)

Creare una pipeline che a partire dal dataset iniziale (dopo aver tolto le colonne rimosse al punto 1 e le colonne testuali):

- usi il Simplelmputer per inserire i valori nulli
- divida in 10 bins i valori di LoanAmount
- applichi il DecisionTreeClassifier per effettuare la predizione

### Domanda 05 (Punti 3)

Creare una pipeline che a partire dal dataset iniziale (dopo aver tolto le colonne rimosse al punto 1):

- usi il Simplelmputer per inserire i valori nulli
- trasformi in valori numerici le colonne testuali
- Applichi lo standard scaler
- applichi il DecisionTreeClassifier per effettuare la predizione

### Domanda 06 (Punti 2)

È possibile utilizzare un regressore linerare al posto del DecisionTree? In che modo?
