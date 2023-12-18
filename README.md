# lab-forensic

L’analyse Forensic désigne l’investigation effectuée sur le système d’information suite à une attaque informatique. Grâce aux données récoltées par les analystes, la structure pourra mieux comprendre ce qui s’est réellement passé pour ensuite tirer des conclusions. Cela permet de récolter des preuves pour justifier une action en interne ou pour lancer une procédure judiciaire.

## Analyse de fichiers et d'images

### Les informations cachées

Quelques outils à utiliser pour avoir des informations pertinentes sur un fichier sous Linux.

* `file` : le type de fichier
* `strings`: extrait sur la console les caractères affichables d'un fichier
* `exiftool`: affichier / modifier les métadonnées d'un fichier
* `binwalk`: outil permettant de rechercher dans une image binaire donnée des fichiers incorporés et du code exécutable

TP:
Récupérez le fichier `anonyme.png` dans le répertoire `TP` du dépot git. Je souhaite connaitre qui est le créateur de cette image?

### Listing fichiers

`find & locate`: trouvez un fichier ou un dossier sous linux

TP:
* Trouvez ou se trouve le fichier `nom_fichier` sur la VM Kali.
* Trouvez tous les fichiers de type `.txt` sur la VM Kali

### Fichiers supprimés

foremost / photorec / dd_rescue / scalpel

TP:


## Capture mémoire

volatility

TP: (https://www.root-me.org/fr/Challenges/Forensic/Command-Control-niveau-2)





