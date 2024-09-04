# Opdracht voor ChatGPT: Insectenlamp Automatiserings-Blueprint

## Doel
Schrijf een YAML-script voor de blueprint dat voldoet aan bovenstaande eisen en structuur. Het script moet gemakkelijk te importeren zijn in een Home Assistant-omgeving en alle bovenstaande functionaliteiten bevatten, inclusief de logische volgorde van instellingen, uitleg bij parameters, en automatiseringen.

### Notitie
Deze opdracht moet in perfecte YAML-syntax worden geschreven zonder fouten, klaar om direct gebruikt te worden in GitHub en Home Assistant.


## Context
De blueprint moet worden ontworpen om insectenlampen automatisch te bedienen op basis van verschillende omgevingsfactoren zoals temperatuur, luchtvochtigheid, UV-straling, beweging en weersomstandigheden. Dit wordt gedaan om muggen, vliegen en andere insecten effectief te bestrijden.

### Gebruikers
De blueprint is bedoeld voor gebruikers van Home Assistant die specifieke controle willen over insectenlampen, afhankelijk van de actuele weersomstandigheden.

## Vereisten

### 1. Gebruik van Sensorgegevens en Entiteiten
De volgende sensoren moeten optioneel worden toegevoegd, met elk bijbehorende instellingen:
- **weather.buienradar**: Deze sensor levert algemene weergegevens zoals temperatuur, luchtvochtigheid, windsnelheid, etc.
  - **Gekozen parameters**:
    - **Temperatuur**: 20-35°C, aangezien muggen en vliegen het meest actief zijn binnen dit bereik.
    - **Luchtvochtigheid**: >60%, aangezien hogere luchtvochtigheid insecten aantrekt.
  - **Uitleg**: Voeg na elke parameter-instelling een korte uitleg toe, waarin staat waarom deze waarde is gekozen. Bijvoorbeeld:
    - "Muggen en vliegen worden het meest actief bij temperaturen tussen 20 en 35 graden Celsius. Stel de temperatuur hoger of lager in om de gevoeligheid te vergroten of te verkleinen."
  
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

### 3. Acties en Automatiseringen
- **Bewegingssensor**: Bij detectie van beweging worden de lampen tijdelijk ingeschakeld.
  - **Actie**: Verleng de actieve periode van de lampen of schakel over van de vakantiemodus naar de thuis-modus. Voeg uitleg toe over het effect van beweging op de automatisering.

- **Vakantieschakelaar**: Wanneer ingeschakeld, beperkt dit de werking van de lampen om energie te besparen.
  - **Actie**: Lampen blijven uit tenzij de weersomstandigheden extreme insectenactiviteit voorspellen.

- **Seizoensmodus**: Wisselt tussen zomer- en wintermodus op basis van temperatuur en andere weergegevens.
  - **Actie**: In de zomermodus gaan de lampen vaker en langer aan; in de wintermodus blijven ze uit tenzij ongebruikelijk warm weer wordt gedetecteerd.

### 4. Tekstuele Uitleg en Helderheid
- **Gedetailleerde uitleg**: Zorg ervoor dat er bij elke stap duidelijke tekstuele uitleg wordt gegeven, vooral over de aanbevolen waarden en waarom ze belangrijk zijn. Elke parameterinstelling moet een uitleg bevatten die de gebruiker begrijpt.
- **Uitleg waar nodig**: Voor elke handeling of wijziging in de blueprint moet tekstuele toelichting aanwezig zijn om de gebruiker te helpen bij het maken van de juiste keuzes.
