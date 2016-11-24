# Tester un détecteur de mouvement (PIR) connecté à Python

Nous allons utiliser le langage de programmation Python pour écrire du code qui permet de détecter des mouvements et imprimer un texte. Lorsque le mouvement est détecté, le détecteur de mouvement PIR met de la puissance à sa broche OUT, que nous avons connectée à la broche GPIO 4 sur le Pi. Donc, dans notre code, nous avons juste besoin de vérifier en permanence la broche 4 pour voir si elle a de la puissance ou non.

Si une broche a de la puissance, nous appelons ça `HIGH` et sinon nous appelons cela `LOW`.

Le programme est assez simple. Nous allons d'abord mettre en place les broches GPIO Raspberry Pi pour nous permettre d'utiliser la broche 4 comme entrée ; elle peut alors détecter lorsque le module PIR envoie de la puissance. Nous avons besoin de vérifier en permanence la broche pour tout changement, donc une boucle `while true` est utilisée pour cela. Ceci est une boucle infinie pour que le programme fonctionne en permanence à moins que nous l'arrêtions manuellement avec `Ctrl + C`.

Nous utilisons ensuite deux variables Booléennes (Vrai ou faux) pour les états précédents et actuels de la broche, l'état précédent étant ce que l'état actuel était au temps précédent autour de la boucle. Dans la boucle, nous comparons l'état antérieur à l'état actuel pour détecter quand ils sont différents. Nous ne voulons pas garder l'affichage d'un message s'il n'y a pas eu de changement.


1. Ouvrez Idle3 dans le menu principal.

![Open Idle3](images/open_idle.png)

2. Créer un nouveau programme à partir de l'option **File** -> **New Window**

3. Entrez le code ci-dessous.

    ```python
    import RPi.GPIO as GPIO
    import time

    sensor = 4

    GPIO.setmode(GPIO.BCM)
    GPIO.setup(sensor, GPIO.IN, GPIO.PUD_DOWN)

    previous_state = False
    current_state = False

    while True:
        time.sleep(0.1)
        previous_state = current_state
        current_state = GPIO.input(sensor)
        if current_state != previous_state:
            new_state = "HIGH" if current_state else "LOW"
            print("GPIO pin %s is %s" % (sensor, new_state))
    ```

4. Appuyez sur `Ctrl + S` et entrez un nom pour le fichier.

5. Lancez maintenant le fichier Python en appuyant sur la touche **F5**.

6. Si vous commencez à vous déplacer ou à vous agiter, la broche du capteur AUGMENTE (HIGH). Continuez à vous agiter et elle va rester élevée, et elle ne reviendra à LOW que si vous ne bougez plus à nouveau. Si le capteur se comporte comme cela, alors tout fonctionne correctement. Sinon, quelque chose ne va pas et vous avez besoin de revenir en arrière et résoudre les problèmes.

    ```
    GPIO pin 4 is HIGH
    GPIO pin 4 is LOW
    GPIO pin 4 is HIGH
    ```

7. Appuyez sur `Ctrl + C` quand vous souhaitez quitter.

8. Sur le module PIR, vous devriez voir deux composants oranges avec des douilles qui ressemblent à un tournevis cruciforme.

    ![](images/pir_potentiometers.png)
    
    Ceux-ci sont appelés potentiomètres et ils vous permettent de régler la sensibilité du capteur et le temps de détection. Nous suggérons de régler la sensibilité au maximum et le temps au minimum, mais c'est vous qui décidez.

Retour vers [Commencer avec l'informatique Physique](worksheet.md)
