# Une introduction aux GPIO et à l'informatique physique avec la Raspberry Pi

Une caractéristique puissante de la Raspberry Pi est la rangée de broches GPIO (entrée / sortie universelle) le long du bord supérieur de la carte. Les modèles A +, B +, et Pi 2 ont 40 broches qui ressemblent à ceci :

![GPIO pins](images/gpio-pins-pi2.jpg)

Ces broches sont une interface physique entre la Pi et le monde extérieur. De manière très simple, vous pouvez penser à elles comme des interrupteurs que vous pouvez activer ou désactiver (entrée) ou que la Pi peut activer ou désactiver (sortie). Sur les 40 broches, 26 sont des broches GPIO et les autres correpondent aux sources d'alimentation ou à la masse (plus deux broches ID EEPROM, auxquelles vous ne devriez pas toucher, sauf si vous êtes expert en la matière).

![GPIO layout](images/gpio-numbers-pi2.png)

Les modèles A et B ont seulement 26 broches et ressemblent à ceci :

![](images/gpio-pins.jpg)

A noter que la numérotation des broches GPIO est assez inhabituelle. Elle est expliquée dans la section correspondante (la numérotation des broches).

## À quoi servent-elles ? Que puis-je faire avec ?

Vous pouvez programmer les broches d'pour interagir de manière incroyable avec le monde réel. Les entrées ne doivent pas provenir d'un interrupteur physique; cela peut être un capteur ou un signal provenant d'un autre ordinateur ou de périphériques, par exemple. La sortie peut aussi faire de nombreuses choses : allumer une LED, envoyer un signal ou bien des données vers un autre appareil. Si le Raspberry Pi est sur un réseau, vous pouvez contrôler des périphériques qui y sont associés de presque partout et ces appareils peuvent envoyer des données en retour. La connectivité et le contrôle des périphériques physiques sur Internet est une chose puissante et excitante, et le Raspberry Pi est idéal pour cela. Il y a beaucoup d'exemples brillants à propos de l'informatique physique sur [notre blog] (http://www.raspberrypi.org/blog/).


## Comment les broches GPIO fonctionnent ?

### Sorties

** ATTENTION ** : Si vous suivez les instructions, alors bricoler avec les GPIO sera sûr et amusant. Brancher aléatoirement des câbles et des sources d'alimentation sur votre Pi peut l'endommager ou la casser. Des effets néfastes peuvent également se produire si vous essayez de connecter les choses qui utilisent beaucoup de puissance à votre Pi ; Les LED sont très bien, les moteurs ne le sont pas. Si vous êtes inquiet à ce sujet, alors vous devriez envisager d'utiliser un circuit imprimé comme la [Pibrella] ( http://pibrella.com/ ) jusqu'à ce que vous soyez assez confiant pour utiliser les GPIO directement.

Ignorant la Pi un moment, l'un des plus simples circuits électriques que vous pouvez construire contient une pile (batterie) reliée à une source de lumière et un interrupteur (la résistance est là pour protéger la LED) :

![Simple circuit](images/simple-circuit.png)

Lorsque nous utilisons une broche GPIO comme sortie, la Raspberry Pi remplace ** à la fois l'interrupteur et la batterie ** dans le diagramme ci-dessus. Chaque broche peut activer ou désactiver, ou `HIGH` (être allumé) ou `LOW` (être éteint) dans les termes informatiques. Lorsque la broche est ` HIGH` , il produit 3,3 volts ( 3c3 ) ; lorsque la broche est ` LOW` , il est éteint.

Voici le même circuit en utilisant le Raspberry Pi. La LED est reliée à une broche GPIO (qui peut produire 3.3 V) et une broche de terre (qui correspond à  0 V et agit comme la borne négative de la batterie) :

![GPIO wth LED](images/gpio-led-pi2.png)

L'étape suivante consiste à écrire un programme pour dire à la broche de fonctionner plus fortement ou plus légèrement. Voici un exemple utilisant [Python](http://www.raspberrypi.org/learning/quick-reaction-game/) (see Step 2), et voici comment le faire dans [Scratch](http://www.raspberrypi.org/learning/robot-antenna/).

### Entrées

Les ** sorties ** GPIOsont faciles ; elles sont allumées ou éteintes , HIGH or LOW, 3.3 V ou 0 V. Les ** Entrées ** sont un peu plus complexes à cause de la façon dont fonctionnent les appareils numériques. Bien qu'il puisse sembler simple de juste connecter un bouton à travers une broche d'entrée et une broche de masse, la Pi peut confondre quant à savoir si le bouton est activé ou désactivé. Il pourrait fonctionner correctement, ou pas. C'est est un peu comme flotter dans un espace profond ; sans référence, il serait difficile de dire si vous allumez ou si vous éteignez, ou même de savoir ce que signifie allumer ou éteindre !

Ceci est la raison pour laquelle vous verrez des phrases comme "remonter" (pull up) and "descendre" (pull down) dans les tutoriels concernant les GPIO Raspberry Pi. C'est une façon de donner à la broche d'entrée une référence de sorte qu'il sache avec certitude quand une entrée est reçue.


Si vous souhaitez de l'aide pour utiliser les GPIO comme des entrées, jetez un oeil à notre [burping jelly baby](https://www.raspberrypi.org/learning/burping-jelly-baby/) et [quick reaction game](http://www.raspberrypi.org/learning/quick-reaction-game/) tutoriels pour Python, ou une [reaction game](http://www.raspberrypi.org/learning/reaction-game/) pour Scratch.

## Le début de quelque chose d'étonnant

Nous espérons que cela vous a encouragé à vous lancer dans l'informatique physique à l'aide de la GPIO Pi; ce n'est vraiment pas aussi difficile que ça n'y paraît. Tout commence avec une LED simple, mais cela peut vous emmener dans des endroits incroyables. Ne sous-estimez pas le plaisir pris, la créativité et le sens de la réalisationque vous pouvez obtenir à partir d'un petit ordinateur et un tas d'épingles. Amusez-vous ! Et si vous faites quelque chose de cool, s'il vous plaît, partagez le.


Retur vers [Commencer avec l'informatique Physique](worksheet.md)
