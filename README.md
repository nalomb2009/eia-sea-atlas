# EIA-SEA Atlas

*English:* open prototype of a public, georeferenced European map of works and plants subject to environmental assessments and permits (EIA, SEA, IED/IPPC and more). Each site has its own digital file. All data are made up. Contributions welcome.

Prototipo di una **mappa pubblica europea georeferenziata** delle opere e degli impianti soggetti a valutazioni e autorizzazioni ambientali.

L'idea: ogni opera ha un proprio **fascicolo digitale** (valutazioni, autorizzazioni, prescrizioni, controlli, storico dei procedimenti) che chiunque può consultare e scaricare, dall'intero territorio dell'Unione fino al comune, senza dover sapere a quale ufficio rivolgersi.

> **Attenzione:** questo è un prototipo dimostrativo. Tutti i dati sono inventati e i punti sulla mappa non corrispondono a opere reali.

## Provarlo

1. Scarica `index.html`.
2. Aprilo con un browser (Chrome, Firefox, Safari o Edge) con la connessione internet attiva: le carte arrivano dai server di OpenStreetMap.
3. Scegli la scala (Unione europea, Paese, Comune) e clicca un punto per aprire la scheda dell'opera.

Per avere un indirizzo web pubblico e gratuito: **Settings → Pages → Deploy from a branch → `main` / `(root)`**. Dopo un minuto il sito è visibile su `https://NOME-UTENTE.github.io/NOME-REPOSITORY/`.

## Cosa fa

- Pagina unica in HTML, CSS e JavaScript, senza framework e senza server.
- Mappa dettagliata con [Leaflet](https://leafletjs.com) e le carte di [OpenStreetMap](https://www.openstreetmap.org).
- Tre scale di partenza: Unione europea, Paese, Comune.
- Tre stati delle opere (titoli in regola, procedimento in corso, titoli mancanti), distinti da colore **e** forma.
- Scheda dell'opera con codice identificativo, posizione, responsabile, amministrazioni competenti e stato di ogni titolo.
- Mappa schematica di riserva, se le carte non si caricano.
- Modalità scura, navigazione da tastiera e rispetto della riduzione del movimento.

## Come è fatto il codice

Tutto è in `index.html`:

| Elemento | Cosa contiene |
|---|---|
| `TPL` | I modelli di opera e l'elenco dei titoli richiesti per ciascuno |
| `VIEWS` | Le tre scale, con centro, zoom e punti dimostrativi (`pts`) |
| `PROVIDERS` | I fornitori delle carte, provati in ordine |
| `renderLeaflet` / `renderFallback` | Disegno dei punti sulla mappa dettagliata o su quella schematica |

Ogni punto è `[latitudine, longitudine, stato, modello, codice, posizione]`, con stato `ok`, `proc` oppure `irr`.

## Come contribuire

Apri una *Issue* per proporre un'idea o segnalare un problema, oppure una *Pull Request* con una modifica. Cose da fare:

- [ ] Collegare dati reali: INSPIRE e Portale europeo sulle emissioni industriali
- [ ] Definire lo schema del codice europeo unico dell'opera
- [ ] Ricerca per territorio, indirizzo, tipologia di attività e soggetto responsabile
- [ ] Elenco e download dei documenti del fascicolo, con storico di rilasci, modifiche, rinnovi, sospensioni e revoche
- [ ] Modulo per segnalare opere non censite o informazioni mancanti o non aggiornate
- [ ] Verifica di accessibilità (WCAG) e traduzione nelle lingue dell'Unione
- [ ] Raggruppamento dei punti alle scale più ampie e caricamento della sola zona visibile
- [ ] Passare a un fornitore di carte adatto a un uso con molto traffico (i server pubblici di OpenStreetMap hanno limiti d'uso)

## Componenti e licenze di terze parti

- **Leaflet 1.9.4**: licenza BSD a due clausole.
- **OpenStreetMap**: dati con licenza ODbL, con obbligo di citare i contributori (già presente nel codice).
- **CARTO** (carte di riserva basate su OpenStreetMap): richiede attribuzione; prima di un uso stabile vanno verificate le condizioni d'uso.
- **Literata** e **Public Sans**: caratteri caricati da Google Fonts, licenza SIL Open Font.

## Licenza

Da definire.
