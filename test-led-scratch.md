# Tester une LED connectée à Scratch

1.  Une fois votre circuit LED complet, vous êtes maintenant prêt à utiliser Scratch pour allumer la LED. Lancez le programme ** Scratch ** en cliquant sur Menu ** ** puis ** Programmation ** et en sélectionnant ** Scratch ** .

 ![](images/scratch-icon.png)

 Notre version de Scratch sur Raspbian est très spéciale. Elle vous permet d'accéder et de contrôler les broches GPIO.

    ![](images/Scratch-interface.png "The Scratch Interface")

2.  Cliquez sur **Control** sur l'écran en haut à gauche . Faites glisser le bloc ![Green Flag](images/green_flag.png) sur la zone de scripts.

3. Faites glisser un bloc `broadcast` sur votre zone de scripts et attacher le au bloc ![Green Flag](images/green_flag.png). Cliquez dans le menu déroulant sur le bloc de diffusion et sélectionnez **nouveau**.
    
Dans le message nommé type de boîte `gpioserveron`, cette instruction indique à Scratch d'activer ses fonctions GPIO.

4. Faites glisser un autre bloc `broadcast` sur votre zone de scripts et attachez le en bas. Cliquez dans le menu déroulant sur le bloc de diffusion et sélectionnez **nouveau**.

    Dans le message nommé type de boîte `config17output`, cette instruction indique à la Raspberry Pi de définir la broche GPIO 17 en tant que sortie.

    ![](images/scratch_config.png)

5. Faites glisser un autre bloc `broadcast` sur votre zone de scripts et attachez le en bas du premier bloc de diffusion. Cliquez dans le menu déroulant sur le bloc de diffusion et sélectionnez **nouveau**.

    Dans le message nommé type de boîte `gpio17on`, cette instruction indique à la Raspberry Pi de régler la broche GPIO 17 à `HIGH`.

6. Faites glisser un bloc `wait 1 secs` sur votre zone de scripts et reliez le au bloc de diffusion précédent.

7. Faites glisser un dernier bloc `broadcast` sur votre zone de scripts et reliez le au bloc `wait 1 secs`. Cliquez dans le menu déroulant sur le bloc de diffusion et sélectionnez **nouveau**.

    Dans le message nommé type de boîte `gpio17off`, cela éteindra la LED.

8. Enregistrez votre travail jusqu'à présent en cliquant sur **File** puis **Save As**. Nommez votre fichier `Test LED` et cliquez sur **OK**.

9. Testez votre programme en cliquant sur l'icône ![Green Flag](images/green_flag_icon.png). Vous devriez voir la LED s'allumer pendant 1 seconde, puis éteindre.

    ![](images/scratch_complete.png)

Retour vers [Commencer avec l'informatique Physique](worksheet.md)
