# Projet QT: moteur de jeux et éditeur de jeux Mario

## Description:
Ce programme est un petit moteur et éditeur de jeux 2D utilisant QT
pour les interfaces utilisateur, OpenGL (fonctionnalités primitives)
pour les graphismes et QJSEngine pour le fonctionnement du jeu.

## Installation:
Ce programme a été conçu et optimisé pour Windows 10. Il a besoin de tourner à 200 fps 
pour réduire les lags et les roll* backs. Sur Linux, QT semble utiliser VSync limitant
le framerate à 60 fps et donc empêchant cette solution. Je vous conseille donc de ne
pas installer ce programme sur Linux.

## Installation sous Windows:
* Faite une installation complète de QT 5.6 ou plus sur le site officiel: https://download.qt.io/archive/qt/ 
* Ouvrez et installez la police de caractères du fichier: PressStart2P.ttf
* Ouvrez le projet (fichier Mario/Mario.pro) sous QTCreator
* Compiler le programme en mode Release (car QJSEngine est 10x plus lent en mode Debug).
* Exécutez le programme (flèche verte) 
* Des fenêtres de dialogue vont s'ouvrir, spécifiez les fichiers de ressource demandés (sprites.json puis map.json).

## Installation sous Linux:
* Installez QT 5.6 ou plus (cmd ou site officiel)
* Installez les packages:
	sudo apt* get install qtdeclarative5* dev libgl1* mesa* dev
* Ouvrez et installez la police de caractère du fichier: PressStart2P.ttf
* Ouvrez le projet (fichier Mario/Mario.pro) sous QTCreator.
* Compiler le programme en mode Release (car QJSEngine est 10x plus lent le mode Debug).
* Executez le programme (flèche verte).
* Des fenêtres de dialogue vont s'ouvrir, spécifiez les fichiers de ressource demandés (sprites.json puis map.json).

## Vocabulaire:
* Tiles: carreaux graphiques constituant la carte.
* Sprites: élements/objets/entités graphiques (associé à une liste de states).
* State: état/animation d'une sprite (associé à une liste de frame).
* Frame: image et boîte de collision composant une animation.

## Utilisation Jeu:
* Appuyez sur le bouton Start pour commencer le jeu.
* Utilisez les flèches directionnelles pour vous déplacer et la touche
espace pour sauter.
* Appuyez sur le bouton Reset pour arrêter le jeu.
* Pour pouvoir rejouer, il faut déplacer la caméra au début du niveau avant d'appuyer sur Start
* Appuyer sur le bouton Debug pour activer/désactiver le mode de débuggage
permettant de voir les sprites, les boîtes de collision et la grille de la carte. 

## Utilisation Editeur:
* Utiliser les flèches directionnelles ou le clique de la molette pour se déplacer dans la carte.
* Agrandir la fenêtre pour voir les fonctionnalités de l'éditeur de jeu.
* Selon la taille de l'écran et l'OS utilisé, ces outils peuvent ne pas
être visibles en plein écran. Dans ce cas* là, passez en mode fenêtré et
élargissez la fenêtre jusqu'à voir les deux menus (à gauche et à droite).

## Utilisation Outils de Dessin:
* Pour dessiner la carte, il suffit de cliquer sur la zone graphique.
* Le menu de droite: "Tilemap" permet de choisir les blocs de map à dessiner.
* Comme dans Paint: un clic gauche (resp. droit) dans ce menu sélectionne le
bloc placé lorsque l'on fait un clic gauche (resp. droit) dans sur la carte.
Ce bloc sélectionné est encadré en rouge (resp. bleu).
* Le menu de gauche: "Spritemap" permet de choisir les sprites à dessiner.
* Ici, le clic gauche permet de créer et de déplacer des sprites sur la carte
et le clic droit permet de supprimer les sprites.
* Par défaut, l'outil du menu de droite est utilisé, mais si un élément est 
sélectionné dans le menu de gauche alors c'est l'outil du menu de gauche qui
sera utilisé.

## Editeur de Sprite:
* Le menu "Spritemap" contient:
	* Une miniature de la sprite, state ou frame sélectionnée.
	* Des champs d'informations modifiables (nom, vitesse, taille, collision).
	* Un bouton script permettant de modifier le script global ou de 
		la sprite ou state sélectionnée.
	* Quatres bouttons d'édition des sprites, states et frames (➕: créer/éditer,
		⯅: déplacer vers le haut, ⯆:déplacer vers le bas, ❌:supprimer).
	* Un arbre affichants les sprites (à la racine), les states
		(dans chaque sprite) et les frames (dans chaque state).
	* Une console de log des scripts.

## Editeur de State:
L'éditeur de state est disponible en choisissant la state à modifier puis en
appuyant sur le bouton d'édition: +. Il suffit de sélectionner sur la zone graphique 
pour définir l'image ou la boîte de collision de la state selon le radio bouton coché.

## JavaScript:
L'éditeur de script est disponible en choisissant l'élément à modifier puis en
appuyant sur le bouton script. Il surligne les mots* clés, nombres, chaînes de caractères,
les commentaires et caractères spéciaux pour une meilleur lisibilité du code.
L'interface suivante permet aux scripts de communiquer avec le moteur de jeu:
	* x,y,vx,vy,ax,ay: position, vitesse, accélération de la sprite.
	* sx,sy: position de la camera.
	* model,state,frame: nom de la sprite, state et frame courrante.
	* collisions.tile,.top,.left,.right,.bottom: les collisions avec l'environement.
	* collisions.sprite: la liste des collisions avec les autres sprites.
	* dt: durée depuis la dernière update en ms.
	* log: texte à afficher dans les logs (pour débugger)
	* despawn: flag à assigner à true pour détruire cette sprite.
	* KeyUp,KeyDown,KeyLeft,KeyRight,KeyJump,KeyRun: état des touches du clavier.
	* score,coins,world,time: Affichage de l'état du jeu.

## Crédit:
Ce jeu est fortement inspiré du jeu Super Mario Bros sur NES: https://en.wikipedia.org/wiki/Super_Mario_Bros.
Les ressources sont tiré de ce jeu par internet.
La police de caractère utilisé pour le jeu est "press start 2p" accessible à l'address: http://www.fontspace.com/codeman38/press* start* 2p.
La police de caractère utilisé pour l'éditeur de script est "Consolas" disponible sur toutes les versions de Windows depuis Vista.