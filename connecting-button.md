# Connecter un bouton poussoir

Un bouton poussoir fermera un circuit lorsque le bouton sera pressé. Cela signifie que le courant ne circule pas tant que le bouton n'est pas enfoncé. Quand il est libéré, le circuit est ouvert.

Tout d'abord, jetez un oeil sur le schéma GPIO suivant. Vous utiliserez une seule broche de terre (marqué `GND`) et plusieurs broches GPIO (marqué `GPIO`) :


|            |            |
|-----------:|:-----------|
|    3V3     | 5V         |
|  **GPIO2** | 5V         |
|  **GPIO3** | GND        |
|  **GPIO4** | **GPIO14** |
|        GND | **GPIO15** |
| **GPIO17** | **GPIO18** |
| **GPIO27** | GND        |
| **GPIO22** | **GPIO23** |
|        3V3 | **GPIO24** |
| **GPIO10** | GND        |
|  **GPIO9** | **GPIO25** |
| **GPIO11** | **GPIO8**  |
|        GND | **GPIO7**  |
|        DNC | DNC        |
|  **GPIO5** | GND        |
|  **GPIO6** | **GPIO12** |
| **GPIO13** | GND        |
| **GPIO19** | **GPIO16** |
| **GPIO26** | **GPIO20** |
|        GND | **GPIO21** |

Notez que si vous avez un modèle Raspberry Pi plus ancien, vous aurez seulement 26 broches, mais elles ont la même disposition, à partir de la rangée supérieure (`3V3` et `5V`) et se terminant par (`GND` et `GPIO7`).
    
1. Trouver une broche de masse (marquée ` GND`) sur le schéma ci-dessus.

2. Fixer un câble à une broche de terre du Raspberry Pi et branchez-le sur le rail de la masse de la platine de prototypage (breadboard) comme ceci:

    ![](images/gpio-connect-ground.png)

3. Placez le bouton poussoir sur la platine de prototypage et connectez l'un de ses pieds sur le rail de la terre.

4. Connectez l'autre pied du bouton poussoir (du même côté) à la broche GPIO 2 comme ceci:

    ![](images/gpio-connect-button.png)
    
Si vous utilisez une mini platine de prototypage sans rail de masse désigné, vous devrez utiliser une des lignes comme un rail de masse. Définissez une rangée de broches de terre et les autres points de cette rangée seront reliés à la terre comme ceci :

    ![](images/gpio-connect-ground-mini.png)

[Retour vers "Commencer avec l'informatique Physique"](worksheet.md)
