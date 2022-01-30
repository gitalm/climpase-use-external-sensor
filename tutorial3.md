# 📡 Send and receive external sensor data

## Step 1

### Climapse - Climate 🌍🌡️ changing over Time  ⏳️

Im folgenden Tutorial lernst Du
1. Sensordaten von DHT11 / DHT22 zu messen
2. Sensordaten zu senden

## micro:bit initialisieren

Zum Start lassen wir einfach Geistsymbol 👻 ``||basic.showIcon||`` einblenden, damit wir wissen,
ob der Microbit läuft. Füge den micro:bit auch einer ```||radio:setze Funkgruppe auf||```, beispielsweise **24** hinzu.

```blocks
radio.setGroup(24)
basic.showIcon(IconNames.Ghost)
```

## Variablen initialisieren

Um die empfangenen Werte auszugeben, müssen diese in Variablen zwischengepeichert werden. Daher erstellen wir
``||variable:Erstelle Variable ||``  **Tmp** für die Temperatur und ``||variable:Erstelle Variable||`` **Hum** für die Luftfeuchtigkeit. 

 ![Block hinzufügen](https://github.com/gitalm/-climpase----use-external-sensor/blob/master/2022-01-30_19-08.png?raw=true)


## Werte auslesen I 

Um die beiden gesendeten Werte auszulesen, muss man zuerst ``||radio:Wenn Wertepaar empfangen||`` einfügen. Nun muss man mit Hilfe der 
Logikbausteinen ||logic:Wenn wahr dann ... ansonsten ||`` auswählen, ob man den Temperaturwert *Tmp* oder den Luftfeuchtigkeitswert *Hum* empfangen hat.

```blocks
radio.onReceivedValue(function (name, value) {
    if ( "Tmp" == name) {
    
    } else {
    
    }
})
```

## Werte auslesen II

Nun muss in den Bedingung der Name verglichen werden, ob man die Temperatur ``||logic:Wenn "Tmp" == name||`` setze 
den Werte der Variable ``||variable:Temp||`` auf den Wert **value**.
Falls der Wert für die Luftfeuchtigkeit empfangen wurde, soll der dazugehörige Wert **value** in der Variablen ``||variable:Hum||`` gespeichert
werden.

```blocks
radio.onReceivedValue(function (name, value) {
    if ("Tmp" == name) {
        Temp = value
    } else {
        Hum = value
    }
})
```

## Werte an PC senden 

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
