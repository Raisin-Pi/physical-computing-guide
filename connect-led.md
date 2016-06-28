# Connecter une Led sans Breadboard

1.  La LED a une branche courte et une branche longue. Insérez un câble de liaison sur la branche longue.

2.  Insérez une résistance dans l'autre extrémité de ce même câble de liaison.

3.  Ajoutez un autre câble de liaison de l'autre côté de la résistance.

4.  Prendre un autre câble de liaison et insérer le sur la branche courte de la LED. Vous devriez vous retrouver avec quelque chose qui ressemble à ceci:


    ![](images/led-wired.png)

    Les broches d'entrée et de sortie universelles (GPIO) sur le Raspberry Pi peuvent communiquer avec le monde extérieur et peut être contrôlées ou programmées. Les différentes broches ont des rôles différents. Pour nous faciliter la vie, les broches sont numérotées pour référence.


1. Connectez votre LED sur les broches 3.3 Volts et à la masse (GND) comme indiqué ci-dessous

    ![](images/led-3v3.png)

1.  Plug in the micro USB power supply and you should see some text appear on your screen.

    Now you have a circuit and the LED should be on. If it is not, make sure that you have plugged the jumper wires into the correct pins by checking the diagram above.

    Why does the LED shine? When the circuit is plugged into the Raspberry Pi GPIO pins, electricity flows through the circuit. The flow is called the current. The LED lights up only when electric current flows from the long leg through the bulb to the short leg. The resistor reduces the amount of electric current passing through the circuit. This protects the LED from breaking, as a high current will make the light shine more brightly and then stop working.

1. Now that you know your LED is working you can connect it to another pin which the Raspberry Pi can switch on and off. Move the wire from the 3.3v pin to any of the GPIO pins coloured yellow on this diagram.

![Pin Diagram](images/gpio-numbers-pi2.png)

1. In the example below pin 17 has been used, when connected the LED will most likely turn off.

![Pin 17](images/led-gpio17.png)

Once you have connected your LED you can control it using a number of programing languages.

|  |     |
| --- | --- |
| [![Scratch](images/scratch_logo.png)](test-led-scratch.md) | [![Scratch](images/python_logo.png)](test-led-python.md) |


[Retour vers "Commencer avec l'informatique Physique"](worksheet.md)
