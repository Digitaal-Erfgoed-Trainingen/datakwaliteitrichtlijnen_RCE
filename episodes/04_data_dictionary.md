---
title: "Data dictionary"
teaching: 15 # teaching time in minutes
exercises: 15 # exercise time in minutes
---


:::::::::::::::::::::::::::::::::::::: questions 
- Wat is een data dictionary en waarom is het nuttig?
- Welke eigenschappen van een kolom leg je vast in een data dictionary volgens de RCE?
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- Kunnen uitleggen wat een data dictionary is en wat het oplevert.
- De belangrijkste eigenschappen kennen die de RCE per kolom vastlegt.
- Zelf een eenvoudige data dictionary kunnen opstellen voor een tabel.
::::::::::::::::::::::::::::::::::::::::::::::::

## Leerdoelen

In de les *Datakwaliteit niet-ruimtelijke data* kwam de data dictionary al een
paar keer voorbij: bij dimensie 5 (semantische eenduidigheid) en bij de fout
*metadata en uitleg in de tabel*. In deze les bekijken we wat een data
dictionary precies is en hoe de RCE die opbouwt.

## Wat is een data dictionary?

Een **data dictionary** is een beschrijving van een tabel, kolom voor kolom. Per
kolom staat erin wat de kolom betekent en aan welke regels de waarden moeten
voldoen. De data dictionary staat *naast* de dataset, in een apart bestand, en
dus niet in de tabel zelf.

De RCE stelt per tabel een data dictionary op. Bij geografische bestanden zoals
een GeoPackage of shapefile geldt dat per laag.

Een data dictionary is nuttig omdat:

- **misverstanden worden voorkomen**: iedereen begrijpt de kolommen op dezelfde
  manier;
- **de datakwaliteit verbetert**: fouten en inconsistenties worden eerder
  opgemerkt;
- **anderen sneller aan de slag kunnen**: wie de dataset later gebruikt, hoeft
  niet te raden wat er in een kolom staat.

## Wat leg je per kolom vast?

De RCE heeft een vaste lijst met eigenschappen die per kolom kunnen worden
vastgelegd. Niet elke eigenschap is op elke kolom van toepassing. Sommige
eigenschappen kunnen automatisch uit het bestand worden afgeleid (zoals de
kolomnaam en het datatype); andere moeten door de beheerder van de data worden
ingevuld. De belangrijkste eigenschappen zijn hieronder per onderwerp
samengevat.

| Onderwerp | Eigenschap                                                                              | Wat leg je vast? |
|---|-----------------------------------------------------------------------------------------|---|
| **Basis** | `kolom_naam`                                                                            | De naam van de kolom. |
| | `data_type`                                                                             | Het soort waarde: tekst, geheel getal, decimaal getal, datum, ja/nee, geometrie, enzovoort. |
| | `beschrijving`                                                                          | Wat betekent de kolom precies, in gewone taal? |
| **Regels voor waarden** | `verplicht`                                                                             | Mag een cel leeg zijn? |
| | `uniek`                                                                                 | Moet elke waarde uniek zijn, zoals bij een id-kolom? |
| | `notatie`                                                                               | Het vaste formaat, bijvoorbeeld `JJJJ-MM-DD` of postcode. |
| | `minimale_waarde`, `maximale_waarde`                                                    | De kleinste en grootste toegestane waarde van een getal of datum. |
| | `herhaalbaar`, `scheidingsteken`                                                        | Mag een cel meerdere waarden bevatten, en zo ja, met welk scheidingsteken? |
| **Begrippen** | `woordsysteem`                                                                          | Uit welke thesaurus of referentielijst komen de waarden? |
| | `waarden_lijst`                                                                         | Als er geen thesaurus is: de toegestane waarden zelf, of een verwijzing naar een bestand. |
| **Identificatie en relaties** | `primaire_sleutel` (primary key)                                                        | Is dit de identificatiekolom van de tabel? |
| | `vreemde_sleutel` (foreign key) + `gerelateerde_tabel_naam` + `gerelateerde_kolom_naam` | Naar welke tabel en kolom verwijst deze kolom? |
| | `pid_systeem`                                                                           | Het systeem van een persistente identifier, zoals Rijksmonumentennummer, DOI of ORCID. |
| **Ruimtelijk** | `coordinatenstelsel`                                                                    | Het CRS als EPSG-code, bijvoorbeeld `EPSG:28992` (RD). |
| | `geometrie_type`                                                                        | Punt, lijn, vlak (polygoon) of een multi-variant daarvan. |
| **Gebruik** | `licentie`                                                                              | Onder welke licentie de data beschikbaar is, bijvoorbeeld CC0 of CC BY 4.0. |
| | `beperking_beschikbaarstelling`                                                         | Of de data publiek mag, alleen intern, of alleen geanonimiseerd. |

Bij `woordsysteem` verwijst de RCE onder andere naar de
[Cultuurhistorische Thesaurus (CHT)](https://linkeddata.cultureelerfgoed.nl/thesauri/cht),
het Archeologisch Basisregister (ABR), de Art & Architecture Thesaurus (AAT)
van Getty en, voor plaatsen en adressen, de Basisregistratie Adressen en
Gebouwen (BAG).

::::::::::::::::::::::::::::::::::::::::: callout

## Formaat

De RCE legt een data dictionary vast als CSV-bestand met een **puntkomma** als
scheidingsteken. Zo'n bestand is goed te openen en te bewerken in Excel, en
tegelijk eenvoudig te lezen door een script. Elke rij in de data dictionary
beschrijft één kolom van de dataset.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Voorbeeld

Hieronder staat een deel van een data dictionary voor de glasdataset uit de
eerdere modules. Alleen de ingevulde eigenschappen zijn opgenomen.

| kolom_naam | data_type | beschrijving | verplicht | uniek | woordsysteem / waarden_lijst | pid_systeem |
|---|---|---|---|---|---|---|
| Monumentnr | INTEGER | Rijksmonumentennummer van het pand waarin het glas zich bevindt | nee | nee | | Rijksmonumentennummer |
| Plaats | VARCHAR | Woonplaats waarin het pand staat | ja | nee | BAG - woonplaats | |
| Soort glas | VARCHAR | Het soort glas | ja | nee | tabblad `Referentielijst` | |
| Circa ja/nee | VARCHAR | Geeft aan of de datering een schatting is | ja | nee | ja, nee | |

Een paar dingen vallen op:

- `Monumentnr` is **niet uniek**: in één monument kan meer dan één glasobject
  zitten. Als identificatie van een rij is deze kolom dus niet geschikt
  (zie dimensie 1).
- Bij `Soort glas` zorgt de verwijzing naar de referentielijst ervoor dat
  iedereen dezelfde termen gebruikt (zie dimensie 5).
- Bij `Circa ja/nee` staan de toegestane waarden direct in de data dictionary,
  omdat het om een korte lijst gaat.

:::::::::::::::::::::::::::::::::::::::::  challenge

## Oefening: stel een data dictionary op

Kies drie à vier kolommen uit een dataset uit je eigen werk, of uit de
glasdataset uit de eerdere modules, en stel daarvoor een data dictionary op.

1. Vul voor elke kolom ten minste `kolom_naam`, `data_type`, `beschrijving`,
   `verplicht` en `uniek` in.
2. Bepaal of er een thesaurus of referentielijst bestaat voor de waarden in de
   kolom. Zo ja, vul `woordsysteem` of `waarden_lijst` in.
3. Bespreek met elkaar: welke eigenschappen waren lastig in te vullen, en wat
   zegt dat over de kwaliteit van de dataset?

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Een data dictionary beschrijft een tabel kolom voor kolom: wat de kolom betekent en aan welke regels de waarden voldoen.
- De data dictionary staat naast de dataset, niet in de tabel zelf.
- De RCE legt per kolom onder andere het datatype, de beschrijving, de regels voor waarden en het gebruikte woordsysteem vast.
- Een data dictionary maakt een dataset begrijpelijker, beter controleerbaar en eenvoudiger te hergebruiken.

::::::::::::::::::::::::::::::::::::::::::::::::::
