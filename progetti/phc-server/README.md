# server-poisson

Server in Go che gestisce le pagine principali del nuovo sito, in fase di sviluppo in https://github.com/phc-dm/server-poisson. 

## Implementazione

- [Echo Web Framework](https://echo.labstack.com/) &mdash; https://github.com/labstack/echo

    Sembra un framework abbastanza usato ed ha molte stelle.

- [Hugo](https://gohugo.io) &mdash; Generatore statico di blog scritto in Go.

    Tutta la parte di contenuti: blog, notizie, guide, etc. Verrà gestita da Hugo e servita sotto l'url `/blog` ed in teoria sarà sotto `content-poisson`.

## Design

Raccolta di materiale usato.

### Fonts

- Share 700: per le intestazioni
- Ubuntu 300, 700: per il testo.
- Ubuntu Mono: per i blocchi di codice

### Assets

- Icone da icons8.it