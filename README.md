# Handelsplatform

Et værktøj til at følge markedet løbende og få genereret konkrete handelsforslag,
som brugeren selv vurderer og udfører manuelt i Nordnet.

## Status

Projektet er under opstart. Der er endnu ikke skrevet kode.

## Vigtig forudsætning: Nordnet har ikke et API til private

Nordnet skriver i deres egen FAQ:

> "Nordnet erbjuder för närvarande inget API (Application Programming Interface)
> för privatpersoner som vill hämta data eller automatisera sin handel."

Kilde: https://www.nordnet.se/faq/handel-vardepapper/handelsapplikationer/erbjuder-nordnet-api

Der findes ganske vist en dokumenteret "Nordnet External API v2"
(https://www.nordnet.se/externalapi/docs/api), men adgang til den er ikke
åben for private kunder ifølge FAQ'en ovenfor.

**Konsekvens for designet:** Platformen kan ikke lægge ordrer ind i Nordnet
automatisk. Den kan overvåge markedet, analysere og fremlægge et forslag —
selve handlen udføres manuelt af brugeren i Nordnets egen app eller hjemmeside.
Det er også den ansvarsmæssigt reneste model: et menneske træffer beslutningen.

## Tiltænkt arkitektur

- **Frontend:** Next.js (React), deployet på Vercel.
- **Markedsdata:** ekstern udbyder via API. Valget er ikke truffet endnu —
  kandidater er bl.a. EOD Historical Data, Finnhub, Twelve Data og Alpha Vantage.
  Bemærk: rigtig realtidsdata for nordiske aktier (Nasdaq Copenhagen/Stockholm)
  koster typisk penge; gratis niveauer leverer ofte forsinkede kurser.
  Priser og vilkår skal verificeres hos udbyderen, før vi vælger.
- **Analyselag:** regler og indikatorer, der omsætter kursdata til et forslag
  med begrundelse.
- **Portefølje:** indtastes manuelt eller importeres fra CSV-eksport fra Nordnet,
  da der ikke er API-adgang.

## Kom i gang

Endnu ikke relevant — der er ingen kode i repoet.

## Forbehold

Dette er et informations- og analyseværktøj. Det er ikke investeringsrådgivning,
og forslag fra systemet er ikke en anbefaling. Al handel sker på eget ansvar.
Historisk afkast er ikke en pålidelig indikator for fremtidigt afkast.
