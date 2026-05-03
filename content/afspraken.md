
# Hoe gebruiken we Python in dit robotproject?
In dit robotproject schrijven we Python-code om sensoren uit te lezen en actuatoren aan te sturen met de micro:bit.  Om de code overzichtelijk en begrijpelijk te houden gebruiken we steeds dezelfde manier van programmeren.Zo kun je makkelijker fouten vinden en elkaars code begrijpen.
## 1. We definiëren pins bovenaan het programma
In plaats van direct `pin0` te gebruiken, geven we pins eerst een naam.Voorbeeld:
```python
from microbit import *

LED_PIN = pin0
```
Waarom doen we dit? Omdat je dan meteen ziet waar de pin voor gebruikt wordt.

Vergelijk:

```python
pin0.write_digital(1)
```

met:

```python
LED_PIN.write_digital(1)
```

De tweede versie is duidelijker.

## 2. We gebruiken variabelen voor vaste waarden

Getallen zoals `1`, `0` of `77` zeggen op zichzelf weinig.

Daarom geven we ze een naam.

Voorbeeld:

```python
LED_AAN = 1
LED_UIT = 0
```

Of bij een servo:

```python
GRIJPER_OPEN = 26
GRIJPER_DICHT = 77
```

Nu wordt de code makkelijker te lezen:

```python
SERVO_PIN.write_analog(GRIJPER_OPEN)
```

## 3. We zetten instellingen altijd bovenaan het programma

Bovenaan het programma staat dus:

-   welke pins we gebruiken
-   welke vaste waarden belangrijk zijn

Bijvoorbeeld:

```python
from microbit import *
SERVO_PIN = pin0
GRIJPER_OPEN = 26
GRIJPER_DICHT = 77
```

Daaronder komt pas de rest van het programma.

## 4. We gebruiken duidelijke namen voor variabelen

Gebruik namen die uitleggen wat iets doet.

Goede voorbeelden:

```python
MOTOR_PIN
LED_PIN
LICHT_SENSOR
AFSTAND_SENSOR
```

Minder goede voorbeelden:

```python
pin
waarde
x
test
```
## 5. We werken met een vaste structuur in elk programma

Onze programma’s hebben meestal deze opbouw:

```python
from microbit import *

# instellingen

LED_PIN = pin0
LED_AAN = 1
LED_UIT = 0

# programma
while True:    
	LED_PIN.write_digital(LED_AAN)
```

Hierdoor kun je snel zien:

-   waar instellingen staan
-   waar het programma begint
-   wat de micro:bit doet

## Waarom werken we zo?

Deze manier van programmeren helpt je om:

-   minder fouten te maken
-   sneller fouten te vinden
-   duidelijkere programma’s te schrijven
-   beter samen te werken in je groep
-   grotere programma’s te begrijpen

Professionele programmeurs werken ook op deze manier.
