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

    from  microbit  import  *  
      
    pin0.write_digital(1)
Dit zet pin0 **aan**.
        
En:

    from  microbit  import  *
    
    pin0.write_digital(0)

zet pin0 **uit**.
