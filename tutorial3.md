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

The serial port writes the data directly to the **console** from your editor. The block ``||serial:Schreibe Wertepaar||``  
will be named with the correct measured value, e.g.. *Temp in C* and the stored data in the variable ``||variable:Temp||`` . 
After that you have to add another block  ``||serial:Schreibe Wertepaar||`` 
*Humidity* and the sored value ``||variable:Hum||`` to n.send both to your PC.

```blocks
basic.forever(function () {
    serial.writeValue("T in C", Temp)
    serial.writeValue("Luftfeuchtigkeit", Hum)
})

```

## download programm to your micro:bit

Download the software to your second micro:bit which acts as receiver and is forwarding the data to your PC.


⚠️ Both micro:bits need a power supply and the same radio group!

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

## control data on your PC 📈

If you activate the **show console** within your editor you see the data from your mobile first micro:bit sender. The data can be further proccessed within any calculation software.


 ![Block hinzufügen](https://github.com/gitalm/-climpase----use-external-sensor/blob/master/2022-01-30_19-26.png?raw=true)
