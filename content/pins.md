# Werken met de pins van de micro:bit
De micro:bit heeft aansluitpunten (pins) waarmee je sensoren en onderdelen kunt **uitlezen (input)** of **aansturen (output)**. In deze sectie leer je:

 - welke pins je kunt gebruiken 
 - wat het verschil is tussen digitaal en analoog     
 - hoe input en output werken     
 - hoe je pins gebruikt in Python

## Wat is een pin?
Een pin is een aansluitpunt op de rand van de micro:bit waarmee je signalen kunt lezen of sturen.

Belangrijke pins in dit project zijn:

-   **P0**
-   **P1**
-   **P2**
-   **3V** (plus)
-   **GND** (min)

Gebruik meestal:

-   **3V** → voeding
-   **GND** → terug naar min
-   **P0 / P1 / P2** → signalen

## Input en output
Pins kunnen twee dingen doen:

### Input (invoer)
De micro:bit **meet** een signaal.

Bijvoorbeeld:

-   knop
-   lichtsensor
-   afstandssensor

De micro:bit leest dan wat er gebeurt.

### Output (uitvoer)
De micro:bit **stuurt** een signaal.

Bijvoorbeeld:

-   led
-   motor (via transistor)
-   grijparm

De micro:bit bepaalt dan wat er gebeurt.
### Digitale signalen
Digitale signalen kennen maar twee waarden:

-   0 = uit
-   1 = aan

Voorbeelden:

-   knop ingedrukt of niet
-   led aan of uit
-   motor aan of uit

   
Python voorbeeld:

```python
from  microbit  import  *  

pin0.write_digital(1)
```
Dit zet pin0 **aan**.
        
En:
```python
from  microbit  import  *

pin0.write_digital(0)
```
zet pin0 **uit**.

### Analoge signalen
Analoge signalen kunnen **veel waarden tegelijk hebben**.

Bijvoorbeeld:

0 – 1023

Dat gebruik je bij sensoren zoals:

-   lichtsensor
-   draaiknop
-   afstandssensor

Python voorbeeld:
```python
from  microbit  import  *  
  
waarde  =  pin1.read_analog()  
display.scroll(waarde)
```
### Analoge output
De micro:bit kan ook analoge signalen sturen.

Gebruik dit bijvoorbeeld voor:

-   motorsnelheid
-   servo-aansturing
-   helderheid van een led
```python
from  microbit  import  *  
  
pin0.write_analog(512)
```
Waarden liggen tussen:

0 – 1023

Dus:

-   0 = uit
-   1023 = maximaal
### Welke pins zijn digitaal en analoog?
Het verschilt enigzins in de versie van de micro:bit welke pins je kan gebruiken.
Sommige pins hebben extra functies.

Bijvoorbeeld:

-   verbonden met knoppen
-   verbonden met led-matrix
-   gebruikt voor communicatie

De micro:bit heeft een ingebouwd 5×5 led-scherm.

Dit scherm gebruikt intern ook pins.

Daardoor geldt:

sommige pins werken anders wanneer het scherm actief is.

Als je nauwkeurige metingen doet (bijvoorbeeld analoge sensoren), kan het handig zijn om het scherm uit te schakelen:
```python
display.off()
```
### Voorbeeld: knop als input en led als output
```python
from  microbit  import  *  
  
while  True:  
	if  pin1.read_digital():  
		pin0.write_digital(1)  
	else:  
		pin0.write_digital(0)
```
Hier gebeurt:

knop ingedrukt → led aan  
knop los → led uit
