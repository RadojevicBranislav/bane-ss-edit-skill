---
name: bane-2-nivoa
description: Montiraj Baneov vertikalni talking-head video sa dve uporedne kolone, levom i desnom labelom, logotipima i žutom karticom teme. Koristi za isti stil kao „bane-3-nivoa-edit“ kada se porede dve opcije; tačan tekst labela mora doći od korisnika.
---

# Bane 2 nivoa

Napravi Remotion edit u stilu Baneovog videa sa tri nivoa, ali sa **dve kolone**. Govornik i originalni zvuk teku neprekinuto; pri svakoj temi levo i desno stoje korisnikove labele, pripadajući logotipi se otkrivaju u ritmu govora, a žuta kartica na trupu označava temu. Najnovije korisnikove instrukcije imaju prednost nad ovim podrazumevanim stilom.

## Obavezan unos pre montaže

**Pre početka editovanja konkretnog videa pribavi tačan tekst obe labele.** Ako ih korisnik već nije izričito naveo sa redosledom, pitaj: „Koji je tačan tekst leve, a koji desne labele? Pošalji i željeno pisanje velikih/malih slova.“ Sačekaj odgovor pre postavljanja grafika. Primeri kao „plaća se“ i „besplatno/džabe“ nisu konačan izbor i ne smeju se preuzeti kao labele bez korisnikove potvrde. Ako su obe labele već jasno date, upotrebi ih bez ponovnog pitanja.

## Priprema

1. Pregledaj izvorni i referentni video: trajanje, dimenzije, slobodan prostor iznad glave i položaj govornika. Poslušaj izvor **lokalnim Whisperom pre montaže**. Proveri nazive i sporna mesta slušanjem jer Whisper može pogrešiti srpski govor.
2. Zapiši redosled tema prema snimku, njihove vremenske granice i po dve opcije u korisnikovom levom/desnom redosledu. Ako se pisani plan i govor razlikuju, veži pojavljivanje grafika za stvarni govor i razjasni suštinsko neslaganje pre editovanja.
3. Najpre proveri korisnikov folder `G:\My Drive\content ikonice` za logotipe, zatim već dostupne lokalne resurse. Pre montaže traži samo potrebne logotipe koji zaista nedostaju ili zamenu za neupotrebljiv fajl. Ne podmeći logo drugog proizvoda. Sačuvaj odnos stranica i prozirnost. Za Claude Code, Claude Design i druge Claude varijante koristi regularni Claude logo, uz tačan naziv varijante ispod njega.

## Raspored i animacija

- Za kadar 1080 × 1920 kreni od centara logotipa **x = 270 levo, x = 810 desno**. Svaka labela stoji iznad svog logotipa, naziv alata ispod. Kao početni raspored za uspravni kadar sa slobodnim prostorom iznad glave koristi labele na oko **y = 186**, logotipe na oko **y = 314** i razmak između labela oko **36 px**; to je raspored nakon korisnikovog pomeranja grafika naniže za 5% visine kadra i približavanja labela. Podesi ga prema drugom kadru i gestovima, tako da nazivi ostanu iznad glave i prstiju, bez zaklanjanja lica. Daj dužim labelama dovoljno širine i proveri da se ne preklapaju.
- Koristi krupne zaobljene labele, čitljive logotipe i nazive, žutu karticu teme s crnim slovima na trupu. Za **„izbegavaj“ / „koristi“** podrazumevane boje su crvena levo i zelena desno, sa fontom labela većim nego u stilu sa tri nivoa. Za **„plaća se“ / „besplatan“** koristi tamno plavu levu i svetlo plavu desnu labelu; početni font oko **53/50 px** za 1080 × 1920, uz prilagođavanje dužini teksta. Tačan tekst, redosled i eventualne drugačije boje iz aktuelnog zahteva uvek imaju prednost. Ne zadržavaj praznu srednju kolonu iz varijante sa tri nivoa.
- Labele ostaju vidljive tokom svoje teme. Logotipe otkrivaj jedan po jedan na izgovorenu opciju ili odgovarajući gest, kratkim pop ulaskom. Pri promeni teme ukloni prethodne opcije i zameni karticu teme. Ne dodaj titlove, muziku, rezove ili zumove automatski. Ako korisnik zatraži da se deo snimka iseče, proveri kontinuitet slike i zvuka na svakom spoju i ukloni primetna seckanja.
- Postavi izvorni video i zvuk jednom kroz celu kompoziciju. Svaku temu stavi u zasebnu Remotion sekvencu; animacije veži za `useCurrentFrame()` i `useVideoConfig()`. Lokalne resurse drži u `public/` i pozivaj preko `staticFile()`.

## Pregled i izvoz

Otvori Remotion Studio i pokaži korisniku pregled. Proveri po jedan kadar svake teme sa obe opcije, najduže labele i nazive, razmak među kolonama, podignute prste i da ništa ne zaklanja lice. Pokreni proveru tipova, lint i formatiranje izmenjenih fajlova. Kontrolni nepokretni kadrovi služe samo za proveru rasporeda.

**Ne izvozi MP4 dok korisnik ne pogleda pregled i izričito ne zatraži izvoz.** Izmene prvo pokaži u Studio pregledu. Posle dozvoljenog izvoza proveri trajanje, rezoluciju, fps, audio i reprezentativne kadrove pre isporuke.

