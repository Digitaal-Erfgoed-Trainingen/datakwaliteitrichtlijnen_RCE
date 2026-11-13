---
title: "Datakwaliteit niet-ruimtelijke data"
teaching: 20 # teaching time in minutes
exercises: 10 # exercise time in minutes
---


:::::::::::::::::::::::::::::::::::::: questions 
- Welke datakwaliteits-richtlijnen van de Rijksdienst voor het Cultureel Erfgoed gelden voor niet-ruimtelijke data?
- Hoe hangen deze richtlijnen samen met de *best practices* uit de eerdere modules?
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- De zes kwaliteitsdimensies voor niet-ruimtelijke data kunnen benoemen en uitleggen.
- Veelvoorkomende spreadsheetfouten kunnen koppelen aan de bijbehorende kwaliteitsdimensie.
::::::::::::::::::::::::::::::::::::::::::::::::

## Leerdoelen

In deze les bespreken we de datakwaliteitsrichtlijnen van de RCE die gelden voor
niet-ruimtelijke data: gegevens over objecten, begrippen en dateringen, zoals je
die in een spreadsheet vastlegt. De richtlijnen voor ruimtelijke data komen aan bod in
de les *Datakwaliteit ruimtelijke data*.

## De kwaliteitsdimensies van de RCE

De RCE heeft haar datakwaliteitsrichtlijnen vastgelegd in het document
*Richtlijnen voor datasets binnen DNA Nl – Kwaliteit als basis* (versie 1.0).
Daarin wordt datakwaliteit teruggebracht tot negen **kwaliteitsdimensies**. Het
doel hiervan is niet om *perfecte* datasets te maken, maar wel dat er voldoende eenduidigheid en structuur 
is om data te kunnen combineren en hergebruiken.

| # | Kwaliteitsdimensie | Soort data | Les |
|---|---|---|---|
| 1 | Unieke identificatie en referentiële integriteit | niet-ruimtelijk | deze les |
| 2 | Structurele consistentie | niet-ruimtelijk | deze les |
| 3 | Waardenvaliditeit | niet-ruimtelijk | deze les |
| 4 | Granulariteit en eenduidige representatie | niet-ruimtelijk | deze les |
| 5 | Semantische eenduidigheid en interoperabiliteit | niet-ruimtelijk | deze les |
| 6 | Ruimtelijke referentie-eenduidigheid | ruimtelijk | les 3 |
| 7 | Ruimtelijke schaal- en resolutieconsistentie | ruimtelijk | les 3 |
| 8 | Ruimtelijke geometrische correctheid | ruimtelijk | les 3 |
| 9 | Temporele resolutie | niet-ruimtelijk | deze les |

Hieronder worden de zes dimensies voor niet-ruimtelijke data een voor een
besproken. Bij elke dimensie staat welke veelgemaakte fouten uit de eerdere
modules ermee samenhangen; de nummers verwijzen naar de tabel onderaan deze les.

### 1. Unieke identificatie en referentiële integriteit

Elk record heeft een unieke en stabiele identifier die nooit ontbreekt en niet
wordt hergebruikt. Dezelfde entiteit heeft overal dezelfde identifier, en
verwijzingen naar andere records of datasets wijzen naar identifiers die ook
echt bestaan.

*Voorbeeld:* elk record heeft een unieke en persistente id.

**Gerelateerde veelvoorkomende fout:** geen unieke code per rij (6).

### 2. Structurele consistentie

De opbouw van de dataset is vast en voorspelbaar: elk veld heeft één datatype,
er staat één waarde en één concept per veld, en formaten worden niet door
elkaar gebruikt.

*Voorbeeld:* de schrijfwijze van dateringen is consistent, bijvoorbeeld bij het
onderscheid tussen voor en na Christus.

**Gerelateerde veelvoorkomende fouten:** meerdere tabellen op één werkblad (1), meerdere
tabbladen voor dezelfde data (2), opmaak gebruiken om informatie vast te leggen
(3), opmaak om de tabel mooi te maken (4), meer dan één gegeven in een cel (8)
en onbekende en ontbrekende waarden (9).

### 3. Waardenvaliditeit

De inhoud van de cellen is juist en realistisch: waarden vallen binnen het
toegestane bereik, worden op dezelfde manier weergegeven en spreken andere
bronnen niet tegen.

*Voorbeeld:* een stijlperiode als 'Romantiek' betekent niet voor iedere
onderzoeker dezelfde tijdsperiode. Leg daarom bij voorkeur ook jaartallen of een
gedefinieerde periode vast.

**Gerelateerde veelvoorkomende fouten:** geen van de fouten in de tabel valt direct onder deze
dimensie. Ongeldige waarden spoor je op met de kwaliteitscontroles uit de
eerdere modules.

### 4. Granulariteit en eenduidige representatie

Elk gegeven wordt op één detailniveau en op één manier vastgelegd: één entiteit
per veld, geen samengestelde waarden en geen vermenging van detailniveaus (zoals
gebouw en bouwonderdeel in dezelfde kolom).

*Voorbeelden:*

- Aanduidingen als 'ca.' of 'omstreeks' bij een datering staan in een apart veld.
- Geografische begrippen moeten eenduidig zijn: bedoel je met 'Groningen' de
  provincie of de gemeente?

**Gerelateerde veelvoorkomende fout:** opmerkingen in een cel (7).

### 5. Semantische eenduidigheid en interoperabiliteit

Begrippen hebben één vaste betekenis, zodat mens én computer de data op dezelfde
manier begrijpen en datasets aan elkaar te koppelen zijn. Elke kolom is
beschreven in een *data dictionary*, en waar vaste termen verplicht zijn, komen
die uit een referentielijst of thesaurus in plaats van uit vrije tekst.

*Voorbeeld:* de term 'neoclassicisme' moet naar hetzelfde begrip verwijzen als
'Neo-Classicisme'.

**Gerelateerde veelvoorkomende fouten:** metadata en uitleg in de tabel (5) en vrije woorden
voor categorieën (12).

### 9. Temporele resolutie

Tijd en datering worden eenduidig en op een passend detailniveau (jaar, maand,
dag) vastgelegd. Datums hebben een uniforme notatie en begin- en einddatum
vormen samen een logisch tijdsinterval.

*Voorbeelden:*

- Datums worden consequent volgens ISO 8601 (`jjjj-mm-dd`) geschreven.
- Onzekere dateringen worden expliciet onderscheiden van exacte dateringen.

**Gerelateerde veelvoorkomende fouten:** datums die niet overal hetzelfde zijn opgemaakt (10) en
meerdere dateringsgegevens in één kolom (11).

:::::::::::::::::::::::::::::::::::::::::  challenge

## Oefening: de RCE-richtlijnen in je eigen praktijk

Lees de Datakwaliteitsrichtlijnen van de Rijksdienst voor het Cultureel Erfgoed
door en beantwoord de volgende vragen vanuit je eigen werkpraktijk:

1. **Relevantie**: welke richtlijnen zijn voor jouw werk het meest van belang?
   Licht kort toe waarom.
2. **Proportionaliteit**: zijn er richtlijnen die voor jouw werk verder gaan dan
   nodig is? Weeg af wat het toepassen ervan kost tegenover wat het oplevert.
3. **Duidelijkheid**: zijn alle richtlijnen helder geformuleerd? Noteer welke
   richtlijnen vragen oproepen of op meerdere manieren te interpreteren zijn.

::::::::::::::::::::::::::::::::::::::::::::::::::

### Overzicht van veelvoorkomende fouten en daaraan gerelateerde RCE Datakwaliteitsrichtlijn
De tabel hieronder vat de fouten samen die in de eerdere modules zijn besproken.
Per fout staat erin:

- **Fout**: de naam van de veelvoorkomende fout uit module 1 [link naar module 1].
- **Oplossing in het kort**: wat je in plaats daarvan kunt doen.
- **RCE Datakwaliteitsrichtlijn**: het nummer van de kwaliteitsdimensie
  (zie hierboven) waar de fout het meest bij past.

| # | Fout | Oplossing in het kort | RCE Datakwaliteitsrichtlijn |
|---|------|------|---|
| | **Opbouw en opmaak van de dataset** | | |
| 1 | Meerdere tabellen op één werkblad | Eén tabel per werkblad; data van hetzelfde soort onder elkaar. | 2 |
| 2 | Meerdere tabbladen voor dezelfde data | Zet alles in één tabel en voeg een kolom toe. Filter wanneer nodig op die kolom. | 2 |
| 3 | Opmaak gebruiken om informatie vast te leggen | Leg informatie vast in een kolom, niet in een kleur. | 2 |
| 4 | Opmaak om de tabel mooi te maken | Geen samengevoegde cellen, titels of lege rijen in de tabel. | 2 |
| 5 | Metadata en uitleg in de tabel | Zet uitleg in een README of data dictionary. | 5 |
| 6 | Geen unieke code per rij | Elke rij een eigen, unieke code die nooit leeg is. | 1 |
| | **Waardes in de cel** | | |
| 7 | Opmerkingen in een cel | Twijfel in een eigen kolom; toelichting in een opmerkingenkolom. | 4 |
| 8 | Meer dan één gegeven in een cel | Eén gegeven per cel: eenheid in de kolomnaam, lijstjes op aparte rijen. | 2 |
| 9 | Onbekende en ontbrekende waarden | Kies één manier, bij voorkeur een lege cel. | 2 |
| 10 | Datums die niet overal hetzelfde zijn opgemaakt | Eén notatie, bij voorkeur `jjjj-mm-dd`. | 9 |
| 11 | Meerdere dateringsgegevens in één kolom | Begin- en eindjaar in aparte kolommen. | 9 |
| 12 | Vrije woorden voor categorieën | Gebruik een referentielijst of thesaurus. | 5 |

:::::::::::::::::::::::::::::::::::::::: keypoints

- De RCE onderscheidt negen kwaliteitsdimensies; zes daarvan gelden voor niet-ruimtelijke data (1 t/m 5 en 9).
- De veelvoorkomende spreadsheetfouten uit de eerdere modules zijn direct te koppelen aan deze dimensies.
- Het doel is niet perfecte data, maar data die te combineren, publiceren en hergebruiken is.

::::::::::::::::::::::::::::::::::::::::::::::::::
