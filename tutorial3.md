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