# bdta

> Corso: **Big data and text analysis**
>
> Argomento: *Data analysis*

Questo repository contiene tutta la sezione pratica del corso *Big data and text analysis* riguardo **Data analysis**. Il repository è impostato come un workspace, ogni package del workspace corrisponde a un singolo esercizio di laboratorio o prova d'esame. Di conseguenza, al loro interno saranno presenti tutte le informazioni riguardo il dominio applicativo.

## Struttura

Di seguito viene mostrata la struttura generale del repository.

```
.
├── .gitignore                          # Git-Ignore generale del workspace
├── scripts                             # Folder contenente script di utilità per la gestione del workspace
│   └── ...
├── docs                                # Documentazione con tutte le informazioni non riguardanti i singoli esercizi o esami
│   └── ...
├── .zed                                # Configurazione dell'editor Zed
│   └── ...
├── ...
└── packages                            # Folder contenente i package del workspace
    ├── boilerplate                     # Package di boilerplate, da cui partire per ogni nuovo esercizio o esame
    │   ├── README.md                   # Traccia dell'esercizio o esame in formato testuale
    │   └── src                         # Folder contenente il codice sorgente del package
    │       └── ...
    └── ...                             # Altri package, ognuno corrispondente a un esercizio o esame, con la stessa struttura del boilerplate
```
