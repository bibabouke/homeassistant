Beste Chat, 

We gaan een Gebouw Beheer Systeem - Ventilatie ontwerpen voor Home Assistant.

Deze automatisering is bedoeld om een ventilatie- en afzuigsysteem te beheren voor meerdere kamers (woonkamer, slaapkamer, kantoor, zolder) op basis van verschillende omgevingsfactoren, zoals temperatuur, vochtigheid, regen, en wind. De automatisering zorgt ervoor dat het systeem energie-efficiënt werkt en dat de ruimtes niet onverwacht te koud worden door het binnenhalen van koude lucht.

We vergelijken binnen sensoren met buiten om zo koude lucht van buiten naar binnen te krijgen als het binnen te warm is, maar we maken het huis niet te koud. Als het binnen al aangenaam is, moeten we het niet nog kouder maken. 

Er wordt één weerstation gebruikt (Buienradar). Attributen zoals buitentemperatuur, regen, luchtvochtigheid worden opgehaald en gebruikt om te bepalen of de ventilatoren aan moeten.
De mechanische ventilatie moet ook temperatuur en luchtvochtigheid in de gaten houden, maar moet niet verplicht zijn.

De ventilatoren mogen niet actief zijn als het in de kamer te koud wordt door koude lucht van buiten.
Elke kamer moet een temperatuurdrempel hebben om dit te voorkomen (bijvoorbeeld standaard 21 graden, met een marge die kan worden aangepast).

Om fouten te voorkomen, werken we niet direct met hardcoded sensoren of hun data, maar halen we die op en geven die dan door aan te gebruiken variabelen. Zo voorkomen we dat bij storing of uitval van een sensor, het script vastloopt. 

Ik ga je een script sturen van een voorbeeld voor ventilatoren. Geef beknopt aan wat je eruit hebt geleerd op coderingsniveau.
