# Projet-de-stage-ouvrier
Transcription d'un patch MAX vers PureData

### A propos ###
Le patch provient de la pièce Ricercare, créé par Jonathan Harvey en 1984. Le patch est réadapté, optimisé, et parfois simplifié : en effet, j'y ai ajouté, par exemple, la partie buffer, mais elle ne fonctionne pas : je voulais juste ajouter cette partie par apprentissage, et par fidélité du patch en question. La notion de buffer est plus compliquée sur PureData que sur MAX, d'où mes difficultés rencontrées, et une non fonctionnalité de cette partie. 

J'y ai ajouté un module par rapport au patch initial: on peut non seulement lancer la patch avec la musique, mais aussi activer le micro de l'ordinateur, et jouer les effets du patch. 

Seuls les numéros de 0 à 5 fonctionnent : en effet, les numéros de 6 à 8 (et une partie de la 5e partie) concernent les buffers: subséquemment ils ne produisent rien, d'après mes propos précédents.


### Description ###
Cette composition est découpée en 2 parties : 
- La première partie (celle que j’ai réussi à reproduire fidèlement au patch initial) constitue à un son d’une trompette, qui se répète 4 fois, une fois par enceinte, avec un “delay” à chaque fois. 
- La seconde partie est avec le buffer : il enregistre normalement le son de la trompette, et le restitue à n’importe quel moment désiré. Ce principe est combiné aussi avec les délais.

Vous trouverez par la suite une brève description de mon patch. Elle est décomposée selon les blocs de mon patch.

 Le premier bloc est le bloc de contrôle. La valeur peut aller de 0 à 8, et chaque valeur correspond à un effet différent. pour augmenter la valeur, on appuie sur espace ou “z”, et pour décrémenter, j’ai choisi la touche “a”. Pour remettre à 0 et pour initialiser le patch, j’ai choisi d’utiliser la touche entrée, fidèlement au patch initial (cf au bloc “pd init”: on peut voir quand on appuie dessus grâce au “bang” vert clair qui s’acitve lorsque l’on appuie sur la touche en question). Voici les différents effets des valeurs : 
- 0: Initialisation des valeurs.
- 1: Le patch met au maximum tous les volumes de toutes les sorties audio; le délai se produit aussi.
- 2: Fait varier aléatoirement le volume de chaque enceinte rapidement.
- 3: Fait toujours varier aléatoirement les volumes, mais plus lentement (géré par un objet nommé line).
- 4: Remet tous les volumes à leur maximum.
- 5: Remise à 0 de tous les volumes et début de l’enregistrement.
- 6 + 7: restitution des sons enregistrés, avec le délai.
- 8: Fin de la pièce, remise à 0 de toutes les valeurs et des volumes.

Le second bloc est dédié au tempo, comme écrit sur le bloc. On peut le faire varier à l’aide de la barre horizontale orangée. Le tempo initial est de 72 selon la pièce d’origine.

Le bloc “open 2nd” fait référence à la seconde partie de la pièce: si on appuie sur le bouton, une fenêtre apparaît, et montre le code pour les buffers. Néanmoins, comme évoqué ci-dessus, cette configuration ne fonctionne guère correctement.

“Ambient sound” est un module que j’ai ajouté personnellement : il permet simplement de savoir si un micro fonctionne ou non. Même si le son en question est un fichier .wav, j’ai toutefois ajouté une option qui permet de parler dans un micro (en configurant préalablement l’entrée audio au micro de l’ordinateur par exemple), et d’avoir les effets comme pour le son prévu normalement. Cela me permettait, durant la conception du patch, de savoir si les effets produits fonctionnaient correctement.

“Pd sound”, quant à lui, permet de lancer le fichier audio à l’aide du bouton vert; il permet aussi de gérer le volume général du son audio, et aussi d’ajouter un gain ou non, se nommant “tp-niv-rec-db”.

Enfin, le plus gros bloc affiche le son produit pour chaque sortie audio, avec son délai attribué. On y voit aussi le volume sonore (que l’on peut voir varier si on est à la valeur 2 ou 3 par exemple) et un sélecteur, qui montre si l’on est dans la première, seconde ou troisième configuration du programme. En effet, au sein même du programme, il y a des configurations spécifiques, et ainsi, ce sélecteur m’a beaucoup aidé pour voir où j’en étais, et pour déterminer certaines fautes que j’aurai pu commettre. 
