
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

Een led moet **altijd via een weerstand** worden aangesloten.  
Zonder weerstand kan de led kapot gaan.

Aansluiten:

P0 → weerstand → led → GND

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
