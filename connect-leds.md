# Connecter et commander une LED avec un Breadboard

Dans ce circuit, vous allez connecter votre Raspberry Pi à un breadboard afin de vous permettre de brancher plusieurs LEDs.

L'utilisation d'un breadboard vous permet de connecter des composants électroniques les uns aux autres sans avoir à les souder ensemble. Ils sont souvent utilisés pour tester un circuit avant de créer une carte de circuit imprimé (PCB). Les trous sur la carte de test sont connectés selon une configuration. Sur la platine de prototypage (breadboard) du "CamJam EduKit", les trous de la colonne gauche (marquée par une ligne rouge) sont tous reliés entre eux, c'est la partie "conducteur". Les trous de la deuxième colonne (marquée par une ligne bleue) sont également reliés entre eux ; nous appelons cela la "masse". Il existe une autre paire de "côté conducteur / masse" de l'autre côté de la platine de prototypage. Au milieu, les trous sont reliés entre eux dans des rangées de 5 avec une coupure au milieu.

1. Prenez un câble de connexion mâle / femelle et connectez l'extrémité femelle à une broche GPIO correspondant à la masse sur le Raspberry Pi. Enfoncez l'autre extrémité du câble de connexion dans un trou sur le rail de la masse de la platine de prototypage comme ceci:

    ![](images/gpio-connect-ground.png)

2. Maintenant, prenez une LED rouge et jetez-y un coup d'oeil. Notez qu'une branche est plus longue que l'autre.

3. Enfoncez la branche longue de la LED dans un trou sur la colonne « E » de la platine de prototypage, par exemple E3 et la jambe la plus courte dans un trou à côté de lui sur la même colonne, par exemple E2 , comme ceci:

    ![](images/gpio-connect-red-led.png)

4. Trouvez une résistance de 330 Ohms et connectez une branche dans un trou du rail de la masse et l'autre branche dans un trou (de la platine de prototypage) de la même ligne que la branche la plus courte de la LED, par exemple A2. Le sens de la résistance n'a pas d'importance. Vous aurez besoin de plier les branches de la résistance à monter, mais assurez-vous que les fils de chaque jambe ne se croisent pas.


    ![](images/gpio-connect-resistor.png)

5. Maintenant, vous devez compléter le circuit afin que le courant puisse circuler dans le Raspberry Pi et allumer la LED. Pour ce faire, vous allez utiliser un autre câble de connexion.

Prenez un câble de connexion mâle / femelle et connectez l'extrémité femelle à la broche `GPIO 17` de votre Raspberry Pi. Puis, enfoncez l'extrémité mâle du câble dans un trou sur la platine de prototypage, qui est alignée avec la branche la plus longue de la LED, par exemple A3.

    ![](images/gpio-complete-circuit.png)

6. Maintenant que vous avez connecté votre première LED, vous pouvez en ajouter davantage à l'aide d'autres résistances, câbles de connexion et LED. Dans l'exemple ci-dessous, trois LED ont été connectées en utilisant des broches 18, 7, 20.


  ![](images/gpio-complete-circuit2.png)

[Retour vers "Commencer avec l'informatique Physique"](worksheet.md)
