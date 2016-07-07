# Tester une LED connectée à Python

Avec votre circuit complet, vous êtes maintenant prêt à écrire du code pour allumer la LED.

1. Ouvrez Idle3 dans le menu principal.

    ![Open Idle3](images/open_idle.png)

2. Créer un nouveau programme à partir de l'option : **File** -> **New Window**

3. Entrez le code ci-dessous.

    ```python
    import time
    import RPi.GPIO as GPIO
    GPIO.setmode(GPIO.BCM)
    GPIO.setwarnings(False)

    led = 17

    GPIO.setup(led,GPIO.OUT)
    ```
    Les deux premières lignes indiquent à l'interpréteur Python (la chose qui exécute le code Python) que nous utiliserons une «bibliothèque» . Vous aurez besoin de la bibliothèque `time` afin d'ajouter des temps à votre programme et de la bibliothèque `RPi.GPIO` qui indiquera au Pi comment travailler avec les broches GPIO du Raspberry Pi. Une «bibliothèque» donne à un langage de programmation des commandes supplémentaires qui peuvent être utilisées pour faire effectuer des choses qu'elle ne savait pas faire auparavant. C'est comme l'ajout d'une nouvelle chaîne sur votre téléviseur de sorte que vous pouvez regarder quelque chose de différent. Chaque broche sur le Pi a plusieurs noms différents, de sorte que vous devez dire au programme quel nom doit être utilisé dans la troisième ligne du code. Le deuxième à la dernière ligne indique à Python de ne pas montrer les messages d'avertissement GPIO à l'écran. La dernière ligne indique à Python de définir la broche 17 comme une sortie .


4. Sous le code que vous venez d'entrer, tapez :

    ```python
    print("Light on")
    GPIO.output(led,GPIO.HIGH)
    ```
    La fonction `print` imprime des informations sur le terminal. C'est pratique car il vous indique ce qu'il se passe ; ainsi, même si votre LED ne s'allume pas, vous savez que votre programme est en train de travailler. Si cela arrive, il pourrait y avoir une erreur avec le câblage de votre circuit et vous devez revenir en arrière à travers les étapes ci-dessus pour vérifier.

    La ligne suivante "allume" la broche GPIO 17. Cela signifie réellement  que cette broche est faite pour fournir une puissance de 3,3 volts. C'est suffisant pour alumer la LED dans votre circuit.


5. Le code à ce jour va allumer la LED ; nous allons ajouter un peu de code pour l'éteindre après un certain temps. Dessous votre code actuel, tapez :

    ```python
    time.sleep(1)
    print("Light off")
    GPIO.output(led,GPIO.LOW)
    ```
    La première ligne ajoute une pause ou un délai. Il indique au programme de "dormir" pendant une seconde avant de passer à la ligne suivante dans la séquence de code. Pendant ce temps, votre LED sera allumée parce que vous ne lui avez pas encore dit de faire quelque chose d'autre. Pour éteindre la LED, vous ajoutez une ligne semblable à celle qui a allumé la broche GPIO 17 ; vous remplacez alors GPIO.HIGH avec GPIO.LOW. Cela éteindra la broche car elle ne fournit plus aucune tension.

6. La dernière partie à ajouter à votre programme est :

    ```python
    GPIO.cleanup()
    ```

    La commande GPIO.cleanup() à la fin est nécessaire pour réinitialiser l'état de toutes les broches GPIO lorsque vous quittez le programme. Si vous ne l'utilisez pas, les broches GPIO resteront à l'état où elles étaient la fois dernière.

7.	Enregistrez votre code en cliquant sur **File** et **Save**.

8. C'est maintenant l'heure de vérité ! Cliquez sur **Run** et **Run Module** pour exécuter (ou lancer) votre code.

Retour vers [Commencer avec l'informatique Physique](worksheet.md)
