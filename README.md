# eOcene

Brezplačen šolski prostor za dijake od 15. leta. Prijava uporablja e-pošto in geslo. Aplikacija vsebuje ocene in povprečja, predmete s cilji, kalkulator, koledar, Pomodoro, zasebni učni čas, obvestila, prostovoljne lestvice in tutorstvo.

- Aplikacija: https://www.eocena.app
- Upravljanje: https://www.eocena.app/upravljanje
- Podpora: eocene.support@gmail.com

## Izvedba

React in Vinext, podatkovna zbirka D1 in shramba datotek R2 na gostovanju Sites. Projekt uporablja obstoječo identiteto v `.openai/hosting.json`. Prijava in pravice so implementirane v `lib/auth.ts` in se preverjajo na strežniku. Skrivnosti niso del izvorne kode.

Glavne mape so `app/` za vmesnik, `lib/` za pravila in strežniške storitve, `drizzle/` za migracije ter `tests/` za preverjanja. Objavljena pravila so v `lib/legal.ts`, njihova različica v `lib/domain.ts`, obvestilo o izdaji v `lib/release.ts`.

## Preverjanje in objava

Za vsak sklop preverjanj uporabi `node tests/<ime>.cjs`. Preverjanje tipov: `node node_modules/typescript/bin/tsc --noEmit --incremental false`. Gradnjo in objavo izvedi s podprtim postopkom Sites. Migracije se ohranjajo in dodajajo po vrsti. Ne ponavljaj že uporabljenih migracij.

Navodila za upravljanje so v `docs/PRIJAVA-IN-UPRAVLJANJE.md`, pravila hrambe in funkcij v `docs/ZASEBNOST-IN-KOLEDAR.md`. Evidenca pregleda je v `docs/PREGLED-2026-10-15.md`.
