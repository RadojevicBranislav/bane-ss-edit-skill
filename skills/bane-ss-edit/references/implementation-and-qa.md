# Implementacija i QA

## 1. Priprema izvora

Pročitaj repozitorijumski `AGENTS.md` i lokalne `/hyperframes` i Remotion skillove koji odgovaraju poslu. Utvrdi rezoluciju, codec, fps, trajanje i audio izvora. Ako browser ne seekuje HEVC/10-bit snimak pouzdano, napravi H.264/yuv420p preglednu kopiju sa stalnim fps i očuvanim audiom; original sačuvaj. `ffprobe` treba da potvrdi isti broj frejmova i fps za original i preglednu kopiju. Trajanje kompozicije veži za stvaran broj dostupnih frejmova, da poslednji frejm ne traži sliku izvan fajla.

Napravi transkript sa vremenima **po reči**. Preslušaj i ručno popravi očigledne greške, naročito naziv proizvoda, komandu, URL i vlastita imena. Nemoj izmišljati izgovoreni tekst. Reč prikazuj samo tokom njenog govornog intervala.

Kada korisnik prijavi dupliranje, prvo utvrdi da li se ponavlja govor, video kadar ili samo tekst u grafici/titlu. Izoluj kratak audio isečak oko navedenih reči; automatski transkript celog snimka može da preskoči tihi pogrešan početak, pa odsustvo duplikata u transkriptu nije dokaz da ga nema. Uporedi lokalnu transkripciju tog isečka sa zvukom i pronađi granice po pauzama. Ako je višak izgovoren, odstrani isti vremenski interval iz videa i zvuka, po mogućnosti na granicama frejmova; zatim pomeri sva kasnija vremena scena, titlova, animacije, SFX i završnog kadra. Proveri trajanje, broj frejmova i kratak audio isečak posle reza. Ako se duplira samo tekst, ispravi odgovarajući sloj bez sečenja govora.

## 2. Asseti i zajednički manifest

Otvori dostavljene URL-ove u browseru i snimi relevantna stanja ekrana. Za korisnički nalog koristi korisnikov screenshot ili recording. Kadriraj izvor tako da tekst ostane čitljiv i u planiranom split ili punom kadru, uz 5–10% nevidljive bezbedne margine. Zum na klik usmeri na tačan UI element, pa se vrati u čitljiv raspored. Pre generičke grafike proveri da li stvarni logotip kanala, anonimizovana poruka ili primer podsetnika mogu jasnije da pokažu izgovorenu situaciju.

Sačuvaj zajednički manifest sekcija (`start`, `end`, asset, tip, izgovoreni cue) i manifest radnji (`time`, pozicija u kompoziciji, radnja, SFX). Drži koordinate u jednom referentnom sistemu 1080 × 1920 i deli ih između HyperFramesa i Remotiona. Obeleži šta je realan snimak, a šta rekonstrukcija.

## 3. HyperFrames animacija

HyperFrames neka upravlja ekranima, grafičkim sekcijama, klikovima, otvaranjima, marker potezima i po potrebi prompt barom. Motion treba da prati govor: prvi smislen element ulazi ubrzo po početku sekcije, zatim fokus na element, kratak click/press i otvaranje, pa miran kadar za čitanje. Kursor je vidljiv samo kada pomaže; tokom kucanja se sklanja s reči, vraća na dugme za slanje i prati ga suptilan SFX. Ključni položaji i prelazi moraju biti seek-safe.

Za svaku izmenjenu `.html` kompoziciju pokreni `npx hyperframes lint` i `npx hyperframes check` pre previewa. Ispravi greške; upozorenja proceni prema stvarnom rasporedu. Uporedi više timestampova s odobrenim storyboardom.

## 4. Remotion kompozicija

Remotion sklapa govor, promene rasporeda kadra, vizuale, titlove i zvuk. Talking-head video i audio ostaju sinhronizovani kroz pun kadar govornika, split i pun kadar vizuala, uključujući rezove koje je korisnik zatražio. Donji split kadar obuhvata približno polovinu videa; nad njim je grafika na korisnikovoj aktuelnoj paleti. Caption komponenta dobija `useCurrentFrame()` i pronalazi aktivnu reč po vremenu. Pozicije hooka i svake vrste titla odredi prema stvarnom položaju glave, lica i ključnog grafičkog sadržaja na više kadrova; ne uzimaj jednu stalnu koordinatu zdravo za gotovo. Ne ubacuj titlove u sam screenshot.

Ako se pri prelazu pun kadar → split javlja zastajkivanje, proveri da li kompozicija na granici uslovno uklanja i ponovo montira video ili grafički izvor. Medijske elemente koji treba da teku kroz obe vrste kadra drži montirane na istom vremenskom toku; menjaj masku, položaj ili vidljivost omotača za raspored. Proveri da skriveni sloj zaista ostaje dekodiran u ciljnom okruženju. Uporedi neposredno susedne frejmove pre i posle svakog tipa prelaza i pregledaj Studio reprodukciju; početni beli kadar odmah posle učitavanja ili seeka proveri ponovo kada se medij učita, pa odvoji kašnjenje pregleda od greške u renderu.

Za MP4 izvore koristi `Video` iz `@remotion/media`, na istoj verziji kao `remotion`. On pri izvozu traži tačan frejm. Stari `Video` iz `remotion` u ovom slučaju je povremeno vraćao frejm nekoliko mesta unazad, a `OffthreadVideo` je ovde padao sa `No frame found at position`. Ako koristiš `@remotion/media`, izbegni tihi fallback na `OffthreadVideo` kada je taj put već pokazao grešku. Za drugačiji format izvora proveri podršku pre izbora dekodera. Pri prelasku sa HTML video elementa na canvas, `object-fit` u CSS-u ne mora raditi: koristi odgovarajući prop ili spoljašnji wrapper sa `overflow: hidden` i eksplicitnim pozicioniranjem da očuvaš izabrani crop lica.

Kursor ne sme pokriti komandu ni važan tekst. Završni korisnikov screenshot izuzmi iz grayscale filtera. Sačuvaj originalni audio govornika; zvukovi klikova neka budu tihi i kratki.

## 5. Provera izvoza

Kada je korisnik tražio MP4, izvezi u **novi imenovani fajl**; ne prepisuj neuspeo fajl dok novi ne prođe proveru. Ako render pada, pročitaj tačnu grešku, popravi uzrok i ponovi samo potreban korak. Manja konkurentnost rendera može pomoći pri ograničenoj memoriji, ali nije zamena za ispravan dekoder.

Proveri:

1. `ffprobe`: rezolucija, fps, broj video frejmova, trajanje i AAC/audio tok.
2. Stvarne kadrove iz punog kadra govornika, split kadra, punog vizuala, sredine UI animacije i završetka; prompt bar proveri ako postoji.
3. Redosled govornikovih frejmova u odnosu na izvor. Sama činjenica da MP4 ima 30 fps nije dovoljna; kratki povratak na raniji izvorni frejm izgleda kao seckanje. Poredi crop lica na uzastopnim frejmovima u punom kadru i splitu; za split uporedi isti deo izvora nakon skaliranja i kropovanja, jer različita geometrija može lažno pokazati odstupanje od jednog frejma. Posebno traži ponovljene ili zadržane pokretne kadrove.
4. Audio protiv izvora na početku, u više srednjih sekcija i na kraju; proveri kontinuitet govora, vremenski pomak i delove sa klikovima. AAC trajanje sme neznatno da se razlikuje, ali govor ne sme da preskoči ili zastane.
5. Završni profil u originalnoj boji i čitljivost svakog jednog titla bez sudara sa licem ili UI tekstom.

Za kvalitetan izvoz možeš koristiti H.264/yuv420p, PNG međukadrove i ograničenu konkurentnost ako memorija to traži; nijedno podešavanje ne zamenjuje proveru redosleda frejmova. Ako browser ne može da se pokrene zbog sandboxa, prijavi konkretnu grešku i upotrebi dozvoljeni način izvršavanja potreban za autorizovani izvoz. Tek nakon provera označi novi fajl kao finalni i pokaži ga korisniku. Stare neuspele izvoze jasno označi kao nevažeće.
