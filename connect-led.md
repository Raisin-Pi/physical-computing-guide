# Connecter une Led sans Breadboard

1.  La LED a une branche courte et une branche longue. Insérez un câble de liaison sur la branche longue.

2.  Insérez une résistance dans l'autre extrémité de ce même câble de liaison.

3.  Ajoutez un autre câble de liaison de l'autre côté de la résistance.

4.  Prenez un autre câble de liaison et insérez-le sur la branche courte de la LED. Vous devriez vous retrouver avec quelque chose qui ressemble à ceci:


    ![](images/led-wired.png)

    Les broches d'entrée et de sortie universelles (GPIO) sur le Raspberry Pi peuvent communiquer avec le monde extérieur et peut être contrôlées ou programmées. Les différentes broches ont des rôles différents. Pour nous faciliter la vie, les broches sont numérotées.


5. Connectez votre LED sur les broches 3.3 Volts et à la masse (GND) comme indiqué ci-dessous

    ![](images/led-3v3.png)

6.  Branchez l'alimentation micro USB et vous devriez voir un texte apparaître sur votre écran.

    Maintenant, vous avez un circuit et la LED devrait être allumée. Dans le cas contraire, assurez-vous d'avoir branché les câbles de liaison dans les broches corrspondantes en vérifiant le schéma ci-dessus.

    Pourquoi la LED brille ? Lorsque le circuit est branché sur les broches GPIO du Raspberry Pi, l'électricité circule à travers le circuit. Le flux est appelé le courant électrique. La LED est allumée uniquement lorsque le courant électrique circule de la branche longue à travers l'ampoule jusqu'à la branche courte. La résistance diminue la quantité de courant électrique passant à travers le circuit. Ceci protège la LED, puisqu'un courant élevé fera briller la lumière plus vivement et s'éteindra plus rapidement.
    

7. Maintenant que vous savez que votre LED fonctionne, vous pouvez la connecter à une autre broche que le Raspberry Pi peut allumer et éteindre. Déplacez le fil de la broche de 3.3 V sur l'une des broches GPIO de couleur jaune sur ce diagramme.


![Pin Diagram](images/gpio-numbers-pi2.png)

8. Dans l'exemple ci-dessous, la broche 17 a été utilisée. Lorsqu'elle est connectée, la LED sera très probablement éteinte.

![Pin 17](images/led-gpio17.png)

Une fois que vous avez connecté votre LED, vous pouvez la contrôler en utilisant un certain nombre de langages de programmation.

|  |     |
| --- | --- |
| [![Scratch](images/scratch_logo.png)](test-led-scratch.md) | [![Scratch](images/python_logo.png)](test-led-python.md) |


[Retour vers "Commencer avec l'informatique Physique"](worksheet.md)
