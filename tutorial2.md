# 📡 Send and receive external sensor data

## Step 1

### Climapse - Climate 🌍🌡️ changing over Time  ⏳️

In the following tutorial for the micro:bit you learn 
1. measure sensor data from external sensor DHT11 / DHT22
2. send the data to a second micro:bit

## micro:bit initialise

For the start we show a ghost symbol 👻 ``||basic.showIcon||``, so we know the status of the micro:bit. 
Add the micro:bit to a radio group ```||radio:setze Funkgruppe auf||```, e.g. **24**.

```blocks
radio.setGroup(24)
basic.showIcon(IconNames.Ghost)
```

## programme sensor

Choose the right type of sensor DHT11 / DHT22 an (use the additional help💡).
Add the blocks for the DHT11 / DHT22 sensor to your editor and choose the correct sensor to initialise it. 


⚠️ Chosse for **Serial Output** the value **wrong**
 ![Block hinzufügen](https://github.com/gitalm/-climpase----use-external-sensor/blob/master/2022-01-30_17-37.png?raw=true)

## 📡>> send data

Send the data ```||radio:sende Wertepaar||``` to a second micro:bit in the same radio group (use the additional help💡).


Use appropraite values to send like
* **Hum** und ```||arrays:Read humidity||```
* **Temp** und ```||arrays:Read temperature||```


 ![Block hinzufügen](https://github.com/gitalm/-climpase----use-external-sensor/blob/master/2022-01-30_17-44.png?raw=true)


## finalise the sender micro:bit

Download your code the first micro:bit, which acts as sender. Open now a second Tab and we start to programme the receiver micro:bit.

