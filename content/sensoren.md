
# Sensoren uitlezen met de micro:bit
Sensoren zijn onderdelen die informatie meten uit de omgeving.  In dit robotproject gebruiken we sensoren om te bepalen wat de robot moet doen.
Voorbeelden:
- lichtsensor → meet hoe licht of donker het is
- afstandssensor → meet hoe ver een object weg is

Sensoren sturen informatie **naar** de micro:bit. Dit noemen we **input**.

## Digitale en analoge sensoren

Er zijn twee soorten signalen die sensoren kunnen geven.

### Digitale sensoren
Digitale sensoren hebben maar twee waarden:
- 0 = geen signaal
- 1 = wel signaal

Bijvoorbeeld:een knop ingedrukt of niet.

### Analoge sensoren
Analoge sensoren kunnen veel verschillende waarden geven. Bij de micro:bit liggen deze waarden tussen: 0 – 1023
Bijvoorbeeld:
- hoe licht het is
- hoe ver iets weg is
De meeste sensoren in dit project gebruiken **analoge signalen**.

## Lichtsensor uitlezen
Een lichtsensor meet hoeveel licht er op de sensor valt.
Meer licht → hogere waarde  
Minder licht → lagere waarde

Voorbeeldprogramma:
```python
from microbit import *

# instellingen

LICHT_SENSOR_PIN = pin1

# programma
while True:    
	lichtwaarde = LICHT_SENSOR_PIN.read_analog()    
	display.scroll(lichtwaarde)
```

De micro:bit meet hier steeds hoeveel licht er binnenkomt en toont dit op het display.

## Reageren op licht (beslissing maken)

Je kunt de robot laten reageren op licht.

Bijvoorbeeld:

bij weinig licht gaat een led aan.

```python
from microbit import *

# instellingen

LICHT_SENSOR_PIN = pin1
LED_PIN = pin0

DONKER_DREMPEL = 400
LED_AAN = 1
LED_UIT = 0

# programma

while True:    
	lichtwaarde = LICHT_SENSOR_PIN.read_analog()    
	if lichtwaarde < DONKER_DREMPEL:        
		LED_PIN.write_digital(LED_AAN)    
	else:        
		LED_PIN.write_digital(LED_UIT)
```

Hier bepaalt de variabele `DONKER_DREMPEL` wanneer het donker genoeg is.


## Afstandssensor uitlezen

Een afstandssensor meet hoe ver een object van de robot staat.

Bijvoorbeeld:

-   dichtbij obstakel
-   ver weg van obstakel

Veel afstandssensoren geven een **analoge waarde** terug.

Voorbeeldprogramma:

```python
from microbit import *

# instellingen

AFSTAND_SENSOR_PIN = pin2

# programma
while True:    
	afstandwaarde = AFSTAND_SENSOR_PIN.read_analog() 
	display.scroll(afstandwaarde)
```

Hoe dichter een object bij de sensor komt, hoe meer de waarde verandert.

Let op:

de exacte betekenis van de waarde hangt af van het type sensor.


## Reageren op afstand

De robot kan stoppen wanneer een object te dichtbij komt.

```python
from microbit import *

# instellingen
AFSTAND_SENSOR_PIN = pin2
MOTOR_PIN = pin0
OBSTAKEL_DREMPEL = 500
MOTOR_AAN = 1
MOTOR_UIT = 0

# programma
while True:    
	afstandwaarde = AFSTAND_SENSOR_PIN.read_analog()    
	if afstandwaarde > OBSTAKEL_DREMPEL:        
		MOTOR_PIN.write_digital(MOTOR_UIT)    
	else:        
		MOTOR_PIN.write_digital(MOTOR_AAN)
```

Hier stopt de motor wanneer een obstakel dichtbij komt.

## Sensorwaarden bekijken tijdens testen

Tijdens het bouwen is het handig om eerst alleen de sensorwaarde te bekijken.

Zo kun je bepalen welke drempelwaarde goed werkt:

```python
from microbit import *

# instellingen

SENSOR_PIN = pin1

# programma
while True:    
	sensorwaarde = SENSOR_PIN.read_analog()    
	display.scroll(sensorwaarde)
```

Test dit eerst voordat je beslissingen toevoegt aan je programma.
