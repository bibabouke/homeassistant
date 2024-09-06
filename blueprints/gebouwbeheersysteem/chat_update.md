Doel van het systeem
Het systeem moet de ventilatie en afzuiging in verschillende kamers van een huis beheren op basis van temperatuur, luchtvochtigheid, weersomstandigheden (zoals regen), en vakantiesensor. Elke ruimte kan zijn eigen configuraties hebben voor ventilatoren, sensoren en regenschakelaars. Het systeem moet modulair, gebruiksvriendelijk en volledig configureerbaar zijn via de Home Assistant UI.

We beginnen met 1 ruimte, de Master Bedroom. Later kunnen we andere kamers toevoegen.

Specifieke wensen en eisen
De Master Bedroom heeft een ventilator (switch) en een temperatuursensor incl luchtvochtigheidssensor.
De ventilator moet via een switch worden in- en uitgeschakeld.
De ventilator moeten automatisch aan of uit gaan op basis van binnen- en buitentemperatuur, om een optimale binnentemperatuur te bereiken zonder onnodig energie te verbruiken. 
De gebruiker kan ook handmatig de switch bedienen en de ventilator aanzetten. We moeten dus voor een schakeling altijd checken wat de huidige status is.

2. Regensensor per ruimte
De kamer moet een regenschakelaar krijgen om de ventilatoren te laten uitschakelen als er regen wordt gedetecteerd (bijvoorbeeld via de opgegeven weather entity / Buienradar).

Regendrempel: De gebruiker kan een drempelwaarde instellen voor regen (in mm), met advies over waarden voor motregen, miezeren en harde regen. Een aanbevolen drempelwaarde net onder motregen moet worden voorgesteld.

6. Modulaire opzet en uitklapbare secties
Het script moet modulair opgebouwd zijn, zodat het eenvoudig kan worden uitgebreid.

Uitklapbare secties: Voor elke functie (ventilatoren, weersensoren, afzuiging, etc.) moet er een aparte, uitklapbare sectie in de blueprint zijn, zodat het overzichtelijk blijft voor de gebruiker. 
Nederlandse benamingen en uitleg: Alle functies en beschrijvingen in het script moeten in het Nederlands zijn om het begrijpelijk te houden voor de gebruiker. Uitleg voor de gebruiker moet in de interface worden opgenomen, met adviezen over bijvoorbeeld regendrempelwaarden.

7. Sensoren en gegevensbronnen
De gebruiker moet de mogelijkheid hebben om zelf een weersensor te kiezen (bijvoorbeeld Buienradar of forecast_thuis). Deze sensor moet relevante waarden zoals temperatuur, luchtvochtigheid, en neerslag doorgeven en het script haalt de attributen eruit op en zet ze in variabelen. 

De blueprint moet flexibel genoeg zijn om deze gegevens te gebruiken zonder hardcoded sensors.

In plaats van direct waarden van entiteiten te gebruiken, verwerken we ze eerst via templates om eventuele 'unknown' of 'unavailable' waarden op te vangen en standaardwaarden in te stellen. Dit voorkomt fouten in de automatisering wanneer sensoren tijdelijk geen waarde hebben. Door het gebruik van variabelen en templates kunnen we de betrouwbaarheid en flexibiliteit van het script vergroten.

variables:
  buiten_temp: "{{ states('sensor.buitentemperatuur') | float(0) }}"

condition:
  - condition: template
    value_template: "{{ buiten_temp > 15 }}"




8. Foutafhandeling en optimalisatie
9. 
Valideer alle templates en condities om te voorkomen dat fouten optreden zoals "unexpected char" en "undefined variable". Het script moet foutloos importeerbaar en uitvoerbaar zijn in Home Assistant.
Check status van switches: Voordat een ventilator of afzuiging wordt in- of uitgeschakeld, moet de huidige status worden gecontroleerd om onnodige schakelingen te voorkomen.
Overige opmerkingen
Versiebeheer: Het is belangrijk om versiebeheer toe te passen voor elke update van de blueprint. Elke nieuwe versie moet een duidelijk versienummer krijgen (bijvoorbeeld versie 13, versie 14, etc.).
Toekomstige uitbreidingen: Er moet ruimte zijn om het systeem in de toekomst uit te breiden met extra systemen zoals rolluiken of airconditioning.

Ik heb liever niet dat we rechtstreeks gebruik maken van de weerentiteit.
Ik heb liever dat jij om de xx tijd de data ophaalt en opslaat in een variabele van onszelf. 
Bij storingen van buienradar heb jij als nog de laatste temperatuur, humidity en neerslag.

De attributen van buienradar zien er als volgt uit>
temperature: 23.4
temperature_unit: °C
humidity: 62
pressure: 1010.6
pressure_unit: hPa
wind_bearing: 82
wind_speed: 16.92
wind_speed_unit: km/h
visibility: 46.8
visibility_unit: km
precipitation_unit: mm
attribution: Data provided by buienradar.nl
friendly_name: Buienradar
supported_features: 1


De gebruiker kiest de desgewenste weather entiteit, maar dan heb je een idee van de attributen ervan. 


