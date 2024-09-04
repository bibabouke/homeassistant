# Opdracht voor ChatGPT: Insectenlamp Automatiserings-Blueprint

## Doel
Schrijf een YAML-script voor de blueprint dat voldoet aan de onderstaande eisen en structuur. Het script moet gemakkelijk te importeren zijn in een Home Assistant-omgeving en alle bovenstaande functionaliteiten bevatten, inclusief de logische volgorde van instellingen, uitleg bij parameters, en automatiseringen.

### Context
De blueprint moet worden ontworpen om insectenlampen automatisch te bedienen op basis van verschillende omgevingsfactoren zoals temperatuur, luchtvochtigheid, UV-straling, beweging en weersomstandigheden. Dit wordt gedaan om muggen, vliegen en andere insecten effectief te bestrijden.

### Gebruikers
De blueprint is bedoeld voor gebruikers van Home Assistant die specifieke controle willen over insectenlampen, afhankelijk van de actuele weersomstandigheden.

## Vereisten

### 1. Gebruik van Sensorgegevens en Entiteiten
De volgende sensoren moeten optioneel worden toegevoegd, met elk bijbehorende instellingen:
- **weather.buienradar**: Deze sensor levert algemene weergegevens zoals temperatuur, luchtvochtigheid, windsnelheid, etc.
  - **Gekozen parameters**:
    - **Temperatuur**: 20-35°C
      - **Uitleg**: Muggen en vliegen worden het meest actief bij temperaturen tussen 20 en 35 graden Celsius. Stel de temperatuur hoger of lager in om de gevoeligheid te vergroten of te verkleinen.
    - **Luchtvochtigheid**: >60%
      - **Uitleg**: Hogere luchtvochtigheid trekt insecten aan.
  
- **sensor.straling**: Meet de UV-straling (W/m²).
  - **Uitleg**: Hogere UV-straling kan insecten actiever maken.

- **sensor.grondtemperatuur**: Meet de temperatuur van de grond.
  - **Uitleg**: Bepaalde insecten worden actiever bij hogere grondtemperaturen.

- **sensor.neerslagintensiteit**: Meet de regenval in mm/h.
  - **Uitleg**: Bij hevige regenval worden insecten vaak minder actief.

- **sensor.neerslagverwachting_totaal**: Verwachte regenval in mm.
  - **Uitleg**: Regen kan de activiteit van insecten verminderen.

### 2. Configuratie en Parameters
- **Per entiteit**: Elke sensor heeft bijbehorende instellingen die gebruikers kunnen aanpassen. De parameters moeten direct onder de entiteit staan. 
  - Bijvoorbeeld:
    1. **Entiteit: weather.buienradar**
    2. **Temperatuurinstelling**: 20-35°C (inclusief uitleg waarom deze waarden zijn gekozen).
    3. **Luchtvochtigheidsinstelling**: >60% (inclusief uitleg).
  
- **Logische volgorde**: Voorzie de blueprint van een logische structuur waarin eerst de entiteit wordt ingevoerd en daarna direct de bijbehorende parameters worden ingesteld. Vermijd het groeperen van alle entiteiten bovenaan en alle parameters onderaan; houd de instellingen per entiteit bij elkaar.

### 3. Helpers en Automatiseringen
Gebruik de volgende helpers in de Home Assistant-configuratie:
- **input_boolean.vakantie** (`Vakantieschakelaar`):
  - **Type:** `input_boolean`
  - **Beschrijving:** Schakelt de vakantiemodus in of uit. Wanneer ingeschakeld, blijven de insectenlampen uit, tenzij beweging of een thuisregistratie wordt gedetecteerd en de weersomstandigheden insectenactiviteit voorspellen.

- **input_select.seizoensmodus** (`Seizoensmodus`):
  - **Type:** `input_select`
  - **Opties:** `Zomerstand`, `Winterstand`
  - **Beschrijving:** Wisselt automatisch tussen zomer- en wintermodus op basis van temperatuur en luchtvochtigheid.

- **timer.noodbediening_insectenlamp_timer** (`Noodbediening Insectenlamp Timer`):
  - **Type:** `timer`
  - **Duur:** 1 uur
  - **Beschrijving:** Schakelt de insectenlamp tijdelijk uit op verzoek van de noodbediening.

- **input_boolean.noodbediening_insectenlamp** (`Noodbediening Insectenlamp`):
  - **Type:** `input_boolean`
  - **Beschrijving:** Handmatige schakelaar om de insectenlamp in of uit te schakelen. Activeert de timer `timer.noodbediening_insectenlamp_timer` wanneer ingeschakeld.

### 4. Acties en Automatiseringen
- **Automatische Seizoenswisseling:**
  - **Actie:** `input_select.seizoensmodus` schakelt automatisch tussen `Zomerstand` en `Winterstand` op basis van sensorwaarden zoals temperatuur en luchtvochtigheid.
  
- **Vakantiemodus Controle:**
  - **Actie:** Wanneer `input_boolean.vakantie` is ingeschakeld, blijven de lampen uit, tenzij er beweging of een thuisregistratie is én de weersomstandigheden insectenactiviteit voorspellen.

- **Bewegingssensor als Sub-check:**
  - **Actie:** Controleert of er iemand thuis is. Bij langdurige afwezigheid schakelt het systeem automatisch over naar `input_boolean.vakantie`.

- **Noodbediening Insectenlamp:**
  - **Actie:** Wanneer `input_boolean.noodbediening_insectenlamp` wordt ingeschakeld, wordt de timer `timer.noodbediening_insectenlamp_timer` gestart, die de lampen 1 uur lang uitschakelt, ongeacht andere condities.

### 5. Tekstuele Uitleg en Helderheid
- **Gedetailleerde uitleg:** Zorg ervoor dat er bij elke stap duidelijke tekstuele uitleg wordt gegeven, vooral over de aanbevolen waarden en waarom ze belangrijk zijn. Elke parameterinstelling moet een uitleg bevatten die de gebruiker begrijpt.
- **Uitleg waar nodig:** Voor elke handeling of wijziging in de blueprint moet tekstuele toelichting aanwezig zijn om de gebruiker te helpen bij het maken van de juiste keuzes.

