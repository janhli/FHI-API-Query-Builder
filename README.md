# FHI API Query Builder

En interaktiv web-applikasjon som gjør det enkelt å bygge og kjøre spørringer mot FHIs åpne statistikk-API.

## Hva er det?

FHI API Query Builder er et visuelt verktøy som lar deg utforske og hente data fra [Folkehelseinstituttets statistikk-API](https://statistikk-data.fhi.no) uten å måtte skrive API-kall manuelt. Appen har et brukervennlig grensesnitt hvor du velger data interaktivt, og får tilbake den JSON-spørringen du kan bruke i dine egne applikasjoner.

## Brukstilfeller

- **Dataanalytikere og forskere** som ønsker å hente norsk folkehelsedata for analyser
- **Utviklere** som skal integrere FHI-data i sine applikasjoner
- **Organisasjoner** som skal lage egne dashboards og rapporter basert på folkehelsesdata
- **Lærere og studenter** som skal lære om norsk folkehelsestatistikk

## Hvordan bruker jeg den?

### Trinn-for-trinn guide

1. **Åpne applikasjonen** i en moderne nettleser

2. **Velg datakilde** - I første skjerm velger du hvilken statistikkkilde du ønsker data fra
   - Se kort beskrivelse av hver kilde
   - Kildene inneholder ulike typer folkehelseinformasjon

3. **Velg tabell** - Når du har valgt en kilde, velger du hvilken tabell du ønsker
   - Du kan søke i tabellene for å finne det du trenger

4. **Konfigurer dimensjoner** - Her velger du hvilke variabler og verdier du vil ha med
   - **Filtertype**: Velg spesifikke verdier, alle verdier, eller for tidsvariabler - siste X år
   - **Geografi**: For geografiske data kan du velge alle kommuner, enkelt fylke, eller spesifikke kommune/bydel
   - **Tidsperiode**: For år-dimensjonen kan du velge enkeltår, eller siste X år
   - Klikk på "Informasjon om tabellen" for detaljer om hva tabellen inneholder

5. **Velg format og last ned/kopier** - I siste skjerm:
   - Velg responseformat (JSON-stat2, CSV med labels, eller CSV med koder)
   - Kopier JSON-spørringen direkte
   - Se forhåndsvisning av data
   - Last ned som CSV-fil

### Eksempel

Hvis du vil hente regneferdighets-data for alle 8. klassinger i Oslo kommune fra 2022-2024:

1. Velg "Regneferdighet, 5. og 8. klasse" som kilde
2. Velg tabellen for regneferdighets-data
3. Konfigurer:
   - Klassetrinn: 8. trinn
   - Geografi: Oslo (kommune)
   - År: Siste 3 år
4. Last ned som CSV eller kopier JSON-spørringen

## Om FHI Statistikk API

Denne appen bygger på [FHI Statistikk sin åpne API](https://statistikk-data.fhi.no), som tilbyr fritt tilgjengelig norsk folkehelsestatistikk.

### Ressurser

- **API-dokumentasjon**: https://statistikk-data.fhi.no
- **Datatyper**: Statistikken inneholder data om blant annet nasjonale prøver, helsedata, skoledata og mer
- **Oppdateringsfrekvens**: Varierer etter datakilde, typisk årlig eller oftere
- **Dekningsområde**: Hele Norge, med detaljer på fylke, kommune og bydel-nivå

### API-endepunkter som brukes

Appen bruker disse FHI API-endepunktene:

- `/Common/source` - Henter liste over tilgjengelige kilder
- `/{sourceId}/table` - Henter tabeller for en gitt kilde
- `/{sourceId}/Table/{tableId}/dimension` - Henter dimensjoner (variabler) for en tabell
- `/{sourceId}/Table/{tableId}/metadata` - Henter detaljert informasjon om en tabell
- `/{sourceId}/Table/{tableId}/data` - Henter faktiske data basert på spørring

## Teknisk informasjon

### Arkitektur

Appen er en single-page application (SPA) bygget med:

- **React** - For UI-komponentene
- **Vanilla JavaScript** - For logikk
- **HTML/CSS** - For grunnleggende struktur og styling

Alt kjører i nettleseren din - ingen backend-server er nødvendig.

### Hvilke formater støttes?

- **JSON-stat2** (anbefalt) - Strukturert JSON-format egnet for statistikk
- **CSV2** - CSV med labels (menneskelesbare navn)
- **CSV3** - CSV med koder (kort kodeversjoner)

### Data-struktur

Spørringer følger FHI APIets struktur:

```json
{
  "query": [
    { "code": "YEAR", "selection": { "filter": "item", "values": ["2024"] } },
    { "code": "REGION", "selection": { "filter": "item", "values": ["03", "0301"] } },
    { "code": "MEASURE", "selection": { "filter": "all" } }
  ],
  "response": {
    "format": "json-stat2"
  }
}
```

### Geo-gruppering

For geografiske data (REGION-dimensjon) håndteres følgende nivåer:

- **2 sifre** - Fylker
- **4 sifre** - Kommuner
- **6 sifre** - Bydeler (Oslo)

Appen lar deg enkelt velge "alle kommuner i fylke X" eller "alle bydeler i Oslo".

### Tidsserier

For år-dimensjonen (AAR) kan du velge:

- `filter: "item"` - Spesifikke år
- `filter: "all"` - Alle år (wildcard)
- `filter: "top"` - Siste X år

### Maksimale antall rader

Du kan sette `maxRowCount` for å begrense antall rader i responsen. La feltet stå tomt for ubegrenset.

### Feilhåndtering

Hvis noe går galt:

- Sjekk at du har valgt alle påkrevde dimensjoner
- Noen kombinasjoner av data kan være skjult av personvernhensyn (færre enn 10 enheter)
- Se konsollen (F12) for detaljer

## Kompatibilitet

- Chrome/Edge (versjon 90+)
- Firefox (versjon 88+)
- Safari (versjon 14+)
- Fungerer på mobiltelefoner og nettbrett

## Kontakt og tilbakemelding

Utviklet av Akershus analyse, en del av Akershus fylkeskommune.

- **Kontakt**: janli@afk.no
- **Om Akershus analyse**: https://akershusanalyse.no/
- **Om Akershus fylkeskommune**: https://afk.no/

## Lisens

Dataene fra FHI er tilgjengelig under [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/).

## Versjon

BETA - Appen er under utvikling. Tilbakemeldinger og forbedringer er velkommen!
