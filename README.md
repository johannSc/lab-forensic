# lab-forensic

L’analyse Forensic désigne l’investigation effectuée sur le système d’information suite à une attaque informatique. Grâce aux données récoltées par les analystes, la structure pourra mieux comprendre ce qui s’est réellement passé pour ensuite tirer des conclusions. Cela permet de récolter des preuves pour justifier une action en interne ou pour lancer une procédure judiciaire.

## Analyse de fichiers et d'images

### Les informations cachées

Quelques outils à utiliser pour avoir des informations pertinentes sur un fichier sous Linux.

* `file` : le type de fichier
* `strings`: extrait sur la console les caractères affichables d'un fichier
* `exiftool`: affichier / modifier les métadonnées d'un fichier
* `binwalk`: outil permettant de rechercher dans une image binaire donnée des fichiers incorporés et du code exécutable

$${\color{green}TP}$$
Récupérez le fichier `anonyme.png` dans le répertoire du dépot git. Je souhaite connaitre qui est le créateur de cette image?

### Listing fichiers

`find & locate`: trouvez un fichier ou un dossier sous linux

$${\color{green}TP}$$
* Trouvez ou se trouve le fichier `boot.log` sur la VM Kali.

* Trouvez tous les fichiers de type `.txt` sur la VM Kali mais uniquement dans le répertoire /var

### Fichiers supprimés

Regardez les différents outils suivants:

```
testdisk (photorec) / dd_rescue / scalpel (foremost)
```

$${\color{green}TP}$$

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

Puis ajouter dans la partie `png`:

```
png     y       20000000        \x50\x4e\x47?   \xff\xfc\xfd\xfe
png     y       20000000        \x89\x50\x4e?
```

Des résultats plus probants?


## Capture mémoire

Les informations importantes ne se situent pas forcément dans les fichiers (comme sur le fichier image vu précédémment) mais peuvent se trouver en mémoire.

Un outil très pratique permet de faire un `dump` de la mémoire, et ensuite de pouvoir la parcourir: `volatility`

$${\color{green}TP}$$

Dans ce TP, je souhaite connaitre le nom du pc sur lequel le dump a été fait.

* Installation de volatility

Tout d'abord clonez le dépot:
```
git clone https://github.com/volatilityfoundation/volatility3
```

Puis lancez l'installation des dépendances:
```
pip3 install -r requirements-minimal.txt
```

Testez ensuite d'exécuter volatility:
```
python3 vol.py -h
```

* Téléchargez le dump mémoire qu'on va analyser: https://sandbox.scourzic.net/td/ch2.tbz2

* Quelques conseils pour bien démarrer:

  - Il est nécessaire pour volatility de connaitre le type d'image (en gros la version de l'OS) avant toute chose. Pour cela une unique commande:
 
```
python3  vol.py  -f ch2.dmp imageinfo
```

Il n'est pas rare que volatility propose plusieurs versions. En général choisissez la plus récente.

  - Naviguer sur un dump mémoire c'est comme être directement sur l'ordinateur. Vous verrez toutes les traces (fichiers ouverts, exécution dans la base de registre...)

Souvent il faut avoir une idée d'ou chercher, sinon vous pouvez être noyé sous les informations.
