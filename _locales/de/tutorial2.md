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

## Sensor programmieren

Passe dazu den Sensortyp DHT11 / DHT22 an (betrachte auch die Hilfe 💡).
Füge den Block DHT11 / DHT22 hinzu und passe den Sensor an. 


⚠️ Setze den Wert **Serial Output** auf **falsch**
 ![Block hinzufügen](https://github.com/gitalm/-climpase----use-external-sensor/blob/master/2022-01-30_17-37.png?raw=true)

## 📡>> Daten übermitteln

Sende die Werte ```||radio:sende Wertepaar||``` an den zweiten micro:bit in derselben Funkgruppe (betrachte auch die Hilfe 💡). 


Verwende dafür eindeutige Werte, etwa
* **Hum** und ```||arrays:Read humidity||```
* **Temp** und ```||arrays:Read temperature||```


 ![Block hinzufügen](https://github.com/gitalm/-climpase----use-external-sensor/blob/master/2022-01-30_17-44.png?raw=true)


## Sender finalisieren

Lade das Programm auf deinen ersten micro:bit und öffne ein neues Fenster für die Programmierung des Empfängers.

