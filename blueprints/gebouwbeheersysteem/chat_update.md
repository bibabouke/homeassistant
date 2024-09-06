Doel van het systeem
Het systeem moet de ventilatie en afzuiging in verschillende kamers van een huis beheren op basis van temperatuur, luchtvochtigheid, weersomstandigheden (zoals regen), en vakantiesensoren. Elke ruimte kan zijn eigen configuraties hebben voor ventilatoren, sensoren en regenschakelaars. Het systeem moet modulair, gebruiksvriendelijk en volledig configureerbaar zijn via de Home Assistant UI.

Specifieke wensen en eisen
1. Ventilatoren en Ruimtes
Aantal ventilatoren: Er zijn 4 vaste ruimtes in het huis waarvoor ventilatoren moeten worden geconfigureerd:
Woonkamer: Ventilator en temperatuursensor.
Master Bedroom: Ventilator, temperatuursensor, optionele luchtvochtigheidssensor.
Kantoorruimte: Ventilator, temperatuursensor, optionele luchtvochtigheidssensor.
Zolder: Ventilator, temperatuursensor, optionele luchtvochtigheidssensor.
Elke ventilator in de ruimtes moet via een switch worden in- en uitgeschakeld.
De ventilatoren moeten automatisch aan of uit gaan op basis van binnen- en buitentemperatuur, om een optimale binnentemperatuur te bereiken zonder onnodig energie te verbruiken. Dit moet ook werken in combinatie met andere systemen zoals airconditioning.
2. Regensensor per ruimte
Elke kamer moet een optionele regenschakelaar krijgen om de ventilatoren uit te schakelen als regen wordt gedetecteerd (bijvoorbeeld via Buienradar).
Gebruiker moet per kamer aangeven of de ventilator wel of niet moet uitschakelen bij regen.
Regendrempel: De gebruiker kan een drempelwaarde instellen voor regen (in mm), met advies over waarden voor motregen, miezeren en harde regen. Een aanbevolen drempelwaarde net onder motregen moet worden voorgesteld.
3. Afzuiginstallatie
Er is een optionele afzuiginstallatie die onafhankelijk van de ventilatoren werkt.
De afzuiginstallatie moet uitgeschakeld worden als de buitentemperatuur hoger is dan de binnentemperatuur, om te voorkomen dat warme lucht wordt aangezogen.
Deze installatie moet ook uitschakelbaar zijn in vakantiemodus.
4. Vakantiemodus
Het systeem moet een vakantiemodus ondersteunen die kan worden geactiveerd via een vakantiesensor (bijvoorbeeld een helper in Home Assistant).
Bij vakantiemodus moeten de ventilatoren, afzuiginstallatie, en andere systemen naar keuze van de gebruiker worden uitgeschakeld. De gebruiker moet kunnen kiezen welke apparaten uitgeschakeld worden.
Overwerktijd: Een "override"-functie moet beschikbaar zijn zodat de ventilatoren tijdelijk handmatig kunnen worden bediend, maar na een ingestelde tijd (standaard 30 minuten, maar configureerbaar door de gebruiker) neemt het systeem de controle weer over.
5. Automatische Seizoensmodus
Seizoensmodus: Het systeem moet de ventilatie aanpassen op basis van de actuele temperatuur in plaats van vaste datums. De gebruiker moet een grenswaarde kunnen instellen voor winter- en zomerseizoenen (bijvoorbeeld winter onder 10°C, zomer boven 25°C).
In de winter moet de ventilatie uitgeschakeld worden en moet alleen de afzuiginstallatie werken op basis van luchtvochtigheid en temperatuur.
In de zomer moeten de ventilatoren aanstaan om de lucht te circuleren, maar alleen als dit bijdraagt aan een aangename binnentemperatuur.
6. Modulaire opzet en uitklapbare secties
Het script moet modulair opgebouwd zijn, zodat het eenvoudig kan worden uitgebreid.
De gebruiker moet zelf kunnen kiezen hoeveel ventilatoren worden gebruikt en in welke ruimtes.
Uitklapbare secties: Voor elke functie (ventilatoren, weersensoren, afzuiging, etc.) moet er een aparte, uitklapbare sectie in de blueprint zijn, zodat het overzichtelijk blijft.
Nederlandse benamingen en uitleg: Alle functies en beschrijvingen in het script moeten in het Nederlands zijn om het begrijpelijk te houden voor de gebruiker. Uitleg voor de gebruiker moet in de interface worden opgenomen, met adviezen over bijvoorbeeld regendrempelwaarden.
7. Sensoren en gegevensbronnen
De gebruiker moet de mogelijkheid hebben om zelf een weersensor te kiezen (bijvoorbeeld Buienradar of forecast_thuis). Deze sensor moet relevante waarden zoals temperatuur, luchtvochtigheid, en neerslag doorgeven.
De blueprint moet flexibel genoeg zijn om deze gegevens te gebruiken zonder hardcoded sensors.
Temperatuursensor per ruimte: Elke ruimte moet een eigen temperatuursensor kunnen hebben of, als er geen sensor beschikbaar is, de sensor van een andere ruimte gebruiken. Dit moet configureerbaar zijn door de gebruiker.
Luchtvochtigheidssensor: In sommige ruimtes is de luchtvochtigheidssensor optioneel, maar in de zolder is deze verplicht vanwege specifieke omstandigheden.
8. Foutafhandeling en optimalisatie
Valideer alle templates en condities om te voorkomen dat fouten optreden zoals "unexpected char" en "undefined variable". Het script moet foutloos importeerbaar en uitvoerbaar zijn in Home Assistant.
Check status van switches: Voordat een ventilator of afzuiging wordt in- of uitgeschakeld, moet de huidige status worden gecontroleerd om onnodige schakelingen te voorkomen.
Overige opmerkingen
Versiebeheer: Het is belangrijk om versiebeheer toe te passen voor elke update van de blueprint. Elke nieuwe versie moet een duidelijk versienummer krijgen (bijvoorbeeld versie 13.1, versie 13.2, etc.).
Toekomstige uitbreidingen: Er moet ruimte zijn om het systeem in de toekomst uit te breiden met extra systemen zoals rolluiken of airconditioning.
