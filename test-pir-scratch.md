# Tester un détecteur de mouvement (PIR) connecté à Scratch

1.  Une fois votre circuit LED complet, vous êtes maintenant prêt à utiliser Scratch pour détecter les mouvements. Lancez le programme ** Scratch ** en cliquant sur Menu ** ** puis ** Programmation ** et en sélectionnant ** Scratch ** .

Notre version de Scratch sur Raspbian est très spéciale. Elle vous permet d'accéder et de contrôler les broches GPIO.

2.  Cliquez sur Control sur l'écran en haut à gauche. Faites glisser le bloc ![Green Flag](images/green_flag.png) sur votre zone de scripts.

3. Faites glisser un bloc `broadcast` sur votre zone de scripts et attacher le au bloc ![Green Flag](images/green_flag.png). Cliquez dans le menu déroulant sur le bloc de diffusion et sélectionnez **new**.

    Dans le message nommé type de boîte `config4in` cette instruction indique à la Raspberry Pi de définir la broche GPIO 4 comme une entrée.

![Config Pin 4](images/scratch_config4.png)

4. Cliquez sur le drapeau vert dans le coin supérieur droit de la fenêtre de Scratch. Cela exécute l'instruction pour définir la broche GPIO 4 comme entrée.

5. Scratch utilise des blocs de « détection » pour vérifier s'il y a une entrée sur les broches GPIO. S'il y a une entrée, la valeur de la broche passe de `0` to `1`. Comme vous avez connecté le capteur PIR à la broche GPIO 4 de la Pi, nous devons surveiller cela. Cliquez sur le menu déroulant sur le bloc `valeur du capteur` et choisissez `gpio4`.

6. Cochez la case à gauche du bloc pour afficher la valeur de la broche à l'écran.

  ![Scratch sensing blocks](images/sensing-blocks.png)

7. Testez le capteur PIR en agitant votre main en face de lui. Quand il détecte un mouvement, la valeur sur l'écran doit passer de `0` to `1`.

8. Si la valeur ne change pas, vérifiez que les bonnes broches soient connectées.

Retour vers [Commencer avec l'informatique Physique](worksheet.md)
