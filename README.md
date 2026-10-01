# Internship Project
Transcription of a MAX Patch to PureData

### About ###
The patch is from the piece *Ricercare*, composed by Jonathan Harvey in 1984. The patch has been adapted, optimized, and in some cases simplified: for example, I added the buffer section, but it doesn’t work: I just wanted to include this section for learning purposes and to stay true to the original patch. The concept of buffering is more complicated in PureData than in MAX, which explains the difficulties I encountered and why this section isn’t functional.

I added one module compared to the original patch: not only can you launch the patch along with the music, but you can also activate the computer’s microphone and play the patch’s effects.

Only numbers 0 through 5 work: numbers 6 through 8 (and part of section 5) involve buffers; consequently, they produce no sound, as I mentioned earlier.


### Description ###
This composition is divided into two parts:
- The first part (which I managed to reproduce faithfully from the original patch) consists of a trumpet sound that repeats four times—once per speaker—with a “delay” each time.
- The second part uses the buffer: it normally records the trumpet sound and plays it back at any desired moment. This principle is also combined with delays.

Below is a brief description of my patch. It is broken down according to the blocks in my patch.

 The first block is the control block. The value can range from 0 to 8, and each value corresponds to a different effect. To increase the value, press the spacebar or “z,” and to decrease it, I’ve assigned the “a” key. To reset to 0 and initialize the patch, I’ve chosen to use the Enter key, just like in the original patch (see the “pd init” block: you can tell when it’s pressed by the light green “bang” that lights up when the key is pressed). Here are the different effects of each value:
- 0: Initializes all values.
- 1: The patch sets the volume of all audio outputs to maximum; the delay also occurs.
- 2: Randomly varies the volume of each speaker rapidly.
- 3: Still randomly varies the volumes, but more slowly (controlled by an object named “line”).
- 4: Resets all volumes to their maximum.
- 5: Resets all volumes to 0 and starts recording.
- 6 + 7: Plays back the recorded sounds, with the delay.
- 8: Ends the piece, resets all values and volumes to 0.

The second block is dedicated to the tempo, as indicated on the block. You can adjust it using the orange horizontal slider. The initial tempo is 72, based on the original piece.

The “open 2nd” block refers to the second part of the piece: if you press the button, a window pops up showing the code for the buffers. However, as mentioned above, this configuration doesn’t work very well.

“Ambient sound” is a module I added myself: it simply lets you know whether a microphone is working or not. Even though the sound in question is a .wav file, I’ve added an option that lets you speak into a microphone (after first configuring the audio input to the computer’s microphone, for example) and apply the same effects as for the intended sound. This allowed me, while designing the patch, to verify whether the generated effects were working correctly.

“Pd sound,” on the other hand, lets you play the audio file using the green button; it also lets you control the overall volume of the audio and choose whether or not to apply gain, via the parameter “tp-niv-rec-db.”

Finally, the largest section displays the sound produced for each audio output, along with its assigned delay. It also shows the volume level (which you can see change if you’re set to value 2 or 3, for example) and a selector that indicates whether you’re in the program’s first, second, or third configuration. In fact, within the program itself, there are specific configurations, and so this selector was very helpful in letting me know where I was and in identifying any mistakes I might have made.






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
