# Idea

Fare una sezione bibliografica sul sito, introducendo dei meccanismi per farvi collaborare gli studenti.

# Dubbi

- Catalogarla per esame, o per argomento (quindi utilizzando delle metriche bibliotecarie)?
- Come gestire le dispense degli utenti?
- Quale meccanismo introdurre per la collaborazione degli utenti?  

//  Se si vuole utilizzare il metodo delle PR di Git, facciamo fare manualmente le PR agli utenti? Oppure creiamo un bot che accetta richieste via email (secondo una nostra notazione) dagli account istituzionali e fa le PR se le proposte sono adeguate?
- Collocare tutto in un'unica pagina, o generare pagine per ciascuna tipologia?

# Proposta

- Fare un crawler che prenda dalle pagine degli esami siti in [insegnamenti attivati](http://www.dm.unipi.it/webnew/it/cds/insegnamenti-attivati) le bibliografie e i titoli dei relativi esami.
- Generare via Hugo le pagine relative a ciascun esame.
- Creare una repo pubblica e permettere agli utenti di fare pull request, sotto nostra moderazione.
- Scrivere una guida per spiegare agli utenti come farlo, nel modo più agevole per la piattaforma scelta

