# Ventilatie- en Afzuigsysteem Automatisering

## Doel van de Automatisering

Deze automatisering is bedoeld om een ventilatie- en afzuigsysteem te beheren voor meerdere kamers (woonkamer, slaapkamer, kantoor, zolder) op basis van verschillende omgevingsfactoren, zoals temperatuur, vochtigheid, regen, en wind. De automatisering zorgt ervoor dat het systeem energie-efficiënt werkt en dat de ruimtes niet onverwacht te koud worden door het binnenhalen van koude lucht.

### Overzicht van de Wensen:
1. **Ventilatie per kamer**: 
   - Ventilatoren in de woonkamer, slaapkamer, kantoor en zolder moeten onafhankelijk werken.
   - Elke ventilator schakelt afhankelijk van de ingestelde temperatuur in de kamer en externe weersomstandigheden (buitentemperatuur, regen, etc.).

2. **Data uit weerstations**:
   - Er wordt één weerstation gebruikt (Buienradar). Attributen zoals buitentemperatuur, regen, luchtvochtigheid worden opgehaald en gebruikt om te bepalen of de ventilatoren aan moeten.
   - De mechanische ventilatie moet ook temperatuur en luchtvochtigheid in de gaten houden, maar moet niet verplicht zijn.

3. **Bescherming tegen koude lucht**:
   - De ventilatoren mogen niet actief zijn als het in de kamer te koud wordt door koude lucht van buiten.
   - Elke kamer moet een temperatuurdrempel hebben om dit te voorkomen (bijvoorbeeld standaard 21 graden, met een marge die kan worden aangepast).

---

## Sensorgegevens en Waarden

| Naam sensor in script        | Entiteit                      | Waarde                    | Reden gebruik                           |
|------------------------------|-------------------------------|---------------------------|-----------------------------------------|
| **Buitentemperatuur sensor**  | `weather.buienradar`           | Attribuut: `temperature`   | Om te controleren of het buiten kouder is dan binnen. |
| **Regen sensor**              | `weather.buienradar`           | Attribuut: `precipitation` | Om ventilatoren uit te schakelen bij regen. |
| **Luchtvochtigheid sensor**   | `weather.buienradar`           | Attribuut: `humidity`      | Om luchtvochtigheid binnen en buiten te vergelijken. |
| **Binnen temperatuur sensor** | `sensor.binnen_temperatuur_*`  | Temp (Woonkamer, Slaapkamer, Kantoor, Zolder) | Om te bepalen of het binnen warmer is dan buiten. |

---

## Geconstateerde Fouten en Oplossingen

Hieronder een overzicht van de meest voorkomende fouten en hoe ze voorkomen en opgelost kunnen worden:

1. **Onjuiste entiteit-referenties**:
   - Fout: "Entity `{{ input('woonkamer_ventilator') }}` is neither a valid entity ID nor a valid UUID".
   - Oplossing: Vermijd gebruik van `{{ input }}` binnen de `entity_id`. Dit moet een concrete entiteit zijn.
   
2. **BluePrint-selector issues**:
   - Fout: "Invalid blueprint: Only one type can be specified. Found entity, multiple for dictionary value".
   - Oplossing: Gebruik `entity:` zonder de `multiple:` optie als er maar één entiteit vereist is.

3. **Template Errors**:
   - Fout: "Template error: float got invalid input 'unknown' when rendering template".
   - Oplossing: Voeg standaardwaarden toe aan templates (`default`), zodat ze ook correct werken als een sensor geen waarde levert.

4. **Weersensor restricties**:
   - Fout: Niet in staat om `weather.buienradar` te selecteren.
   - Oplossing: Controleer dat de juiste entiteit beschikbaar is in de integratie en gebruik alleen het `weather`-domein voor Buienradar.

---

## Volgende Stappen

1. **Optimalisatie van ventilatorbesturing**:
   - We zullen ervoor zorgen dat ventilatoren voor kantoor en zolder juist werken.
   
2. **Implementatie van mechanische ventilatie**:
   - Dit moet optioneel zijn en geactiveerd kunnen worden op basis van binnen- en buitentemperatuur, evenals luchtvochtigheid.

3. **Dashboard voor weergave en controle**:
   - We gaan werken aan een dashboard waar alle ventilatoren, temperaturen en instellingen in real-time bekeken en aangepast kunnen worden.

---

## Voorbeeld YAML (Automation):

```yaml
alias: Ventilatie Automatisering
description: ""
use_blueprint:
  path: bibabouke/vent7.yaml
  input:
    woonkamer_ventilator: switch.ventilator_woonkamer
    slaapkamer_ventilator: switch.ventilator_slaapkamer
    kantoor_ventilator: switch.ventilator_kantoor_2
    zolder_ventilator: switch.ventilator_zolder
    buitentemperatuur_sensor: weather.buienradar
    gewenste_temperatuur_woonkamer: input_number.gewenste_temperatuur_woonkamer
    gewenste_temperatuur_slaapkamer: input_number.gewenste_temperatuur_slaapkamer
    marge: input_number.temperatuur_marge
