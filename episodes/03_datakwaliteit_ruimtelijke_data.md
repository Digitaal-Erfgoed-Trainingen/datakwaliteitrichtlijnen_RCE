---
title: "Datakwaliteit ruimtelijke data"
teaching: 15 # teaching time in minutes
exercises: 10 # exercise time in minutes
---


:::::::::::::::::::::::::::::::::::::: questions 
- Welke datakwaliteits-richtlijnen van de Rijksdienst voor het Cultureel Erfgoed gelden voor ruimtelijke data?
- Waar moet je op letten als je locaties en geometrieën vastlegt?
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives
- De drie ruimtelijke kwaliteitsdimensies van de RCE kunnen benoemen en uitleggen.
- Kunnen herkennen wanneer locaties, schaalniveaus of geometrieën niet aan de richtlijnen voldoen.
::::::::::::::::::::::::::::::::::::::::::::::::

## Leerdoelen

In de les *Datakwaliteit niet-ruimtelijke data* zijn de kwaliteitsdimensies
voor niet-ruimtelijke data besproken. In deze les gaat het om de drie dimensies die specifiek gelden voor
**ruimtelijke data**: gegevens die een locatie of vorm op de kaart vastleggen,
zoals coördinaten, adressen, punten, lijnen en vlakken (polygonen).

Ook voor ruimtelijke data gelden de dimensies uit die les. Een waarneming
met een locatie heeft bijvoorbeeld ook een unieke identifier nodig (dimensie 1). In de richtlijnen
staat daarbij als voorbeeld dat geo-coördinaten moeten verwijzen naar een reële
locatie in de werkelijkheid. De dimensies hieronder komen daar bovenop.

De veelgemaakte fouten uit de eerdere modules gingen niet over ruimtelijke data.
Een aantal ervan komt bij locaties wel in een vergelijkbare vorm terug. Bij elke
dimensie staat daarom welke fouten vergelijkbaar zijn; de nummers verwijzen naar
de foutentabel in de les *Datakwaliteit niet-ruimtelijke data*.

### 6. Ruimtelijke referentie-eenduidigheid

Elke locatie is eenduidig vastgelegd en verwijst in alle datasets naar dezelfde
plek. Locaties staan in eigen velden, zijn niet vaag of alleen tekstueel
omschreven, en het gebruikte coördinaatreferentiestelsel (CRS) is bekend,
bijvoorbeeld RD (Rijksdriehoeksmeting) of WGS84.

*Voorbeelden:*

- Een CRS-aanduiding bevat altijd een EPSG-code (bijvoorbeeld `EPSG:28992` voor
  RD New of `EPSG:4326` voor WGS84).
- Coördinaten worden consequent in hetzelfde referentiestelsel vastgelegd.
- Een locatie wordt niet afwisselend als adres, plaatsnaam en coördinaat
  vastgelegd.

**Vergelijkbare fouten:**

- *Meer dan één gegeven in een cel (8)*: in een spreadsheet de X- en
  Y-coördinaat samen als tekst in één cel (`155000, 463000`) in plaats van in
  twee aparte kolommen. (In GIS-formaten zoals GeoPackage staat de geometrie overigens wél
  in één kolom, maar daar is dat een speciaal geometrie-datatype dat de software
  kan interpreteren. Dat is dus geen fout).
- *Vrije woorden voor categorieën (12)*: een locatie alleen als vrije tekst
  ('bij de kerk', 'Groningen') in plaats van als coördinaat of vaste code.
- *Datums die niet overal hetzelfde zijn opgemaakt (10)*: coördinaten in
  wisselende notaties of stelsels door elkaar, zoals graden-minuten-seconden,
  decimale graden en RD-coördinaten.
- *Metadata en uitleg in de tabel (5)*: het gebruikte CRS staat nergens
  vastgelegd. Dit hoort in een README of data dictionary.

### 7. Ruimtelijke schaal- en resolutieconsistentie

Het schaalniveau (bijvoorbeeld 1:100 of 1:1000) en de nauwkeurigheid van
ruimtelijke data zijn bekend en passen bij de bron en het beoogde gebruik.
Gegevens suggereren geen grotere nauwkeurigheid dan er werkelijk is (geen
*over-precisie*), en verschillende schaalniveaus worden niet zomaar door elkaar
gebruikt.

*Voorbeelden:*

- Gegevens die op verschillende schaalniveaus zijn ingewonnen, worden niet
  zonder transformatie gecombineerd.
- De ruimtelijke nauwkeurigheid past bij het beoogde gebruik. Een locatie die
  van een historische kaart is overgenomen, krijgt geen coördinaten tot op de
  millimeter.

**Vergelijkbare fout:** *metadata en uitleg in de tabel (5)*. Het schaalniveau
en de nauwkeurigheid staan nergens vastgelegd, of alleen als opmerking in de
tabel. Leg ze vast in een README of data dictionary.

### 8. Ruimtelijke geometrische correctheid

Geometrieën zijn technisch geldig en sluiten logisch op elkaar aan. Het
geometrietype (punt, lijn of vlak) is vastgelegd, lijnen en randen kruisen
zichzelf niet en aangrenzende objecten hebben geen ongewenste overlappingen of
gaten.

*Voorbeelden:*

- Polygonen zijn gesloten.
- Geometrieën bevatten geen self-intersections.
- Punt-, lijn- en vlakobjecten voldoen aan de gekozen geometrische
  representatie.

**Vergelijkbare fouten:** geen. Geometrieën komen in spreadsheets niet voor;
deze dimensie wordt pas relevant als je met GIS-software werkt.

:::::::::::::::::::::::::::::::::::::::::  challenge

## Oefening: ruimtelijke data in je eigen praktijk

Neem een dataset uit je eigen werk waarin locaties voorkomen, of de
oefendataset uit de eerdere modules, en beantwoord de volgende vragen:

1. **Vastlegging**: hoe zijn locaties nu vastgelegd: als adres, plaatsnaam,
   coördinaat of geometrie? Is dat overal op dezelfde manier gedaan?
2. **Referentie**: is bekend in welk coördinaatreferentiestelsel de coördinaten
   staan, en is dat vastgelegd met een EPSG-code?
3. **Nauwkeurigheid**: past de nauwkeurigheid van de locaties bij de bron
   waaruit ze afkomstig zijn? Is er sprake van over-precisie?

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Voor ruimtelijke data gelden drie extra kwaliteitsdimensies: referentie-eenduidigheid (6), schaal- en resolutieconsistentie (7) en geometrische correctheid (8).
- Leg altijd het coördinaatreferentiestelsel vast met een EPSG-code en gebruik dit consequent.
- Leg locaties niet afwisselend als adres, plaatsnaam en coördinaat vast zonder expliciete relatie.
- Combineer geen gegevens van verschillende schaalniveaus zonder transformatie, en suggereer geen grotere nauwkeurigheid dan de bron biedt.

::::::::::::::::::::::::::::::::::::::::::::::::::
