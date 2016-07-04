# Pull up et Pull down les résistances

Quand une broche GPIO est en mode entrée et non connectée à 3,3 volts ou à la terre, la broche est dite **flottante**, ce qui signifie qu'elle n'a pas de tension fixe. Ce n'est pas très bon pour ce que vous voulez, puisque la broche va flotter au hasard entre `HIGH` et `LOW` . Vous devez savoir catégoriquement l'état de la broche . Vous avez donc besoin de fixer la tension à `HIGH` ou `LOW` , puis la faire varier **seulement** quand (dans le cas de ce guide) un bouton est pressé ou une paire de câble est reliée manuellement.


Cela peut être fait de deux façons :

- A pull up circuit

   Câblez la broche GPIO à 3,3 volts via une grande (10 kOhms) résistance de sorte qu'elle lise toujours `HIGH`. Ensuite, nous pouvons court-circuiter la broche à la masse en fermant le circuit de telle sorte que la broche lira `LOW`. 


  ![](images/pull_up.png)

- A pull down circuit

   Câblez la broche GPIO à la masse via une grande (10 kOhms) résistance de sorte qu'elle lise toujours `LOW` . Ensuite, vous pouvez court-circuiter la broche à 3,3 volts en fermant le circuit de sorte qu'elle lira `HIGH`. Lorsque le circuit est fermé, il y a un chemin de moindre résistance jusqu'à 3,3 volts, et donc la broche va lire `HIGH` .

  ![](images/pull_down.png)

Note : La résistance 1k kOhm R2 est là dans les deux circuits pour donner à la broche GPIO une protection de sécurité intégrée, au cas où nous aurions mis par erreur la broche en mode SORTIE.

### Analogie
Imaginez une porte donnant sur un champ qui a des charnières extrêmement lisses, le moindre choc, une douce brise ou l'atterrissage d'un insecte pourrait la déplacer. Vous ne savez jamais si la porte était ouverte ou fermée car elle pourrait constamment balancer doucement entre ces deux positions. Si vous deviez ajouter un ressort à la porte pour la maintenir fermée, la porte serait maintenue en place, sauf dans le cas d'une poussée délibérée qui pourrait l'ouvrir. Dans cette situation, la position de la porte représente la tension qui peut fluctuer, le ressort représente la résistance qui fixe la tension soit `HIGH` ou `LOW`.

Heureusement, la Raspberry Pi a tous les circuits ci-dessus intégrés. Il peut être utile d'imaginer que les deux résistances `R1` et`R2` des diagrammes ci-dessus sont à l'intérieur des circuits de la Raspberry Pi et ils peuvent être activés ou désactivés autant que nécessaire. Vous pouvez sélectionner un "pull up" ou un "pull down" dans votre code pour chaque broche GPIO.


### Circuit Pull up

Dans cet exemple, vous allez utiliser le pull up interne de la résistance pour que la GPIO 4 lise `HIGH` par défaut, alors vous allez la court-circuiter à la masse à l'aide des câbles de façon à ce qu'elle lise `LOW` quand on appuie sur le bouton ou lorsque les fils se touchent, en complétant le circuit .

1. Utilisez de câbles de connexion , connectez un bouton poussoir aux broches GPIO de la Raspberry Pi comme illustré ci-dessous. Prenez soin d'utiliser les bonnes broches. Si vous ne disposez pas de bouton-poussoir, vous pouvez utiliser deux câbles mâle / femelle afin de faire manuellement le contact entre la masse et la broche d'entrée.


  ![](images/pull_up_wire.png)

2. Ouvrez Idle3 dans le menu général.

![Open Idle3](images/open_idle.png)

3. Créez un nouveau programme en cliquant sur **File** -> **New Window**

4. Entrez le code ci-dessous.
  ```python
  import time
  import RPi.GPIO as GPIO
  GPIO.setmode(GPIO.BCM)
  GPIO.setwarnings(False)

  button = 4

  GPIO.setup(pin, GPIO.IN, GPIO.PUD_UP)

  while True:
      button_state = GPIO.input(button)
      if button_state == GPIO.HIGH:
        print ("HIGH")
      else:
        print ("LOW")
      time.sleep(0.5)
  ```

5. Enregistrez votre programme , en lui donnant un nom.

6. Lancez votre programme en appuyant sur la touche **F5**

7. Le texte `HIGH` devrait commencer à défiler en haut de l'écran. Lorsque vous appuyez sur le bouton (ou connectez les fils ensemble) pendant quelques secondes, vous verrez le texte `LOW` parce que vous êtes en train de court-circuiter la broche à la masse. Relâchez le bouton (ou déconnectez les fils) et il sera de retour à `HIGH` à cause de la résistance interne pull up.


  ![Pull Up Logic](images/pull_up_screenshot.png)

8. Appuyez sur `Ctrl - C` pour terminer votre script Python à tout moment.

### Pull down circuit

1. Retirez les câbles de démarrage des broches GPIO de la Raspberry Pi et rattachez-les comme indiqué dans le schéma ci-dessous. Prenez soin d'utiliser les bonnes broches.

  ![](images/pull_down_wire.png)

2. Le code nécessaire pour tester le cicuit pull down est presque identique à celui du pull up. Afin de gagner du temps, nous allons tout simplement faire une copie de votre fichier et changer une chose. Cliquez sur  **Fichier** et **Enregistrer sous** et donnez à votre programme un nouveau nom.

3. Trouvez la ligne `GPIO.setup` et changez le dernier paramètre : il faut passer de `GPIO.PUD_UP` à `GPIO.PUD_DOWN`. Ceci définit la résistance interne pull down sur la GPIO 4 de sorte qu'elle lise `LOW` sauf si elle est connectée à 3,3 Volts.

  `GPIO.setup(pin, GPIO.IN, GPIO.PUD_DOWN)`

4. Appuyez sur la touche **F5** pour exécuter votre nouveau programme.

5. Le texte `LOW` devrait commencer à défiler en haut de l'écran, lorsque vous appuyez sur le bouton (ou connectez les fils ensemble) pendant quelques secondes, vous verrez le texte `HIGH` parce que vous êtes en train de court-circuiter la broche à 3,3 volts. Relâchez le bouton (ou déconnectez les fils ) et il sera de retour à `LOW` à cause de la résistance interne pull dpwn.


  ![Pull Down Logic](images/pull_down_screenshot.png)

6. Appuyez sur `Ctrl - C` pour terminer votre script Python et revenir à la ligne de commande.

[Retour vers la feuille de travail](worksheet.md)
