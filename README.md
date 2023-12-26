# lab-forensic

L’analyse Forensic désigne l’investigation effectuée sur le système d’information suite à une attaque informatique. Grâce aux données récoltées par les analystes, la structure pourra mieux comprendre ce qui s’est réellement passé pour ensuite tirer des conclusions. Cela permet de récolter des preuves pour justifier une action en interne ou pour lancer une procédure judiciaire.

## Analyse de fichiers et d'images

### Les informations cachées

Quelques outils à utiliser pour avoir des informations pertinentes sur un fichier sous Linux.

* `file` : le type de fichier
* `strings`: extrait sur la console les caractères affichables d'un fichier
* `exiftool`: affichier / modifier les métadonnées d'un fichier
* `binwalk`: outil permettant de rechercher dans une image binaire donnée des fichiers incorporés et du code exécutable

```diff
+TP:
```
Récupérez le fichier `anonyme.png` dans le répertoire du dépot git. Je souhaite connaitre qui est le créateur de cette image?

### Listing fichiers

`find & locate`: trouvez un fichier ou un dossier sous linux

TP:
* Trouvez ou se trouve le fichier `boot.log` sur la VM Kali.

* Trouvez tous les fichiers de type `.txt` sur la VM Kali mais uniquement dans le répertoire /var

### Fichiers supprimés

Regardez les différents outils suivants:

```
testdisk (photorec) / dd_rescue / scalpel (foremost)
```

TP: 

On va essayer à partir d'une image de retrouver des informations cachées ou supprimées.
Au préalable vous pouvez utiliser la commande suivante pour monter l'image `image.dd` présente dans le dépot afin de voir ce qu'elle contient:

```
sudo mkdir /media/image
```

```
sudo mount -t auto -o loop /chemin/image.dd /media/image/
```

Vous pouvez ensuite naviguer dans /media/image et voir son contenu.

* Installez l'outil testdisk, puis essayer d'utiliser celui ci avec l'image fournie dans le dépot git:

Voyez vous des secrets ou informations cachées?
  
* Maintenant utilisons l'outil `scalpel`. Paramétrez le fichier de configuration:

```
nano /etc/scalpel/scalpel.conf
```

Des résultats plus probants?


## Capture mémoire

volatility

TP: (https://www.root-me.org/fr/Challenges/Forensic/Command-Control-niveau-2)





