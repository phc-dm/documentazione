
# Kolmogorov

Kolmogorov essenzialmente svolge tre funzioni per tutto il sistema. 

1. ha il pieno controllo di tutte le [macchine virtuali](#1-macchine-virtuali);

2. ha il [firewall](#2-firewall);

3. contiene i  file per i certificati di [ldap](#3-ldap) (servizi interni)

## 1. Macchine Virtuali

I file di configurazione si trovano principalmente in `/etc/xen` e mentre altri file di configurazione delle macchine si trovano in `/etc/xen-tools`

### VMs

Descrizione delle macchine virtuali attive su Kolmogorov.

- [prova-web](./prova-web) Macchina di testing per il nuovo sito di Poisson del PHC

- [ssh2](./ssh2) Macchina per fare prove prima di sostituirla con la macchina `ssh` principale.

- [service](./service) Macchina che gestisce gli account con LDAP.

### Comandi

- `xl` serve per tirare su, spegnere etc

- `xen-create-image` è una collezione di script che servono a creare in modo automatico macchine virtuali

    `xen-create-image` mette i file di configurazione delle macchine virtuali che crea in `/etc/xen`, quindi tutti i seguenti comandi vanno lanciati da lì.

- `xen-delete-image` elimina le macchine virtuali che non servono più

- `xl list`

    Con 'xl list' vengono mostrate le macchine attualmente accese. Questo è un esempio di output:
    ```
    Name                                        ID   Mem VCPUs      State   Time(s)
    Domain-0                                     0 17945     8     r-----  173084.6
    prova-web                                    2   512     2     -b----  112479.3
    ssh2                                        13  4096     2     -b----  217937.6
    log-phc                                     14   512     1     -b----    2119.1
    service                                     15   512     2     -b----   18210.3
    mail                                        16   512     2     -b----    9538.8
    maillist                                    17   512     2     -b----    6658.9
    ssh                                         18  4096     2     -b----   12738.6
    web                                         19   512     2     -b----   13193.6
    ...
    ```
    Da qui si possono visualizzare **ID** e **Name** delle macchine accese, le quali possono essere spente tramite il comando 
    `xl shutdown ...`.
    
- `xl create <path_to_config_file>`	
    
    Per avviare una macchina invece si utilizza il comando `xl create path` dando come path il file di configurazione della macchina. Tutti i file di configurazione si trovano in `/etc/xen`.

- `xl shutdown <id>` (oppure `xl shutdown <name>`]

- `xl destroy <id>` (più brutale di shutdown, da tenere a mente, oppure `xl destroy <name>`)
    
    Il comando `xl destroy ...` fa fondamentalmente quel che fa `xl shutdown`, ma in maniera più brutale e rapida, va usato con cautela perchè potrebbe interrompere processi in corso nella macchina. 

## 2. Firewall

Essenzilamente tutto il firewall è gestito da un modulo del kernel e questo viene configurato/controllato tramite i comandi `iptables` e `ip6tables`.

Il primo serve per fare controllo a livello di IPv4 e il secondo per IPv6. Nello specifico noi abbiamo uno script in bash che configura il firewall: `/etc/firewall.`

### iptables / ip6tables

Essenzialmente un comando _iptables_ (o _ip6tables_) è composto da due tipi di parametri opzionali:

1. il parametro **regola**
    
    Le _regole_ sono dei filtri che decidono per un pacchetto se applicare l'azione che è nella seconda parte del comando.

2. il parametro **azione**
    
    Le _azioni_ decidono cosa fare con il pacchetto che è stato riconosciuto dalle regole. 
    Tra le azioni più importanti ci sono, oltre ad `ACCEPT` (che essenzialmente fa passare il pacchetto), `DROP`, che butta nel cestino il pacchetto senza dare nessuna risposta al mittente, `REJECT`, che blocca il pacchetto, ma avvisa il mittente che il pacchetto è stato filtrato, ma anche altra roba (`FORWARD`, `nat` etc) che può servire a reinoltrare il pacchetto da altre parti.

#### Esempio

- `iptables -A INPUT -p tcp --dport <port> -d <ipv4> -j ACCEPT`

La prima parte (`-A INPUT -p tcp.... -d <ipv4>`) è la regola per ogni pacchetto che arriva in input (`-A INPUT`), con il protocollo tcp (`-p tcp`), sulla porta `<port>` (`-dport <port>`) e indirizzato all'indirizzo `<ipv4>` (`-d <ipv4>`) bisogna applicare l'azione (`-j ACCEPT`).

### Comandi

- `cat /etc/firewall` Configurazione delle _iptables_.
- `iptables` comando del firewall per controllo a livello IPv4
- `ip6tables` comando del firewall per controllo a livello IPv6

## 3. LDAP

TODO

## Miscelanea

- `tmux -S /tmp/new.tmux attach-session -t prove-con-tmux` per condividere un terminale con tmux.