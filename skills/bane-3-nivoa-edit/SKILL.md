---
name: bane-3-nivoa-edit
description: Montiraj Baneov vertikalni talking-head video u formatu tri ocene (LOŠE, DOBRO, SUPER), sa logotipima alata i žutom karticom teme. Koristi kada govornik redom ocenjuje tri opcije po kategoriji; za druge Baneove edit stilove koristi odgovarajući skill.
---

# Bane 3 nivoa edit

Napravi Remotion kompoziciju u kojoj originalni snimak i zvuk teku neprekinuto, a iznad govornika se za svaku kategoriju pojavljuju tri ocene i pripadajući logotipi. Žuta kartica na trupu imenuje trenutnu temu. Referentni video služi kao vizuelni uzor; najnovije korisnikove instrukcije određuju konkretne reči, rangiranje, alat, raspored i odobrenje za izvoz.

## Priprema

1. Pregledaj izvorni i referentni video: dimenzije, trajanje, slobodan prostor iznad glave, položaj lica i raspored grafika. Poslušaj izvor **lokalnim Whisperom pre montaže**. Whisper može pogrešno prepoznati srpski govor i nazive alata; proveri sporna mesta slušanjem i korisnikovom skriptom.
2. Napravi vremensku mapu kategorija prema stvarnom redosledu govora. Za svaku zabeleži početak, kraj, temu i po tri alata u kolonama LOŠE / DOBRO / SUPER. Ako se pisana skripta i snimak razlikuju po redosledu, uskladi grafike sa govorom. Ako se razlikuje samo formulacija teme, napiši kratku, čitljivu karticu.
3. Popiši sve potrebne logotipe i proveri folder koji je korisnik naveo. **Pre montaže pitaj samo za logotipe koji nedostaju** ili za zamenu neupotrebljivog fajla. Ne koristi logo drugog proizvoda kao zamenu bez dogovora. Sačuvaj prozirnost i odnos stranica; široke slike poput Flow naslovne slike prikaži u okviru sa `objectFit: 'contain'`.

## Raspored i animacija

- Za vertikalni kadar 1080 × 1920 kreni od centara tri kolone **x = 290, 540, 790**. To je zbijen raspored iz aktuelnog primera. Ocene su u prvom redu, logotipi tačno ispod svojih ocena, nazivi ispod logotipa. Podesi pozicije prema konkretnom snimku, ali očuvaj jednake razmake među kolonama i spreči preklapanje najdužih naziva.
- Polazna geometrija primera: kartice ocena na y ≈ 148, veličina oko 176 × 68; logotipi na y ≈ 235 u okviru oko 134 × 118; naziv alata ispod. Kartica teme je žuta, crnim krupnim slovima, oko y ≈ 1210. Sve mere su početna tačka, ne obaveza: lice, usta, ruke i važan deo kadra moraju ostati vidljivi.
- Paleta ocena: crvena za **LOŠE**, žuta za **DOBRO**, zelena za **SUPER**. Ako korisnik zatraži „OKEJ“ ili drugi tekst, zameni samo natpis. Nazivi alata imaju jak kontrast sa pozadinom. Tema je kratka, po mogućnosti pitanje, kao „AI slike?“.
- Ocene stoje tokom cele kategorije. Logotipe otkrivaj redom, na odgovarajuću izgovorenu ocenu ili gest, kratkim pop ulaskom. Ne prikazuj sve tri opcije prerano. Na promeni kategorije očisti prethodne logotipe i temu. Ne dodaj automatski titlove, muziku, rezove ili zumove ako ih korisnik nije tražio ili referenca ne zahteva.
- Izvorni video i zvuk postavi jednom kroz celu kompoziciju. Za svaku kategoriju napravi zasebnu vremensku sekvencu u Remotionu. Animacije veži za `useCurrentFrame()` i `useVideoConfig()` da pregled i eventualni izvoz daju isti kadar na istoj vremenskoj tački. Resurse drži lokalno u `public/` i referenciraj preko `staticFile()`.

## Pregled i završetak

Otvori Remotion Studio čim projekat može da se pokrene i ostavi pregled korisniku. Proveri po jedan kadar svake kategorije sa sva tri logotipa, prelaze između kategorija i najduže nazive; posebno proveri razmak među kolonama i da grafike ne zaklanjaju lice. Pokreni proveru tipova, lint i formatiranje izmenjenih fajlova. Kontrolni nepokretni kadrovi su dozvoljeni za proveru rasporeda.

**Ne izvozi MP4 dok korisnik ne pogleda pregled i izričito ne zatraži izvoz.** Korekcije prvo prikaži u Studio pregledu. Posle dozvoljenog izvoza proveri trajanje, rezoluciju, fps, audio tok i reprezentativne kadrove, pa dostavi važeći video fajl.

