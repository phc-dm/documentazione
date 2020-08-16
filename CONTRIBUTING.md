# Contribuire

Per contribuire alla documentazione, il vostro *pull request* necessità di
adempire a determinati standard.

## Impaginazione

Per l'impaginazione del markdown, il nostro *repository* segue la specifica di
[Versioned Markdown](https://github.com/bobertlo/vmdrima di fare un *commit*).
Non dovrebbe causarvi problemi con markdown comune (ad esempio
[CommonMark](https://commonmark.org/)). Per verificare il corretto
funzionamento, installate il pacchetto `vmdfmt` di attraverso i comandi di `go`.
Se avete `go` installato sul vostro sistema e configurato correttamente, per installare il pacchetto eseguite:
```sh
go get https://github.com/bobertlo/vmd/tree/master/cmd/vmdfmt
```

Dopo aver installato il pacchetto, potete impaginare un file eseguendo:

``````
vmdfmt -w <percorso>
``````

Per impaginare tutti i file presenti nel *repository*, eseguite:

``````
vmdfmt -w -l <percorso>
``````

## Apporre modifiche

Dopo aver verificato che la composizione è corretta, usate i comandi `git` per
aggiungere le vostre modifiche al *repository*:

``````
git add <file modificati>
git commit
git push --set-upstream-origin origin <ramo>
``````

Il messaggio del *commit* deve essere della forma `<file>: <descrizione delle
modifiche>`. I *pull request* devono contenere un singolo *commit* relato ad un
file; se vengono apportate modifiche successivamente ad un *commit*,
aggiungetele a quello precedente via `git commit --amend`. Per aggiungerlo al
vostro *repository*, il comando dovrà forzare la storia con `git push --force`.
Per *commit* multipli, dovete usare `git rebase`.

## Riferimento
Questa guida è basata su quella di [Void Linux Handbook](https://github.com/void-linux/void-docs/blob/master/CONTRIBUTING.md), che vi invogliamo a leggere qualora abbiate bisogno di esempi sullo stile dei *commit* e di presentazione.
