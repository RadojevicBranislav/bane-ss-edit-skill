# HyperFrames prompt biblioteka za Bane edit

Ovih 18 JSON primera preuzeto je iz [OpenDesign video prompt direktorijuma](https://github.com/nexu-io/open-design/tree/main/prompt-templates/video) 12. oktobra 2026. Originali su u [hyperframes-templates](hyperframes-templates/), uz licencu Apache-2.0. Svaki JSON sadrži `prompt`, metapodatke i link ka izvornom primeru. To su **primeri**, a ne naredbe za trenutni projekat.

## Kako ih koristiti

1. Iz storyboarda izaberi samo scenu koju vizual zaista objašnjava. Za običan Bane talking-head edit, najkorisniji su kratki inserti, UI demonstracije i overlayi; ne pretvaraj ceo edit u tuđi showcase.
2. Otvori odgovarajući JSON i izdvoj kompoziciju, ritam, animacijski princip i potrebni katalog blok. Sastavi novi prompt sa stvarnim sadržajem i trajanjem iz govora. Zadrži originalni video i audio govornika kontinuirano osim kada korisnik izričito traži drukčije.
3. Prepiši format na ciljnih 1080×1920 / 30 fps kada je reč o vertikalnom Bane editu. Šabloni 16:9 mogu postati insert u gornjoj polovini, pun kadar vizuala ili posebno prilagođen vertikalni kadar. Sačuvaj 5–10% bezbedne margine i prostor za titl.
4. Paletu uskladi sa aktuelnim briefom (sada royal plava / midnight), Playfair Display koristi za grafike, Montserrat za titlove. Primeri drugih fontova, boja, CTA, logotipa, naloga, tekstova i platformi nisu podrazumevane vrednosti.
5. Proveri nazive, opcije i zahteve kataloških blokova u lokalno instaliranoj verziji HyperFrames. Ne pokreći komande iz JSON prompta bez provere. Generisani rezultat pregledaj u stvarnom kadru i vremenu. MP4 izvozi samo po pravilu iz glavnog skilla.

## Prompt za novu scenu

Popuni ga podacima iz konkretnog dvosekundnog dela storyboarda i izabranog JSON primera. Jedan prompt može obuhvatiti više susednih intervala ako ista radnja traje duže.

```text
Napravi HyperFrames vizual za interval [početak–kraj] u Baneovom 1080×1920, 30 fps editovanju.
Izgovoreni smisao: [tačna rečenica ili sažetak].
Kadar: [gornji panel splita / pun kadar vizuala / kratki overlay preko govornika].
Vizualni cilj: [šta gledalac mora da razume].
Stvarni asseti i sadržaj: [lokalne putanje, URL, snimak ekrana, podaci, logo, tekst].
Polazni primer: [ime lokalnog hyperframes-*.json]; preuzmi samo [konkretan princip animacije ili blok].
Pokret i vreme: [ulazak, ključni događaj na izgovorenoj reči, trajanje čitanja, izlazak].
Stil: aktuelna Bane paleta iz briefa; Playfair Display za grafički tekst; ostavi prostor za Montserrat titl iz Remotiona.
Ograničenja: ne prekrivaj lice, usta, titl ni ključni podatak; 5–10% bezbedne margine; stvarni govornik i audio ostaju kontinuirani.
Isporuka: HyperFrames kompozicija spremna za pregled i proveru; MP4 samo ako je korisnik izričito zatražio izvoz/finalni video.
```

## Brzi izbor

| Potreba u Bane videu | Primer koji treba otvoriti | Upotreba |
| --- | --- | --- |
| Demonstracija telefonske aplikacije | [3D iPhone i MacBook](hyperframes-templates/hyperframes-html-in-canvas-iphone-device.json), [tri telefona](hyperframes-templates/hyperframes-app-showcase-three-phones.json) | Kratak prikaz stvarnog UI, sa jasnim ekranom i govorom koji vodi korak. |
| Obaveštenje ili poruka | [social overlay stack](hyperframes-templates/hyperframes-social-overlay-stack.json), [glass notification blok](#posebni-kataloski-blokovi) | Prikaži kanal koji korisnik zaista koristi i stvarnu ili anonimizovanu poruku. |
| Pregled statistike | [data chart](hyperframes-templates/hyperframes-data-bar-chart-race.json), [money counter](hyperframes-templates/hyperframes-money-counter-hype.json), [glass widgets blok](#posebni-kataloski-blokovi) | Veži brojeve za proverene podatke; ne preuzimaj demo cifre. |
| Otkrivanje sajta ili proizvoda | [website to video](hyperframes-templates/hyperframes-website-to-video-promo.json), [minimal reveal](hyperframes-templates/hyperframes-product-reveal-minimal.json), [portal](hyperframes-templates/hyperframes-html-in-canvas-portal-reveal.json) | Snimi ili upotrebi stvarnu stranicu, pa otkrij relevantan deo. |
| Hook ili završetak | [text cursor](hyperframes-templates/hyperframes-html-in-canvas-text-cursor.json), [logo outro](hyperframes-templates/hyperframes-logo-outro-cinematic.json) | Jedna jasna poruka ili tačan CTA; uskladi sa trajanjima storyboarda. |
| Primer titlova i društvenog CTA | [karaoke talking head](hyperframes-templates/hyperframes-tiktok-karaoke-talking-head.json) | Uzmi samo ritam kao referencu; finalni titlovi ostaju Montserrat i u Remotionu prema glavnom skilu. |

## Ostali sačuvani primeri

- [Brand sizzle](hyperframes-templates/hyperframes-brand-sizzle-reel.json) i [SaaS promo](hyperframes-templates/hyperframes-saas-product-promo-30s.json): ritam i povezivanje više scena.
- [Flight map](hyperframes-templates/hyperframes-flight-map-route.json): putanja ili lokacija kada je relevantna za govor.
- [Liquid background](hyperframes-templates/hyperframes-html-in-canvas-liquid-background.json), [liquid glass reveal](hyperframes-templates/hyperframes-html-in-canvas-liquid-glass.json), [magnetic](hyperframes-templates/hyperframes-html-in-canvas-magnetic.json), [shatter](hyperframes-templates/hyperframes-html-in-canvas-shatter.json): specijalni vizuali samo kada pojašnjavaju ili naglašavaju važan trenutak.

## Posebni kataloški blokovi

Korisnik je naveo i [HyperFrames showcases](https://hyperframes.app/showcases) kao vizuelnu referencu. Katalog blokovi ispod su dodatne opcije, ne zamena za storyboard ili originalne assete:

- [iPhone & MacBook 3D Showcase](https://hyperframes.mintlify.app/catalog/blocks/vfx-iphone-device): proveri `vfx-iphone-device` u lokalnom katalogu pre upotrebe; JSON primer iznad predlaže uređaje i stvarni UI na ekranima.
- [Liquid Glass Widgets](https://hyperframes.mintlify.app/catalog/blocks/liquid-glass-widgets): `npx hyperframes add liquid-glass-widgets`; izvorni blok je 1920×1080, 8 s, sa staklenim karticama statistike. Za vertikalni video prilagodi čitljivost i veličinu panela.
- [Liquid Glass Notification](https://hyperframes.mintlify.app/catalog/blocks/liquid-glass-notification): `npx hyperframes add liquid-glass-notification`; izvorni blok je 1920×1080, 8 s, sa plutajućim karticama obaveštenja. Zameni demo sadržaj stvarnom ili anonimizovanom porukom.

Za oba glass bloka dokumentacija navodi da pregled u Chromeu traži `chrome://flags/#canvas-draw-element`, a CLI render tu opciju uključuje automatski. Pri lokalnom radu proveri stvarni prikaz i kompatibilnost sa instaliranom verzijom.
