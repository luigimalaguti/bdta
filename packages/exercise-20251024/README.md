# Banca

> **Big data and text analysis**
>
> Data: *2025-10-24*
>
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luigimalaguti/bdta/blob/main/packages/exercise-20251024/src/notebook.ipynb)

## Parte 0: Il Dataset

Carica in un dataframe il file "bank.csv" (preso da [Kaggle](https://www.kaggle.com/datasets/mathchi/churn-for-bank-customers)) che contiene dati relativi ai clienti di una banca. Lo scopo è predire se il cliente abbandonerà la banca (feature `Exited`).

## Parte 2: Trasformazione e Predizione

### Domanda 01

Quante righe e quante colonne sono presenti? Ci sono valori nulli? Il dataset è bilanciato rispetto alla classe da predire?

### Domanda 02

Converti i valori di Gender in numerici (Male = 0, Female = 1).

### Domanda 03

Trasforma la feature Geography con OneHotEncoder.

### Domanda 04

Elimina le feature `RowNumber`, `CustomerId`, `Surname` e dividi il dataset in train (75% del dataset) e test (25%). Usa *random_state=0*.

### Domanda 05

Allena un decision tree per predire l'abbandono dei clienti, scegli tu i valori dei parametri e calcola l'accuratezza della predizione.

### Domanda 06

Aggiungi una nuova feature nel dataset con il valore di `(EstimatedSalary * Tenure + Balance) / 2`. L'accuratezza della predizione migliora?

### Domanda 07

Applica due trasformazioni diverse a tutto il dataset e/o a feature specifiche, valuta la predizione.
