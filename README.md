# EIA-SEA Atlas

*English:* open prototype of a public, georeferenced European map of works and plants subject to environmental assessments and permits (EIA, SEA, IED/IPPC and more). Each site has its own digital file. All data are made up. Contributions welcome.

Prototipo di una **mappa pubblica europea georeferenziata** delle opere e degli impianti soggetti a valutazioni e autorizzazioni ambientali.

L'idea: ogni opera ha un proprio **fascicolo digitale** (valutazioni, autorizzazioni, prescrizioni, controlli, storico dei procedimenti) che chiunque può consultare e scaricare, dall'intero territorio dell'Unione fino al comune, senza dover sapere a quale ufficio rivolgersi.

> **Attenzione:** questo è un prototipo dimostrativo. Tutti i dati sono inventati e i punti sulla mappa non corrispondono a opere reali.

## Provarlo

1. Scarica `index.html`.
2. Aprilo con un browser (Chrome, Firefox, Safari o Edge) con la connessione internet attiva: le carte arrivano da server esterni (OpenTopoMap e OpenStreetMap).
3. Scegli la scala (Unione europea, Paese, Comune) e clicca un punto per aprire la scheda dell'opera.

Versione online (GitHub Pages): https://nalomb2009.github.io/eia-sea-atlas/

**Perché questo nome:** EIA e SEA sono i nomi inglesi della valutazione di impatto ambientale (VIA) e della valutazione ambientale strategica (VAS).

## Cosa fa

- Pagina unica in HTML, CSS e JavaScript, senza framework e senza server.
- Mappa con [Leaflet](https://leafletjs.com): carta fisica con rilievo ([OpenTopoMap](https://opentopomap.org)) e carta stradale ([OpenStreetMap](https://www.openstreetmap.org)), con selettore.
- Tre scale di partenza: Unione europea, Paese, Comune.
- Due livelli facoltativi con dati reali dell'Agenzia europea dell'ambiente (EEA): aree Natura 2000 e siti industriali del Portale europeo sulle emissioni industriali. Questi dati non indicano lo stato delle autorizzazioni e restano separati dai punti dimostrativi.
- Cinque lingue (italiano, inglese, spagnolo, francese, portoghese), scelte dal selettore in alto a destra o con un link diretto, per esempio `?lang=en`. Le traduzioni vanno riviste da madrelingua.
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
| `DICT` | Le traduzioni dei testi della pagina e delle schede, un blocco per lingua |
| `PROVIDERS` | I fornitori delle carte, provati in ordine |
| `renderLeaflet` / `renderFallback` | Disegno dei punti sulla mappa dettagliata o su quella schematica |

Ogni punto è `[latitudine, longitudine, stato, modello, codice, posizione]`, con stato `ok`, `proc` oppure `irr`.

## Come contribuire

Apri una *Issue* per proporre un'idea o segnalare un problema, oppure una *Pull Request* con una modifica. Cose da fare:

- [ ] Collegare dati reali: servizi INSPIRE nazionali (da verificare uno per uno, le condizioni d'uso cambiano) e dati del Portale europeo sulle emissioni industriali oltre alla sola visualizzazione
- [ ] Definire lo schema del codice europeo unico dell'opera
- [ ] Ricerca per territorio, indirizzo, tipologia di attività e soggetto responsabile
- [ ] Elenco e download dei documenti del fascicolo, con storico di rilasci, modifiche, rinnovi, sospensioni e revoche
- [ ] Modulo per segnalare opere non censite o informazioni mancanti o non aggiornate
- [ ] Verifica di accessibilità (WCAG) e traduzione nelle lingue dell'Unione
- [ ] Raggruppamento dei punti alle scale più ampie e caricamento della sola zona visibile
- [ ] Revisione delle traduzioni da parte di madrelingua e nuove lingue (si copia un blocco di `DICT`, si traduce, si aggiunge il codice lingua a `SUPPORTED` e una voce al selettore)
- [ ] Passare a un fornitore di carte adatto a un uso con molto traffico (i server pubblici di OpenStreetMap hanno limiti d'uso)

## Componenti e licenze di terze parti

- **Leaflet 1.9.4**: licenza BSD a due clausole.
- **OpenTopoMap** (carta fisica con rilievo): stile con licenza CC-BY-SA, dati OpenStreetMap e SRTM, attribuzione già nel codice. Il servizio ha limiti d'uso: per molto traffico serve un fornitore dedicato.
- **Dati EEA** (Natura 2000 e siti industriali): servizi di mappa pubblici dell'Agenzia europea dell'ambiente. Il riutilizzo è consentito citando la fonte (attribuzione già nel codice), salvo condizioni specifiche del singolo dataset da verificare.
- **OpenStreetMap**: dati con licenza ODbL, con obbligo di citare i contributori (già presente nel codice).
- **CARTO** (carte di riserva basate su OpenStreetMap): richiede attribuzione; prima di un uso stabile vanno verificate le condizioni d'uso.
- **Literata** e **Public Sans**: caratteri caricati da Google Fonts, licenza SIL Open Font.

## Licenza

Licensed under the EUPL. Il codice è distribuito con la [European Union Public Licence v. 1.2](LICENSE.txt) (EUPL-1.2).
