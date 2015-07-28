# Programmes Démo

Raspbian est livré avec un ensemble de programs "démo" que vous pouvez facilement compiler et exécuter.  Ces programs partent d'un simple affichage de texte *hello world*, jusqu'à jouer de la vidéo "full HD" en 1080p, des théières tournants en 3D, et des motifs fractals, animés en temps réel. C'est une bonne façon d'apprécier ce dont le Pi est capable, et en même temps de pouvoir se familiariser avec la navigation du système et le lancement de programs en ligne de commande.

## Non, pas ça ! La ligne de commande !

Faire démarrer votre Raspberry Pi et vous allez vous trouver à l'invite de commande ci-dessous. Si vous avez paramétré votre Pi de charger automatiquement l'interface de bureau graphique, utilisez le bouton "démarrer" pour se déconnecter du bureau.

`pi@raspberrypi ~ $ _`

Le texte ci-dessus est l'invite de commande. Essayez de ne pas en avoir peur ! A CLI (l'interface en ligne de commande) est en réalité un moyen très rapide et efficace pour faire fonctionner un ordinateur.

Pour commencer, naviguez jusqu'au dossier `hello_pi`, là où toutes les démos sont stockées. Entrez la commande ci-dessous pour pouvoir y arriver. **ASTUCE**: Vous pouvez utiliser la touche `TAB` pour auto-completer les commandes tout en saissisant.

`cd /opt/vc/src/hello_pi`

L'invite de commande devrait ressembler à ceci. La partie bleu indique où vous vous trouvez dans le système de fichiers du Pi.

`pi@raspberrypi /opt/vc/src/hello_pi $ _`

Si vous entrez `ls` et vous appuyez sur `Entrée`, vous allez voir la liste des dossiers. Il y en a un chaque démo. Cependant, avant de pouvoir les éxecuter,  il faudrait les compiler d'abord. Ne vous inquitétez pas si vous ne comprenez pas pourquoi on a besoin de faire ça; l suffit de suivre les indications pour l'instant, et nous allons apprendre plus à ce sujet d'ici peu.

Il y a un petit script de l'interpréteur de commandes ("shell script") fourni dans le dossier `hello_pi` sous le nom `rebuild.sh`, ce qui va dérouler la compilation pour vous. Entrez la commande suivante pour le lancer. Ignorez le "blahblah" qui s'affiche pour l'instant !

`./rebuild.sh`

Beaucoup de texte va désormais défiler à l'écran, mais pour cet exercice vous pouvez l'ignorer. Il s'agit simplement de la sortie du compilateur pendant qu'il traite le code démo. Attendez le retour de l'invite de commande avant de pouvoir continuer.

Maintenant, nous sommes prêts à lancer des démos.

## Hello world

D'abord, nous allons faire un test rapide afin de s'assurer que l'étape précédente de compilation s'est déroulé avec succès. Ce programme, pas super intéressant, va simplement afficher le texte `Hello world!`, mais si ça fonctionne correctement on sait que toutes les autres démos sont à priori opérationnelles aussi.

Entrez les commandes suivantes pour descendre dans le dossier `hello_world` et afficher la liste des fichiers.

```
cd hello_world
ls
```

Vous pouvez remarquer que le fichier `.bin` est affiché en vert. C'est parce qu'il s'agit d'un fichier éxecutable. Ca veu dire que c'est le fichier que l'on utilise pour lancer le programme.

Utilisez la commande suivante pour éxecuter la démo. Vous avez besoin du `./` pour spécifier le dossier actuel, sinon tous les dossiers du système Linux vont être scrutés pour le nom du fichier que vous avez entré.

`./hello_world.bin`

## Hello vidéo

Ceci va jouer un clip vidéo de 15s en "Full HD" 1080p sans le son. L'objectif est de montrer les capactiés de décodage et lecture de vidéo. Vous allez voir comme c'est fluide !

![image](images/bbb.jpg "Big Buck Bunny")

Entrez les commandes suivantes afin de naviguer jusqu'au dossier `hello_video` et lister son contenu.

```
cd ..
cd hello_video
ls
```

Vous pouvez remarquer le fichier `.bin` de nouveau. On doit indiquer à cette démo le clip vidéo à lire au moment de l'éxection, donc ça doit être le fichier `test.h264` (h264 est un type de codec vidéo).

Vous aurez besoin du `./` pour spécifier le répertoire actuel de nouveau.

`./hello_video.bin test.h264`

## Hello triangle

Ceci affiche un cube qui tourne avec des images differentes sur chaque face. L'objectif est de montrer le rendement en Open GL ES (une bibliothèque de programmation open-source pour des graphiques en 3D).

Entrez la commande suivante pour naviguer jusqu'au dossier `hello_triangle` et lister le son contenu.

```
cd ..
cd hello_triangle
ls
```

Vous allez voir de nouveau qu'un des fichiers est affiché en vert. Celui-ci est le fichier exéctutable. Cette démo n'a pas besoin d'entrer un fichier vidéo comme dans l'exemple précédent, donc vous pouvez simplement lancer le fichier `.bin`.

`./hello_triangle.bin`

Cette démo continuera à tourner tant que vous n'aurez pas dit d'arreter. Pour quitter la démo appuyez sur `Ctrl – C`.

## Hello triangle 2

Celui-ci affiche deux motifs factals super-imposés, l'un sur l'autre. Vous pouvez bouger la souris afin de changer la forme de fractale en temps réel. L'objectif est également de montrer le rendement en Open GL ES. Certains parmi vous peuvent reconnaître la fractale Mandelbrot.

![image](images/mandelbrot.jpg "Mandelbrot")

```
cd ..
cd hello_triangle2
ls
```

A noter le fichier en vert `.bin` ? Ok, lancez-le !

`./hello_triangle2.bin`

Maintenant fait bouger la souris, et vous allez voir la fractale se transformer. Voir si vous pouvez la transformer en cercle parfait. C'est un challenge, mais c'est possible. Pour quitter la démo appuyez sur `Ctrl – C`.

## Hello théière

Ceci affiche un théière qui tourne avec la texture du clip vidéo de `hello_video` mappée sur sa surface. Impressionnant ! Peut-être vous reconnaissez le modèle théière si vous connaissez déjà un logiciel qui s'appelle Blender. Ceci montre le rendement Open GL ES ainsi que le décodage/lecture vidéo en simultané.

![image](images/teapot.jpg "Tea Pot")

```
cd ..
cd hello_teapot
ls
```

A noter le fichier en vert `.bin` ? Ok, lancez-le !

`./hello_teapot.bin`

C'est possible que vous recevez l'erreur suivante quand vous essayez de lancer cette démo :

```
Note: ensure you have sufficient gpu_mem configured
eglCreateImageKHR:  failed to create image for buffer 0x1 target 12465 error 0x300c
eglCreateImageKHR failed.
```

Ne vous inquietez pas si c'est le cas : si vous voyez cette erreur, il suffit de modifier un paramètre pour la faire fonctionner.

Cette erreur veut dire que la GPU (processeur graphique) n'a pas suffisamment de mémoire attribuée pour exécuter la démo. C'est la GPU qui prend tout la lourde charge quand les graphiques 3D sont affichés à l'écran (un peu comme une carte graphique dans un PC de joueur). Le Raspberry Pi partage sa mémoire/RAM entre la CPU (processeur centrale) et la GPU (processeur graphique), et par défaut il est configuré de telle sorte que seuls 64 Mo de RAM sont dédiés à la GPU. Si on augmente cette valeur à 128, ça devrait régler le problème.

Afin de changer ce paramètre, vous devrez entrer la commande suivante :

`sudo raspi-config`

Un menu à fond bleu va s'ouvrir. Déroulez les actions suivantes :

- Allez dans Advanced Options.
- Allez dans Memory Split.
- Supprimez `64` et entrez `128` à la place. Appuyez sur `Entrée`.
- Descendre jusqu'à Finish.
- Cliquez sur Yes pour redemarrer.

Après s'être connecté de nouveau, entrez la commande suivante pour retourner à la démo `hello_teapot` :

`cd /opt/vc/src/hello_pi/hello_teapot`

Maintenant essayez de la lancer de nouveau, et vous devrez trouver désormais que ça marche.

`./hello_teapot.bin`

Cette démo continuera à tourner tant que vous n'aurez pas dit d'arreter. Pour quitter la démo appuyez sur `Ctrl – C`.

## Hello audio

Cette démo montre le fonctionnement de la sortie audio. Elle joue une onde sinusoïdale, qui fait un son comme WOO WOO WOO.

```
cd ..
cd hello_audio
ls
```

A noter le fichier en vert `.bin` ? Lancez-le ! Vous commencez à vous debrouiller maintenant ?

`./hello_audio.bin`

Ca va jouer le son via la sortie "jack" du Pi. Si vous utiliser un écran HDMI, vous pouvez forcer la sortie via HDMI en ajoutant `1` à la commande.

`./hello_audio.bin 1`

Cette démo continuera à tourner tant que vous n'aurez pas dit d'arreter. Pour quitter la démo appuyez sur `Ctrl – C`.

## Prochaine étape ?

- A ce stade vous commencez certainement à être à l'aise avec la navigation montant jusqu'au dossier parent `hello_pi` (via la commande `cd ..`) et puis descendant dans un des dossiers démo (en utilisant la commande `cd hello_quelquechose`).  
- Tentez de lancer certaines des autres démos de façon autonome. Celle de `hello_videocube` est un excellent point de départ.
