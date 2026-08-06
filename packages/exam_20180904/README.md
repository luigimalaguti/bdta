# Exam

> **Big data and text analysis**
>
> Data: *2018-09-04*

## Parte 0: Il Dataset

Il file weather.csv contiene dati meteo rilevati in alcune città australiane. Si vuole predire se il giorno successivo pioverà. Lo schema del dataset è il seguente:

- Month: mese in cui avviene la rilevazione del dato
- Location: città in cui avviene la rilevazione
- MinTemp, MaxTemp: temperature minima e massima
- Rainfall: quantitativo di pioggia caduta
- WindGustSpeed, WindSpeed9am, WindSpeed3pm: misurazioni relative al vento
- Humidity9am, Humidity3pm: misurazioni relative all’umidità
- Pressure9am, Pressure3pm: misurazioni relative alla pressione
- Cloud3pm: nuvolosità in ottavi: https://it.wikipedia.org/wiki/Okta
- Temp9am, Temp3pm: misurazioni relative alla temperatura
- RainToday, Yes/No
- RainTomorrow, la classe da predire

Note: Creare una cartella esame e scaricare in essa il file csv che si trova al [link](http://bit.ly/BDAweather2018).

## Parte I: Analisi (Punti 10)

### Domanda 01 (Punti 2)

Quante sono le istanze contenute nel dataset? Il dataset è completo (cioè non esistono valori nulli)? Il dataset è bilanciato per quanto riguarda la classe da predire? Il numero di rilevazioni per città è bilanciato?

### Domanda 02 (Punti 3)

Rappresentare in un grafico la frequenza delle rilevazioni mensili per città.

### Domanda 03 (Punti 3)

Calcolare per ogni città e per ogni mese l’umidità minima e la massima.

### Domanda 04 (Punti 2)

Creare un nuovo attributo "TemperatureRange" che mostri l’escursione termica giornaliera. Rappresentare in un grafico l’escursione massima mensile.

## Parte II: Trasformazione e Predizione (Punti 20)

### Domanda 01 (Punti 4)

Si vuole predire la possibilità di avere pioggia il giorno successivo (RainTomorrow è la classe da predire). Trasformare i valori degli attributi RainToday e RainTomorrow da No a 0, e da Yes a 1. Creare un nuovo dataset chiamato reduce con le istanze del dataset per le quali c’è un valore di Cloud3pm maggiore o uguale a 0.

Dividere il dataset in modo che 4/5 degli elementi siano contenuti in un nuovo dataset "train" e 1/5 in un dataset "test". Valutare l’accuracy ottenuta con il classificatore Logistic Regression e il Decision Tree.

Il valore di accuratezza ottenuto è pari a? La confusion matrix evidenzia delle peculiarità?

### Domanda 02 (Punti 2)

Che valore di accuratezza si ottiene con un 5 Fold cross validation e il classificatore basato su Decision Tree? E quello basato su Logistic Regression? Il valore di accuratezza maggiormente rappresentativo è quello che si ottiene con questa tecnica o con quella attuata in precedenza?

### Domanda 03 (Punti 4)

Si introduca un attributo che sostituisca per ogni rilevazione i due valori di temperatura "MinTemp, MaxTemp" con il valore medio delle registrazioni. Si faccia lo stesso con vento (WindSpeed9am, WindSpeed3pm). Che valore di accuratezza si ottiene?

### Domanda 04 (Punti 4)

Si riparta dal dataset originario e si considerino due nuovi dataset ottenuti rimuovendo dal dataset di partenza gli elementi con Cloud3pm minore di 0. Il dataset con i valori negativi si chiamerà cloudP, l’altro cloudT. Si alleni un regressore su cloudT per predire i valori di Cloud3pm. Si usi il modello per sostituire in cloudP il valore predetto per Cloud3pm.

### Domanda 05 (Punti 3)

Si consideri il dataset ottenuto concatenando cloudP e cloudT in un unico dataset e si confronti l’accuratezza che si ottiene con un 10 Fold cross validation e il classificatore basato su Decision Tree e quello basato su Logistic Regression con quella ottenuta al punto 3.

### Domanda 06 (Punti 3)

Utilizzare un algoritmo di regressione da applicarsi al dataset del punto 1 per effettuare la predizione. Arrotondare i valori predetti all’intero. Confrontare i risultati ottenuti con quelli ottenuti nei punti precedenti.
