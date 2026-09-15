# Exam

> **Big data and text analysis**
>
> Data: *2023-07-25*
>
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luigimalaguti/bdta/blob/main/packages/exam-20230725/src/notebook.ipynb)

## Parte 0: Il Dataset

Il datataset (preso e modificato da [Kaggle](https://www.kaggle.com/datasets/iamsouravbanerjee/data-science-salaries-2023)) contiene dati relativi a salari di persone che operano in ambito data science. Il separatore è il ";". L'obiettivo è quello di inferire il livello di esperienza (Experience Level).

Nota: Il file csv che si trova al [link](https://bit.ly/2023BDTAS).

## Parte 1: Analisi (Punti 10)

### Domanda 01 (Punti 2)

Quante sono le istanze contenute nel dataset? Il dataset è completo (cioè per ogni istanza tutti i valori di ogni attributo sono sempre correttamente specificati – non esistono "missing values")? Il dataset è bilanciato per quanto riguarda la classe da predire? Il livello di conoscenza (Expertise Level) è un attributo significativo nel determinare il livello di esperienza?

### Domanda 02 (Punti 3)

Verificare se il salario medio varia rispetto alla dimensione dell'impresa ("Company Size"), sia nel complesso sia relativamente al livello di esperienza. Quanti sono i data scientist che non risiedono nella nazione della impresa per cui lavorano?

### Domanda 03 (Punti 3)

Il salario ricevuto dai lavoratori (Salary in USD) è distribuito nello stesso modo nelle imprese di piccola, media e grande dimensione? Rappresentare con il/gli opportuni grafici il concetto. Il salario ha poi la stessa distribuzione all'interno dei livelli di esperienza?

### Domanda 04 (Punti 2)

Quali sono i 5 lavori (Job Title) più remunerativi?

## Parte 2: Trasformazione e Predizione (Punti 20)

### Domanda 01 (Punti 3)

Si vuole predire il valore di Experience Level sulla base degli attributi presenti nel dataset. Ricaricare il dataset originale, eliminare eventuali attributi inutili (giustificare la scelta), eliminare le istanze che eventualmente contengono valori nulli, rendere tutti gli attributi numerici utilizzando un ordinal encoder, e dividerlo in modo che 3/4 degli elementi siano contenuti in un nuovo dataset "train" e 1/4 nel dataset "test".

Allenare il train con il modello Decision Tree e valutare l'accuracy ottenuta calcolata sia sul dataset train sia sul dataset test. Confrontare i risultati ottenuti con quelli ottenuti con una predizione basata sul modello KNeighborsClassifier. Effettuare alcune considerazioni sui risultati ottenuti, tenendo in considerazione anche l'analisi della confusion matrix e la predizione effettuata da un dummy classifier.

### Domanda 02 (Punti 4)

Trovare i parametri migliori del classificatore DecisionTree. Agire sui parametri criterion e min_samples_leaf. Verificare se l'accuratezza che si ottiene con la nuova configurazione supera quella con i parametri di default ottenuta al punto 1.

### Domanda 03 (Punti 4)

Creare una pipeline che a partire dal dataset numerico utilizzato nel punto 1 applichi:

- il SimpleImputer per sostituire eventuali valori nulli
- divida in 10 bins i valori di Salary in USD
- applichi il DecisionTreeClassifier per effettuare la predizione

### Domanda 04 (Punti 1)

Estendere la pipeline del punto precedente aggiungendo a ogni feature una nuova feature che rappresenti il valore della feature normalizzato. Applicare il DecisionTreeClassifier per effettuare la predizione.

### Domanda 05 (Punti 6)

Creare una pipeline che a partire dal dataset iniziale (dopo aver tolto le colonne rimosse al punto 1):

- usi il SimpleImputer per inserire i valori nulli
- trasformi in vettori booleani (OneHotEncoder, sparse_output=False) le colonne 'Job Title', 'Employment Type', 'Company Location', 'Employee Residence'
- trasformi in valori numerici le colonne 'Year', 'Company Size'
- Applichi lo standard scaler sulla colonna Salary in USD
- applichi il DecisionTreeClassifier per effettuare la predizione

### Domanda 06 (Punti 2)

È possibile utilizzare un regressore linerare al posto del DecisionTree? In che modo?
