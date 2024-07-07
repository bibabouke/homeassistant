Ik heb blueprint code geschreven voor Ikea lampen voor Home Assistant. Die code werkt samen met een controller code die ik heb geschreven. Het is dus belangrijk dat je de code respecteert en niets erin verandert en niks weglaat! Ook is de yaml-indeling zeer gevoelig dus voer dat correct uit.

Ik wil alleen 1 klein detail veranderen. Nu werken de kleuren voor de HUE - SATURATION optie in 24 stapjes met 15% stapjes tot 360. Ik wil dat veranderen door te kiezen voor 24 voorgedefinieerde wit/kleur codes.

Waar in de code zou jij dat veranderen en hoe zou je dat doen. Kies een zo klein mogelijke oplossing, die logisch is en waar later de kleurcodes makkelijk in aan te passen zijn. Geef een suggestie waar in de code je dat zou aanpassen en hoe.

Begin de aanpassing met een line by line analyse van mijn code. Gevolgd door opmerkingen waar de hue kleuren nu bepaald worden en wat dat in de huidige code betekent. En pas daarna jouw suggestie verwerken in mijn code, zodat ik die direct kan overnemen. 



IKEA kleurindeling (20):


Witte tinten
Koude hemel – 6000 Kelvin
Koud daglicht – 5000 Kelvin
Koudwit – 4000 Kelvin
Zonsopgang – 3000 Kelvin
Warmwit – 2700 Kelvin
Warm schijnsel – 2200 Kelvin
Kaarslicht – 1780 Kelvin
Kleuren
Barnsteen, Perzik, Donkerperzik, Donkerrood, Roze,
Lichtroze, Donkerroze, Lichtpaars, Donkerpaars, Blauw,
Lichtblauw, Lime, Geel
