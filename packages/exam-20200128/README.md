# Exam

> **Big data and text analysis**
>
> Data: *2020-01-28*
>
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luigimalaguti/bdta/blob/main/packages/exam-20200128/src/notebook.ipynb)

## Parte 0: Il Dataset

Il datataset weather_train.csv (preso da [Kaggle](https://www.kaggle.com/nicholasjhana/energy-consumption-generation-prices-and-weather)) contiene dati relativi a rilevazioni meteo registrate in città spagnole una volta al giorno secondo il seguente schema:

- `dt_iso`
- `city_name`
- `temp`
- `temp_min`
- `temp_max`
- `pressure`
- `humidity`
- `wind_speed`
- `wind_deg`
- `rain_1h`
- `rain_3h`
- `snow_3h`
- `clouds_all`
- `weather_id`
- `weather_main'`
- `weather_description`
- `weather_icon`

Il dataset è costituito da attributi con valori numerici e categorici. L'obiettivo è quello di prevedere il tempo complessivo di una giornata (valore della feature
`weather_main`) sulla base degli altri parametri.

Note: Il file csv che si trova al [link](http://bit.ly/wea_2020).

## Parte 1: Analisi (Punti 10)

### Domanda 01 (Punti 1)

Quante sono le istanze contenute nel dataset? Il dataset è completo (cioè per ogni istanza tutti i valori di attributo sono sempre correttamente specificati - non esistono "missing values")? Il dataset è bilanciato per quanto riguarda la classe da predire?

### Domanda 02 (Punti 1)

Le rilevazioni con pressione e umidità uguale a 0 sono irreali. Quante sono queste rilevazioni? Eliminarle dal dataset.

### Domanda 03 (Punti 4)

Analizzare la temperatura massima rilevata. Valutare se la distribuzione dei valori assume un andamento simile a una gaussiana. Considerare poi le rilevazioni che si collocano all'interno del 5% delle temperature più alte. Le città sono equamente presenti in quella fascia di rilevazioni? Come è il tempo complessivo nei giorni in cui la temperatura massima è in quella fascia per ogni città?

### Domanda 04 (Punti 2)

Verificare se quando nevica la temperatura sia prossima alla temperatura di congelamento. (NOTA: il dataset riporta i valori in Kelvin)

### Domanda 05 (Punti 2)

Confrontare l'escursione termica media (`temp_max - temp_min`) registrata nei giorni in cui nevica, con quella delle giornate che sono all'interno del 5% delle temperature più alte

## Parte 2: Trasformazione e Predizione (Punti 20)

### Domanda 01 (Punti 4)

Si vuole predire il valore di `weather_main` sulla base degli attributi presenti nel dataset. Dividere il dataset in modo che 2/3 degli elementi siano contenuti in un nuovo dataset "train" e 1/3 nel dataset "test".

Eliminare gli attributi `[dt_iso, city_name, weather_description, weather_icon, weather_id, clouds_all]`. Convertire l'attributo `weather_main` in numerico in maniera opportuna.

Allenare il train con il modello Decision Tree e valutare l'accuracy ottenuta calcolata sia sul dataset train sia sul dataset test. Confrontare i risultati ottenuti con quelli ottenuti con una predizione basata sul modello Logistic Regression. Effettuare alcune considerazioni sui risultati ottenuti, tenendo in considerazione anche l'analisi della confusion matrix.

### Domanda 02 (Punti 1)

Confrontare l'accuratezza ottenuta nel punto precedente con l'accuratezza che si ottiene con un una 10 Fold cross validation.

### Domanda 03 (Punti 3)

Utilizzare la funzione Normalizer per normalizzare i valori del dataset e confrontare se l'accuratezza ottenuta con il Decision Tree Classifier migliora.

### Domanda 04 (Punti 2 + 2)

Creare una pipeline con trasformatori PCA (si scelgano 5 attributi) e poi Normalizer. Si usi come modello il Decision Tree Classifier. (2 punti ulteriori se gli attributi della PCA sono aggiunti agli attributi del dataset)

### Domanda 05 (Punti 4)

Utilizzare la funzione di gridSearchCV sulla pipeline per modificare il numero di attributi selezionati dalla PCA e alcuni parametri a piacere del classificatore. Verificare se l'accuratezza che si ottiene con la nuova configurazione supera quella standard ottenuta al punto 1.

### Domanda 06 (Punti 2)

Si verifichi l'accuratezza ottenuta dalla pipeline del punto 4 con il file weather_test. I risultati corretti sono nel file class.csv. Controllare le features presenti nei dataset.

### Domanda 07 (Punti 2)

Si sperimenti una pipeline come quella del punto 4 dove al posto del classificatore si utilizzi un regressore lineare. Il risultato dovrà essere approssimato all'intero per il calcolo dell'accuratezza.
