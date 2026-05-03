
# Communiceren met twee micro:bits via radio
Je kunt twee micro:bits met elkaar laten communiceren via radiosignalen.
In dit robotproject gebruiken we:
- één micro:bit als afstandsbediening
- één micro:bit op de robot
Beide micro:bits krijgen **exact dezelfde programmacode**.
Daardoor hoef je maar één programma te onderhouden.

## Hoe werkt dit?

We gebruiken twee micro:bits:

| micro:bit | functie |  
|----------|---------|  
| micro:bit 1 | afstandsbediening |  
| micro:bit 2 | robotbesturing |

Wanneer je op knop A drukt:
- stuurt de micro:bit een radiosignaal
- voert de micro:bit zelf ook dezelfde actie uit

De andere micro:bit ontvangt het radiosignaal en voert dezelfde actie uit.
Zo kun je de robot:
- rechtstreeks bedienen
- én via een afstandsbediening

met hetzelfde programma.
## Radio aanzetten
Om radio te gebruiken moet je eerst de radio-module importeren en inschakelen.

```python

from microbit import *
import radio

# instellingen

RADIO_GROEP = 7
radio.on()
radio.config(group=RADIO_GROEP)
```

De `RADIO_GROEP` zorgt ervoor dat micro:bits alleen luisteren naar berichten binnen dezelfde groep.

Gebruik voor jouw robotgroep dus steeds hetzelfde groepsnummer.

## Signalen afspreken

We spreken vaste berichten af.

```python
RIJD_VOORUIT = "vooruit"
STOP = "stop"
```

Deze berichten sturen we via radio.

## Eén actie uitvoeren op twee manieren

De robot moet vooruit rijden als:

-   knop A wordt ingedrukt
-   of het radiosignaal `"vooruit"` wordt ontvangen

Dat schrijven we zo:

```python
from microbit import *
import radio

# instellingen

RADIO_GROEP = 7
LINKER_MOTOR_PIN = pin0
RECHTER_MOTOR_PIN = pin1
MOTOR_AAN = 1
MOTOR_UIT = 0
RIJD_VOORUIT = "vooruit"
STOP = "stop"
radio.on()
radio.config(group=RADIO_GROEP)

# functies

def rij_vooruit():    
	LINKER_MOTOR_PIN.write_digital(MOTOR_AAN) 
	RECHTER_MOTOR_PIN.write_digital(MOTOR_AAN)

def stop_robot():    
	LINKER_MOTOR_PIN.write_digital(MOTOR_UIT) 
	RECHTER_MOTOR_PIN.write_digital(MOTOR_UIT)
# programma

while True:    
	bericht = radio.receive()    
	if button_a.was_pressed() or bericht == RIJD_VOORUIT:   
		radio.send(RIJD_VOORUIT)        
		rij_vooruit()    
	
	if button_b.was_pressed() or bericht == STOP:
		radio.send(STOP)
		stop_robot()
```

Hier gebeurt dus hetzelfde bij:

```
button_a.was_pressed()
```

en bij:

```
bericht == RIJD_VOORUIT
```

Dat betekent:

lokale knop = radiosignaal = dezelfde actie


## Waarom gebruiken we dezelfde code?

Beide micro:bits krijgen dezelfde code.

Dat heeft voordelen:

-   je hoeft maar één programma te onderhouden
-   je kunt de robot direct bedienen
-   je kunt de robot ook via afstandsbediening bedienen
-   je hoeft niet steeds te onthouden welke micro:bit welke versie van de code heeft

De micro:bit op de robot reageert dus op:

-   eigen knoppen
-   radiosignalen van de afstandsbediening

De afstandsbediening stuurt signalen, maar kan dezelfde actie ook lokaal uitvoeren.  
Als daar geen motor op aangesloten is, gebeurt er lokaal gewoon niets zichtbaars.
