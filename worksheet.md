# Commencer avec l'Informatique Physique avec la Raspberry Pi

Une caractéristique puissante de la Raspberry Pi est la rangée de broches GPIO le long du bord supérieur de la carte. Les GPIO représentent les entrées et sorties universelles. Ces broches sont une interface physique entre Pi et le monde extérieur. De manière simplifiée, vous pouvez les comparer à des interrupteurs que vous pouvez allumer ou éteindre (entrée) ou que le Pi peut allumer ou éteindre (sortie).

Les broches GPIO sont un moyen avec lequel le Raspberry Pi peut contrôler et surveiller le monde extérieur en étant connecté à des circuits électroniques. Le Pi est capable de contrôler des LED, les allumer ou les éteindre, contrôler des moteurs ou bien d'autres éléments. Il est aussi capable de détecter si un interrupteur a été activé ou détecter la température, la lumière. Nous appelons cela l'informatique physique.

## GPIO
Les modèles A +, B +, et Pi 2 ont 40 broches qui ressemblent à ceci :

![GPIO pins](images/gpio-pins-pi2.jpg)

Ces broches sont une interface physique entre la Pi et le monde extérieur. De manière très simple, vous pouvez penser à elles comme des interrupteurs que vous pouvez activer ou désactiver (entrée) ou que la Pi peut activer ou désactiver (sortie). Sur les 40 broches, 26 sont des broches GPIO et les autres correpondent aux sources d'alimentation ou à la masse (plus deux broches ID EEPROM, auxquelles vous ne devriez pas toucher, sauf si vous êtes expert en la matière).

![GPIO layout](images/gpio-numbers-pi2.png)

Les modèles A et B ont seulement 26 broches et ressemblent à ceci :

![](images/gpio-pins.jpg)

A noter que la numérotation des broches GPIO est assez inhabituelle. Elle est expliquée dans la section ci-dessous.

## À quoi servent-elles ? Que puis-je faire avec ?

Vous pouvez programmer les broches pour interagir de manière incroyable avec le monde réel. Les entrées ne doivent pas provenir d'un interrupteur physique; cela peut être un capteur ou un signal provenant d'un autre ordinateur ou de périphériques, par exemple. La sortie peut aussi faire de nombreuses choses : allumer une LED, envoyer un signal ou bien des données vers un autre appareil. Si le Raspberry Pi est sur un réseau, vous pouvez contrôler des périphériques qui y sont associés de presque partout et ces appareils peuvent envoyer des données en retour. La connectivité et le contrôle des périphériques physiques sur Internet est une chose puissante et excitante, et le Raspberry Pi est idéal pour cela. Il y a beaucoup d'exemples brillants à propos de l'informatique physique sur [our blog](http://www.raspberrypi.org/blog/).

## Comment les broches GPIO fonctionnent ?

### Sorties

**Attention**: Si vous suivez les instructions, alors bricoler avec les GPIO sera sûr et amusant. Brancher aléatoirement des câbles et des sources d'alimentation sur votre Pi peut l'endommager ou la casser. Des effets néfastes peuvent également se produire si vous essayez de connecter les choses qui utilisent beaucoup de puissance à votre Pi ; Les LED sont très bien, les moteurs ne le sont pas. Si vous êtes inquiet à ce sujet, alors vous devriez envisager d'utiliser une carte supplémentaire comme la [Explorer HAT](https://shop.pimoroni.com/products/explorer-hat) jusqu'à ce que vous soyez assez confiant pour utiliser les GPIO directement.

Ignorez la Pi un moment, l'un des plus simples circuits électriques que vous pouvez construire contient une pile (batterie) reliée à une source de lumière et un interrupteur (la résistance est là pour protéger la LED) :

![Simple circuit](images/simple-circuit.png)

Lorsque nous utilisons une broche GPIO comme sortie, la Raspberry Pi remplace **à la fois l'interrupteur et la batterie** dans le diagramme ci-dessus. Chaque broche peut activer ou désactiver, ou `HIGH` (être allumé) ou `LOW` (être éteint) dans les termes informatiques. Lorsque la broche est ` HIGH`, il produit 3,3 volts ( 3V3 ) ; lorsque la broche est ` LOW`, il est éteint.

Voici le même circuit en utilisant le Raspberry Pi. La LED est reliée à une broche GPIO (qui peut produire 3.3 V) et une broche de terre (qui correspond à 0 V et agit comme la borne négative de la batterie) :

![GPIO wth LED](images/gpio-led-pi2.png)

L'étape suivante consiste à écrire un programme pour dire à la broche de fonctionner plus fortement ou plus légèrement (`HIGH` or `LOW`). Voici un exemple utilisant [Python](test-led-python.md), et voici comment le faire dans [Scratch](test-led-scratch.md)..

### Entrées

Les **sorties** GPIO sont faciles ; elles sont allumées ou éteintes, HIGH or LOW, 3.3 V ou 0 V. Les **Entrées** sont un peu plus complexes à cause de la façon dont les appareils numériques fonctionnent. Bien qu'il puisse sembler simple de juste connecter un bouton à travers une broche d'entrée et une broche de masse, la Pi peut confondre quant à savoir si le bouton est activé ou désactivé. Il pourrait fonctionner correctement, ou pas. C'est un peu comme flotter dans un espace profond ; sans référence, il serait difficile de dire si vous allumez ou si vous éteignez, ou même de savoir ce que signifie allumer ou éteindre !

C'est la raison pour laquelle vous verrez des phrases comme "remonter" (pull up) and "descendre" (pull down) dans les tutoriels concernant les GPIO Raspberry Pi. C'est une façon de donner à la broche d'entrée une référence de sorte qu'il sache avec certitude quand une entrée est reçue.


## La numérotation des broches GPIO

Lors de la programmation des broches GPIO, il y a deux façons de se référer à elles : numérotation GPIO et numérotation physique.

### La numérotation GPIO

Ce sont les broches GPIO telles que l'ordinateur les voit. Les chiffres n'ont pas de sens pour les humains, ils défilent partout, donc il n'y a aucun moyen de s'en rappeler. Cependant, vous pouvez utiliser une référence imprimée ou une carte de référence qui se place sur les broches pour vous aider.

![GPIO layout](images/gpio-numbers-pi2.png)

### La numérotation physique

L'autre façon de se référer aux broches est en comptant simplement "across and down" à partir de la broche 1 en haut à gauche (la plus proche de la carte SD) . C'est la « numérotation physique» et ça ressemble à ceci :

![GPIO layout](images/physical-pin-numbers.png)

### Quel système dois-je utiliser ?

Les débutants et les jeunes enfants peuvent trouver le système de numérotation physique plus simple : vous comptez simplement les broches. Vous aurez toujours besoin d'un schéma comme celui ci-dessus pour savoir quelles sont les broches GPIO, quelles sont celles qui sont à la masse , qui ont de la puissance.

En général, nous vous recommandons d'utiliser la numérotation GPIO. C'est une bonne pratique et la plupart des ressources utilisent ce système. Faites votre choix  : tant que vous utilisez le même système dans un programme, tout ira bien. Notez que la numérotation des broches peut aussi dépendre du langage de programmation que vous utilisez.


Pour plus de détails sur les fonctionnalités des broches GPIO, allez voir : [interactive pinout diagram](http://pi.gadgetoid.com/pinout).

### Pull up et Pull down les résistances

Quand une broche GPIO est en mode entrée et non connectée à 3,3 volts ou à la terre, la broche est dite **flottante**, ce qui signifie qu'elle n'a pas de tension fixe. Ce n'est pas très bon pour ce que vous voulez, puisque la broche va flotter au hasard entre `HIGH` et `LOW` . Nous devons savoir catégoriquement l'état de la broche. Nous avons donc besoin de fixer la tension à `HIGH` ou `LOW`, puis la faire varier seulement lorsque l'on fait toucher les fils ensemble. Vous pouvez en apprendre plus sur "pull up and pull down" des résistances dans [ce guide](pull_up_down.md).

# Composants

## Qu'est ce qu'une carte de prototypage ?

Vous pouvez penser à une carte de prototypage comme étant la toile d'un artiste, mais sans qu'aucune création sur la toile ne soit permanente. Bien qu'il soit possible de faire un circuit sans carte de prototypage (breadboard), elle permet d'organiser les composants plutôt que d'avoir pleins de fils en désordre sans indication claire de la façon dont chaque fil est relié les uns aux autres. Deuxièmement, si vous deviez réaliser un circuit et le dessiner pour l'adapter sur un PCB, un breadboard vous permet d'organiser des composants logiquement avant de faire la conception permanente.


![](images/breadboard.png)

Du point de vue de l'électronique, des lignes horizontales de trous sont reliées entre elles à l'intérieur du breadboard par des liaisons métalliques, avec à l'intérieur des composants, des trous sur chaque connexion.

Sur les côtés de la carte de prototypage, il y a des rails d'alimentation et de masse - ceux-ci se connectent verticalement au lieu d'horizontalement, et sont utilisés pour ranger les circuits en étant un point d'union pour toutes les connexions électriques. C'est également plus sûr de cette façon, que toute la puissance peut être déconnectée des composants en tirant la connexion de la source d'alimentation à ces rails, plutôt que de tirer la liaison de chaque composant nécessitant de la puissance.

Le nom breadboard provient du fait que les ingénieurs dans le passé voulaient prototyper des circuits sur des bouts de bois. 

![Early Breadboard](images/early_breadboard.jpg)

## Qu'est-ce qu'une résistance ?

Les résistances sont un moyen de limiter la quantité d'électricité qui passe dans un circuit ; plus précisément, ils limitent la quantité de **courant** qui est autorisée à circuler. La mesure de la résistance est **ohms (Ω)**, et plus la valeur de la résistance est élevée, plus on limite le courant.

![](images/resistor-330r.png)

La valeur d'une résistance est marquée par des bandes de couleur le long du corps de résistance. Une résistance, communément utilisée dans des projets avec des LEDs, a une valeur de résistance de 330 Ω. Vous pouvez identifier les résistances de 330 Ω par les bandes de couleur le long du corps. Le codage couleur dépendra de combien de bandes sont sur les résistances : s'il y a quatre bandes de couleur, elles seront orange, orange, marron et or. S'il y a cinq bandes, les couleurs seront orange, orange, noir, noir, marron.

Vous devez utiliser des résistances pour connecter les LED sur les broches GPIO de la Raspberry Pi. La Raspberry Pi ne peut fournir qu'un courant faible (environ 60mA). Les LEDs veulent tirer plus, et si on les laisse faire, elles brûleront la Raspberry Pi. Par conséquent, mettre les résistances dans un circuit fera en sorte que seulement un petit courant circule et que la Pi ne sera pas endommagée. Le sens de connexion des résistaces importent peu. Le courant circule dans les deux sens à travers elles.

## Qu'est ce qu'une LED?

![](images/led.png)

LED signifie diode électroluminescente (Light Emitting Diode). Une LED brille quand du courant électrique passe à travers elle. Lorsque vous décrochez le LED, vous remarquerez qu'une branche est plus longue que l'autre. La plus grande branche (connue sous le nom de l'anode) est toujours connectée à la borne + positive du circuit. La branche la plus courte (appelée la cathode) est connectée au côté négatif de l'alimentation électrique : la masse ou la terre. Les LED ne fonctionnent que si l'alimentation est fournie dans le bon sens (à savoir si la polarité est correcte). Vous ne casserez pas les LEDs si vous les connectez dans le mauvais sens, mais elles ne brilleront pas.

### Pourquoi la LED brille ?

Quand un circuit est branché sur les broches GPIO de la Raspberry Pi, l'électricité circule à travers le circuit. Le flux est appelé le courant. La LED est allumée uniquement lorsque le courant électrique circule de la longue branche à travers l'ampoule jusqu'à la branche courte. La résistance diminue la quantité de courant électrique passant à travers le circuit. Ceci protège la LED de la casse.


- [Connecter une LED sans breadboard](connect-led.md)
- [Connecter une LED avec breadboard](connect-leds.md)
- [Tester une LED connectée sur Python](test-led-python.md)
- [Tester une LED connectée sur Scratch](test-led-scratch.md)

## Qu'est ce qu'un bouton poussoir ?
Un bouton poussoir fermera un circuit lorsque le bouton est enfoncé. Cela signifie que le courant circule à travers le circuit seulement lorsqu'on appuie sur le bouton. Quand il est libéré, le circuit sera « ouvert ».

![](images/tactile-push-button.png)

## Qu'est-ce qu'un câble de connexion ?

Les câbles de connexion sont utilisés sur breadboards pour passer d'une connexion à un autre . Généralement, les câbles de connexion disposent de connecteurs différents à chaque extrémité. Il existe trois types de câbles de connexion :


| | | |
|:-------|---|:---|
| **Mâle / Mâle** | ![](images/jumper-male-to-male.png) | Les deux extrémités ont une « broche » qui peut être utilisée sur une carte de prototypage. |
| **Mâle / femelle** | ![](images/jumper-male-to-female.png) | L'extrémité avec la « broche » ira sur une carte de prototypage.  L'extrémité avec le morceau de plastique avec un trou ira sur les broches GPIO de la Raspberry Pi. |
| **Femelle / femelle** | ![](images/jumper-female-to-female.png) | Les deux extrémités ont un morceau de plastique avec un trou dedans et peuvent être utilisés avec des broches GPIO et des composants Raspberry Pi.  |

Nous utilisons des câbles de liaison pour relier les broches GPIO sur la Raspberry Pi et les cartes de prototypage. C'est vraiment un moyen simple et rapide pour commencer à faire des circuits simples.


## Qu'est-ce qu'un détecteur de mouvement PIR ?

**PIR** signifie **infrarouge passif**. C'est un type de capteur que'on trouve souvent dans les coins des pièces pour les systèmes d'alarme antivol. Tous les objets dont les températures sont au-dessus du zéro absolu émettent un rayonnement infrarouge. Les longueurs d'onde infrarouges ne sont pas visibles pour l'oeil humain, mais elles peuvent être détectées par le système électronique à l'intérieur de l'un de ces modules.

Le capteur est considéré comme passif, car il n'envoie pas de signal pour détecter le mouvement. Il se règle à la signature infrarouge de la pièce dans laquelle il est et ensuite il montre tout changement. Tout objet se déplaçant à travers la pièce va perturber la signature infrarouge et provoquer un changement qui sera remarquée par le module PIR .


![](images/pir_module.png)

Il ne faut pas se soucier de son fonctionnement interne. Ce qui nous intéressent sont les trois axes sur elle ; nous pouvons les connecter aux broches GPIO de la Raspberry Pi. Une broche est pour +5 volts, une broche est pour la mase et l'autre est la broche du capteur (la broche centrale sur notre Pi). Cette broche de capteur est alimentée chaque fois que le mouvement est détecté par le module PIR. On peut alors voir que cela se produit sur la Raspberry Pi et créer des actions en conséquence.


- [Connecter un détecteur de mouvement PIR](connect-pir.md)
- [Tester un détecteur de mouvement PIR avec Python](test-pir-python.md)
- [Tester un détecteur de mouvement PIR avec Scratch](test-pir-scratch.md)

## Quoi d'autre ?

### Le début de quelque chose d'étonnant

Nous espérons que cela vous a encouragé à vous lancer dans l'informatique physique à l'aide de la GPIO Pi; ce n'est vraiment pas aussi difficile que ça n'y paraît. Tout commence avec une LED simple, mais cela peut vous emmener dans des endroits incroyables. Ne sous-estimez pas le plaisir pris, la créativité et le sens de la réalisation que vous pouvez obtenir à partir d'un petit ordinateur et un tas d'épingles. Amusez-vous ! Et si vous faites quelque chose de cool, s'il vous plaît, partagez-le.

- Pourquoi ne pas utiliser vos nouvelles connaissances sur l'informatique physique pour compléter une nouvelles [ressources](https://www.raspberrypi.org/resources/make/)?
