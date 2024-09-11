Overzicht van Wensen voor Insectenlamp Automatisering
Insectenlampen

Beschrijving: Apparaten die insecten aantrekken en vernietigen wanneer ze worden geactiveerd.
Input Type: Meerdere schakelaars of lampen
Standaardwaarde: Geen standaardwaarde; de gebruiker moet dit selecteren.
UI Uitleg: "Selecteer de insectenlampen die je wilt aansturen."
Weersensor

Beschrijving: Een sensor die temperatuur, luchtvochtigheid en regen meet.
Input Type: Weersensor (Buienradar of een andere ondersteunde sensor)
Standaardwaarde: Geen standaardwaarde; de gebruiker moet dit selecteren.
UI Uitleg: "Selecteer de weersensor die temperatuur, luchtvochtigheid en regen meet. Dit is nodig om de lampen dynamisch aan te sturen op basis van het weer."
Minimale Temperatuur

Beschrijving: De temperatuur waaronder insecten niet meer actief zijn en de lampen niet worden geactiveerd.
Input Type: Getal (in °C)
Standaardwaarde: 10 °C
UI Uitleg: "Stel de minimumtemperatuur in waarbij de insectenlampen nog geactiveerd worden. Insecten zijn doorgaans niet actief onder deze temperatuur."
Maximale Temperatuur

Beschrijving: De temperatuur boven welke insecten minder actief worden en de lampen niet worden geactiveerd.
Input Type: Getal (in °C)
Standaardwaarde: 35 °C
UI Uitleg: "Stel de maximumtemperatuur in waarbij de insectenlampen nog geactiveerd worden. Insecten zijn minder actief boven deze temperatuur."
Minimale Luchtvochtigheid

Beschrijving: De luchtvochtigheid waaronder insecten niet actief zijn en de lampen niet worden geactiveerd.
Input Type: Getal (in %)
Standaardwaarde: 60%
UI Uitleg: "Stel de minimum luchtvochtigheid in waarbij de insectenlampen nog geactiveerd worden. Hogere luchtvochtigheid trekt meer insecten aan."
Maximale Regenintensiteit

Beschrijving: De maximale regenval waarbij de lampen nog worden ingeschakeld.
Input Type: Getal (in mm/h)
Standaardwaarde: 0.5 mm/h
UI Uitleg: "Stel de maximale regenintensiteit in. Bij hevige regenval zijn insecten minder actief, dus de lampen zullen niet worden geactiveerd bij regenval boven deze waarde."
Handmatige Bediening (optioneel)

Beschrijving: Een schakelaar om de lampen handmatig in of uit te schakelen.
Input Type: Schakelaar
Standaardwaarde: Optioneel; geen standaardwaarde.
UI Uitleg: "Selecteer een schakelaar die handmatige bediening mogelijk maakt. Hiermee kunnen de lampen handmatig aan of uit worden gezet, ongeacht de weersomstandigheden."
Vakantieschakelaar

Beschrijving: Schakelt de vakantieschakelaar in of uit.
Input Type: Boolean
Standaardwaarde: Geen standaardwaarde; de gebruiker moet dit selecteren.
UI Uitleg: "Schakel de vakantiemodus in om te voorkomen dat de lampen onnodig worden ingeschakeld wanneer niemand thuis is."
Seizoensmodus

Beschrijving: Bepaalt of de lampen moeten werken op basis van zomer- of wintercondities.
Input Type: Keuzemenu (opties: Zomer, Winter)
Standaardwaarde: Zomer
UI Uitleg: "Selecteer de seizoensmodus. In de zomer blijven de lampen langer aan dan in de winter, omdat insecten 's zomers actiever zijn."
Duur van Insectenlampen

Beschrijving: De tijdsduur dat de insectenlampen aan moeten blijven na activatie.
Input Type: Getal (in minuten)
Standaardwaarde: 30 minuten
UI Uitleg: "Stel de tijd in dat de insectenlampen moeten blijven branden na activatie. Een duur van 30 minuten is aanbevolen voor effectieve insectenbestrijding."
Hysteresis voor Inschakeling

Beschrijving: De marge die wordt aangehouden om te voorkomen dat de lampen te snel aan- of uitgaan bij kleine schommelingen in temperatuur of luchtvochtigheid.
Input Type: Getal (in °C of %)
Standaardwaarde: 0.5 °C of %
UI Uitleg: "Stel de hysteresiswaarde in om te voorkomen dat de lampen te vaak schakelen bij kleine veranderingen in temperatuur of luchtvochtigheid."
Aanvullende Logica:
Fallback voor Onbeschikbare Sensorwaarden

Indien de weersensor tijdelijk niet beschikbaar is, gebruik je standaard fallback-waarden zoals:
Temperatuur: 20 °C
Luchtvochtigheid: 60%
Regenintensiteit: 0 mm/h
Logging en Foutafhandeling

Alleen noodzakelijke fouten moeten worden gelogd. Dit voorkomt onnodige belasting van het systeem.
Triggers

De automatisering moet geactiveerd worden door veranderingen in weersomstandigheden (temperatuur, luchtvochtigheid, regen), de handmatige bediening, en de seizoensmodus.
