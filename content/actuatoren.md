
# Actuatoren aansturen met de micro:bit

Actuatoren zijn onderdelen die **iets laten bewegen of zichtbaar maken**.  
In dit robotproject gebruiken we onder andere:

- leds (licht)
- motoren (beweging)
- grijparmen (servo)

De micro:bit stuurt actuatoren aan via pins zoals **P0, P1 en P2**.

## Led aansturen

Een led is de eenvoudigste actuator. Hij kan alleen:

- aan
- uit


# Hoe sluit je een led goed aan?

Een led werkt maar in **één richting**.  
Daarom moet je goed opletten welke kant naar **plus** en welke kant naar **min (GND)** gaat.

Een led moet **altijd via een weerstand** worden aangesloten.  
Zonder weerstand kan de led kapot gaan.

Aansluiten:

P0 → weerstand → led → GND

## Welke kant van een led is plus en min?

Je kunt dit op drie manieren herkennen:

| kenmerk | betekenis |
|--------|-----------|
| lange poot | plus (anode) |
| korte poot | min (kathode) |
| platte rand van de led | min (kathode) |

Vuistregel:

lange poot → via weerstand naar pin  
platte kant → naar GND

Dus meestal sluit je een led zo aan:


pin → weerstand → lange poot led
platte kant led → GND

## Waarom moet een led de juiste richting hebben?

Een led is een **diode**.  
Dat betekent dat stroom er maar in één richting doorheen kan lopen.

Als je hem omdraait:

- gaat de led niet branden
- maar meestal gaat hij niet kapot (als je een weerstand gebruikt)

## Altijd een weerstand gebruiken

Een led moet **altijd via een weerstand** worden aangesloten.

Zonder weerstand kan:

- de led kapot gaan
- of de micro:bit beschadigd raken

Gebruik daarom altijd:

pin → weerstand → led → GND


## Werkt de led niet?

Controleer dan:

1. zit de platte kant aan GND?
2. zit er een weerstand in de schakeling?
3. zit de led goed in het breadboard?
4. gebruik je de juiste pin in je programma?

In veel gevallen hoef je de led alleen even om te draaien.

![](figures/led.jpg)

Voorbeeldprogramma:

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
Led bedienen met knop A en knop B:

```python
from  microbit  import  *  
  
# instellingen  
LED_PIN  =  pin0  
  
LED_AAN  =  1  
LED_UIT  =  0  
  
  
# programma  
while  True:  
	if  button_a.was_pressed():  
		LED_PIN.write_digital(LED_AAN)  
	if  button_b.was_pressed():  
		LED_PIN.write_digital(LED_UIT)
```
## Motor aansturen

Een motor heeft meer stroom nodig dan de micro:bit kan leveren.  
Daarom gebruik je:

-   een **transistor**
-   een **externe batterij**

De micro:bit stuurt de transistor aan.  
De transistor schakelt vervolgens de motor.

Aansluiten (vereenvoudigd):

micro:bit → transistor → motor → batterij

Motor aansturen:

```python
from microbit import *

# instellingen
MOTOR_PIN = pin0
MOTOR_AAN = 1
MOTOR_UIT = 0

# programma
while True:    
	MOTOR_PIN.write_digital(MOTOR_AAN)
```

Motor snelheid regelen (PWM):

```python
from microbit import *

# instellingen

MOTOR_PIN = pin0
MOTOR_LANGZAAM = 300
MOTOR_SNEL = 700

# programma
while True:    
	MOTOR_PIN.write_analog(MOTOR_SNEL)
```

Waarden liggen tussen:

0 – 1023

Dus:

-   lage waarde = langzaam
-   hoge waarde = snel

## Grijparm aansturen (servo)

Een grijparm wordt meestal bestuurd met een **servo-motor**.

Een servo kan draaien naar een **specifieke positie**, bijvoorbeeld:

-   open
-   dicht

Servo aansluiten:

rood → 3V  
zwart → GND  
geel → P0

Voorbeeldprogramma:

```python
from microbit import *

# instellingen
SERVO_PIN = pin0
GRIJPER_OPEN = 26
GRIJPER_DICHT = 77

# programma
SERVO_PIN.write_analog(GRIJPER_OPEN)
```

Grijper bedienen met knop A en B:

```python
from microbit import *

# instellingen

SERVO_PIN = pin0
GRIJPER_OPEN = 26
GRIJPER_DICHT = 77

# programma
while True:    
	if button_a.was_pressed():        
		SERVO_PIN.write_analog(GRIJPER_OPEN)
	if button_b.was_pressed():        
		SERVO_PIN.write_analog(GRIJPER_DICHT)
```
