# 📡 Send and receive external sensor data

## Step 1

### Climapse - Climate 🌍🌡️ changing over Time  ⏳️

In the following tutorial for the micro:bit you learn to receive sensor data from DHT11 / DHT22 

## micro:bit initialisieren

To know about the status and to distinguish the two micro:bits (sender and receiver) we show a giraffe 🦒 ``||basic.showIcon||``. 
Add your receiver micro:bit to your common radio group ```||radio:setze Funkgruppe auf||```, e.g. **24**. If there are more progammers 👩🏼‍💻👨🏾‍💻 in the room choose different radio groups. 

```blocks
radio.setGroup(24)
basic.showIcon(IconNames.Giraffe)
```

## initialise the variables 

To store the received data and send it to your PC, you have to create variables.
``||variable:Erstelle Variable ||``  **Tmp** for temperature and ``||variable:Erstelle Variable||`` **Hum** the humidity. 

 ![Block hinzufügen](https://github.com/gitalm/-climpase----use-external-sensor/blob/master/2022-01-30_19-08.png?raw=true)


## read the values I 

To read the sended data you first have to add a block ``||radio:Wenn Wertepaar empfangen||``. 
Now you have to use logic  ``||logic:Wenn wahr dann ... ansonsten ||`` to store the data in the correct variable, e.g. the temperature in *Tmp* or humidity *Hum*.
Because there are only two options it is easy to just check for one variable.

```blocks
radio.onReceivedValue(function (name, value) {
    if ( "Tmp" == name) {
    
    } else {
    
    }
})
```

## read values II

The conditions checks the name of the variable  ``||logic:Wenn "Tmp" == name||`` and stores the received vaule in the correct variable 
``||variable:Temp||`` by attributing  **value**.
If the sensor didn't receive the value for the temperaure, you have to store the **value** in the variable ``||variable:Hum||``.

```blocks
radio.onReceivedValue(function (name, value) {
    if ("Tmp" == name) {
        Temp = value
    } else {
        Hum = value
    }
})
```

## send data to PC 💻️

Der serielle Ausgang schreibt die Werte an die **Konsole** des Editors. Der Block ``||serial:Schreibe Wertepaar||``  soll nun die Bezeichnnug
des Wertes, bspw. *Temp in C* und die Variable ``||variable:Temp||`` und ein weiterer Block  ``||serial:Schreibe Wertepaar||`` 
*Luftfeuchtigkeit* und den Wert ``||variable:Hum||`` an den PC schicken.

```blocks
basic.forever(function () {
    serial.writeValue("T in C", Temp)
    serial.writeValue("Luftfeuchtigkeit", Hum)
})

```

## Datei auf micro:bit laden

Lade nun die Software auf den zweiten micro:bit und dieser empfängt nun sogleich die Sensorwerte des ersten micro:bits.


⚠️ Beide micro:bits müssen mit Spannung versorgt sein und in derselben Funkgruppe sein!

```blocks
radio.onReceivedValue(function (name, value) {
    if ("Tmp" == name) {
        Temp = value
    } else {
        Hum = value
    }
})
let Hum = 0
let Temp = 0
radio.setGroup(24)
basic.showIcon(IconNames.Giraffe)
basic.forever(function () {
    serial.writeValue("T in C", Temp)
    serial.writeValue("Luftfeuchtigkeit", Hum)
})

```

## Daten auf der Konsole betrachten

Wenn du nun auf * **Konsole anzeigen** Gerät* klcikst, erscheinen die Messwerte des externen Sensors am frei beweglichen ersten micro:bit.


 ![Block hinzufügen](https://github.com/gitalm/-climpase----use-external-sensor/blob/master/2022-01-30_19-26.png?raw=true)
