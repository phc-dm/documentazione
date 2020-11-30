# ssh

Macchina con le home degli utenti e con le cartelle public_html per le pagine web degli  utenti.

- `/root/nuovi-utenti-{year}`

    Cartelle con gli script di ogni anno per la creazione dei nuovi utenti.

- `/home/{username}` 

    Home degli utenti di Poisson.

- `/home/{username}/public_html` 

    Link simbolico alla cartella `/data/public_html/{username}/` per le pagine web degli utenti.

## Creazione Nuovi Account

Al momento c'è una libreria in Python che permette di interagire con LDAP in `kolmogorov:/root/codice-python`, i file importanti sono `utenti_ldap.py` e `crea_utenti_di_massa.py`, il primo contiene le classi della libreria mentre la seconda uno script di utiliy per creare utenti in massa a partire da un file.

A partire dall'anno scorso stiamo iniziando ad usare la convezione di tenere i file relativi alla creazione dei nuovi utenti per l'anno corrent in `ssh:/root/nuovi-utenti-{year}`. 

Per l'effettiva creazione degli utenti l'idea di base è eseguire un interpreter di Python (`python3` o anche `ipython3`), e importare il modulo per la creazione degli utenti in massa ed eseguire manualmente l'unica funzione del modulo (che chiama a sua volta la funzione `aggiungi_utente` che per precauzione ha un tempo d'attesa integrato di circa 5s).

### 2019/2020

Quest'anno avevamo migliorato leggermente `crea_utenti_di_massa.py` e iniziato la convezione delle cartelle `ssh:/root/nuovi-utenti-{year}`.

### 2020/2021

Abbiamo copiato la cartella con gli script da _kolmogorov_ a _ssh_ e ulteriormente migliorato lo script in Python di `crea_utenti_di_massa.py`, ora il file di input è un [tsv](https://en.wikipedia.org/wiki/Tab-separated_values) con username, nome, cognome, email d'ateneo e separato da `\t` ed è predisposto per generare dei pdf per ogni utente con le credenziali per accedere a Poisson.

