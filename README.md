# Tutoriel Debian Laptop

Ce tutoriel vous permettra d'installer un système d'exploitation GNU/Linux Debian minimal sur un ordinateur portable. Vous aurez ensuite la possibilité d'y rajouter vos propres logiciels et/ou ceux qui sont mentionnés dans ce dépot.

Même si ce tutoriel est axé sur les ordinateurs portables, vous pouvez tout à fait le suivre afin d'effectuer l'installation sur un ordinateur fixe. Il faudra alors passer certaines parties relatives aux spécificités d'un ordinateur portable telles que les problématiques d'autonomie ou de touchpad.

> [!NOTE]
> Si vous souhaitez proposer des correctifs et/ou participer à l'enrichissement de ce projet, n'hésitez pas à forker ce dépôt et à me solliciter via une issue Github.

## Pré-requis

Avant de commencer l'installation de Debian sur votre ordinateur portable, assurez-vous de disposer des éléments suivants :

- Un ordinateur portable compatible (32 bits ou 64 bits) sur lequel vous souhaitez installer Debian. Si vous effectuez l'installation sur un ordinateur fixe, notez que certaines étapes spécifiques aux portables (comme la gestion de l'autonomie ou du touchpad) pourront être ignorées.

- Une clé USB d'au moins 8 GB

> [!NOTE]  
> Cette clé sera utilisée pour créer un support d'installation bootable. Veillez à ce qu'elle soit vide, car toutes les données seront effacées lors du processus de création.

- Une connexion réseau par câble Ethernet

> [!NOTE]  
> Cette connexion est recommandée pour éviter les problèmes liés à la configuration du Wi-Fi lors de l'installation, et pour garantir que tous les paquets nécessaires peuvent être téléchargés sans interruption.

## Installation de l'image Debian sur clé USB (WIP)

Pour installer Debian sur votre ordinateur portable, vous devrez d'abord créer une clé USB bootable contenant l'image Debian. Voici les étapes à suivre :

### 1. Téléchargement de l'image Debian

- Rendez-vous sur le [site officiel de Debian](https://www.debian.org/distrib/)
- Choisissez l'image DVD pour une installation complète
- Sélectionnez l'architecture correspondant à votre ordinateur (64 bits ou 32 bits)
- Téléchargez le fichier .iso sur votre ordinateur

> [!NOTE]
> Exemple: J'ai un ordinateur avec un architecture 64 bits. Je vais donc télécharger le fichier `ISO DVD-1 pour PC 64 bits`

### 2. Préparation de la clé USB

Avant de créer une clé USB bootable, assurez-vous d'avoir une clé USB d'au moins 8 GB, totalement vide. Si des fichiers y sont présents, sauvegardez-les ailleurs car cette opération effacera tout le contenu de la clé.

### 3. Création de la clé USB bootable

Pour transférer l'image Debian sur votre clé USB et la rendre bootable, vous pouvez utiliser un logiciel dédié. Deux options populaires sont :

#### Option 1 : Utiliser Rufus (Windows)

- Téléchargez [Rufus](https://rufus.ie/fr/) et installez-le sur votre machine Windows
- Insérez la clé USB dans votre ordinateur
- Lancez Rufus :
  - Dans le champ Périphérique, sélectionnez votre clé USB
  - Dans le champ Sélection de démarrage, cliquez sur Sélectionner et choisissez l'image Debian .iso que vous avez téléchargée
  - Les autres options (Partition, Système de fichiers, etc.) sont généralement configurées automatiquement
  - Cliquez sur Démarrer pour lancer le processus de création

Une fois terminé, Rufus vous indiquera que la clé USB est prête.

#### Option 2 : Utiliser Etcher (Windows, macOS, Linux)

- Téléchargez [Etcher](https://etcher.balena.io/) et installez-le sur votre machine
- Insérez la clé USB dans votre ordinateur
- Lancez Etcher :
  - Cliquez sur Flash from file et sélectionnez l'image Debian .iso
  - Cliquez sur Select target et choisissez votre clé USB
  - Cliquez sur Flash pour démarrer le processus

Une fois l'opération terminée, Etcher vous notifiera que votre clé est prête.

## Installation de Debian sur l'ordinateur

- Connectez votre ordinateur à un réseau connecté à internet via ethernet
- Connectez votre clé USB à votre ordinateur
- Démarrez votre ordinateur en appuyant sur le bouton de sélection de volume de boot (généralement F12 sur Dell et Lenovo)

Vous accédez alors à l'interface d'installation de Debian.

> [!IMPORTANT]
> Les commandes permettant de naviguer dans l'interface d'installation sont les suivantes:
>
> - Valider: Entrée
> - Naviguer à l'intérieur des options: Touches fléchées
> - Naviguer entre les options: Tab
> - Modifier: Espace

> [!TIP]
> N'oubliez pas d'activer la fonctionnalité Verr. Num si vous souhaitez écrire des caractères numériques via votre pavé numérique.

- Sélectionnez `Advanced options …`
- Sélectionnez `… Expert install`

### 1. Menu: Choose language

- sélectionez **French**
- sélectionez **France**
- sélectionez **France**
- sélectionez **Continuer**

### 2. Menu: Configurer le clavier

- sélectionez **Français**

### 3. Menu: Détection et montage du support d’installation

- sélectionez **Continuer**

### 4. Menu: Charger des composants depuis le support d’installation

- sélectionez **Continuer**

### 5. Menu: Détecter le matériel réseau

- sélectionez **Continuer**

### 6. Menu: Configurer le réseau

- sélectionez **Continuer**
- l'interface ethernet (pas la `wireless`qui, si vous l'avez, correspond à la carte wifi de votre ordinateur)
- sélectionez **Oui**
- sélectionez **Continuer**
- `Nom de machine` (le nom que portera l'ordinateur dans votre réseau)
- `Domaine` (laissez ce champ vide)

### 7. Menu: Créer les utilisateurs et choisir les mots de passe

Dans ce menu, nous allons donner un mot de passe à notre utilisateur root (l'utilisateur administrateur du système) et nous allons créer notre premier utilisateur ordinaire ("test") qui nous permettra de tester notre système et d'accéder à notre utilisateur root.

- sélectionnez **Oui**
- saisissez le `Mot de passe de root` (ce mot de passe sera celui de l'utiliateur administrateur du système donc saisissez un mot de passe fort)
- saisissez à nouveau le même mot de passe dans `Confirmation mot de passe de root`
- dans `Créer compte utilisateur ordinaire` sélectionnez **Oui**
- saisissez le nom complet de l'utilisateur ordinaire: **test**
- saisissez l'identifiant de l'utilisateur ordinaire: **test**
- saisissez le `Mot de passe de test`: **test**
- saisissez à nouveau le même mot de passe dans `Confirmation mot de passe de test`

### 8. Menu: Configurer l'horloge

- dans `Configurer l’horloge: NTP`? saisissez **Oui**
- saisissez l'adresse NTP suivante: 0.debian.pool.ntp.org
- saisissez votre région (**Europe de l’Ouest** si vous êtes en France métropolitaine)

### 9. Menu: Détecter les disques

- **Continuer**

### 10. Menu: Partitionner les disques

- sélectionner: **Manuel**

#### 10.1 Formatage du disque de l'ordinateur

- sélectionner le disque de l'ordinateur
- dans `créer nouvelle table`, sélectionnez **Oui**
- sélectionnez le format `gpt`

#### 10.2 Création d'une partition EFI

Créer une partition EFI sur le disque va permettre de lancer le système d'exploitation via l'interface logicielle EFI qui remplace désormais l'environnement de démarrage BIOS.

- sélectionnez **Espace libre**
- sélectionez **Créer une nouvelle partition**
- choisissez une taille de **513 MB**
- sélectionnez **Début**
- dans la fenêtre de paramétrage, sélectionnez **Utiliser comme 'Partition système EFI'**, puis **Fin du paramétrage de cette partition**

#### 10.3 Création d'une partition d'échange

Créer une partition d'échange (aussi appelée mémoire d'échange (swap) ou mémoire cache) est une partition qui permet de décharger la mémoire vive physique (RAM) sur le disque lors d'une mise en veille ou d'hibernation du système.

- sélectionnez **Espace libre**
- sélectionez **Créer une nouvelle partition**
- choisissez une taille correspondant à celle de votre mémoire vive en **GB** (exemple: **8GB** ou **16GB**)
- sélectionnez **Début**
- dans la fenêtre de paramétrage, sélectionnez **Utiliser comme 'espace d’échange'**, puis **Fin du paramétrage de cette partition**

#### 10.4 Création d'une partition système

A partir de ce point, vous avez deux possibilités:

- soit vous suivez le tutoriel afin de créer deux partitions: une sur '/' qui prendra 10% du disque et une sur '/home' qui prendra l'espace restant. Cette stratégie nous permet de maintenir plus facilement notre partition '/home' (en cas de restauration de cette partition par exemple) mais limite la taille de la partition '/' ce qui peut poser problème si vous utilisez des technologies qui ne sont pas user-oriented telles que docker ou flatpak
- soit vous décidez de créer une seule partition système sur '/' en utilisant tout l'espace restant. Dans ce cas, sélectionnez la taille par défaut pour cette partition (elle correspond à l'espace restant sur le disque) et sautez le paragraphe `10.5`

> [!NOTE]
> Pour illlustrer, j'utilise moi-même Docker en suivant la deuxième option ce qui limite ma partition '/' à 50GB (ayant un disque de 500GB). Cela m'est suffisant car, sur ma partition '/', je n'ai que Docker, le système d'exploitation et mes logiciels installés via apt. Je fais juste attention à ne pas garder de containers, images ou volumes inutilisés qui me prendraient de la place inutilement. Donc, à vous de voir en fonction de vos besoins et de la taille de votre disque.

La première option consiste à faire les choix suivants:

- sélectionnez **Espace libre**
- sélectionez **Créer une nouvelle partition**
- choisissez une taille correspondant à 10% de la taille de votre disque (exemple: 50GB si votre disque fait 500GB)
- sélectionnez **Début**
- dans la fenêtre de paramétrage, sélectionnez **Utiliser comme 'ext4'**, puis **Point de montage '/'**, puis **Fin du paramétrage de cette partition**

#### 10.5 Création d'une partition utilisateur

C'est cette partition (la plus grande) qui servira à stocker nos données utilisateurs. Elle contiendra donc les fichiers, logiciels, configurations de chaque utilisateur indépendamment des autres.

- sélectionnez **Espace libre**
- sélectionez **Créer une nouvelle partition**
- validez la taille qui vous est proposée (celle-ci correspond à l'espace restant)
- sélectionnez **Début**
- dans la fenêtre de paramétrage, sélectionnez **Utiliser comme 'ext4'**, puis **Point de montage '/home'**, puis **Fin du paramétrage de cette partition**

#### 10.6 Fin du partitionnement des disques

- sélectionnez **Terminer le partitionnement et appliquer les changements**

> [!CAUTION]
> La prochaine action formattera et donc efacera toutes les données présentes sur les disques que vous aurez sélectionnés dans les étapes précédentes

- sélectionnez **Oui**

### 11. Menu: Installer le système de base

- sélectionnez **linux-image-amd64** (si 64 bits, sinon **linux-image-amd32**)
- sélectionnez **image générique**

### 12. Menu: Configurer l’outil de gestion des paquets

- dans la sélections du miroir, sélectionnez **Non**
- dans les `Services à utiliser`, décochez toutes les options

### 13. Menu: Choisir et installer des logiciels

- sélectionnez **Pas de mises à jour automatiques**
- dans `popularity-contest`, sélectionnez **Non**
- dans `Tasksel`, cochez seulement **utilitaires usuels du système**

> [!NOTE]
> Nous installerons l'environnement de bureau plus tard manuellement (sans passer par Tasksel) ce qui nous permettra d'effectuer une installation minimale

### 14. Menu: Installer le programme de démarrage GRUB

- dans `Forcer l’installation sur le chemin des supports amovibles EFI`, sélectionnez **Oui** (c'est pour cette fonctionnalité que nous avons créé une partition EFI)
- dans `Démarrer Debian automatiquement`, sélectionnez **Oui**
- dans `os-prober`, sélectionnez **Non** (hormis si vous souhaitez faire du multi-boot)

### 15. Menu: Terminer l’installation

- dans `UTC`, sélctionnez **Oui**
- retirez le périphérique USB d’installation, puis sélectionnez **Continuer**

Votre ordinateur va alors redémarrer et vous vous retrouvez sur le terminal de votre système Debian fraichement installé.

Il est maintenant temps de configurer votre système afin de pouvoir l'utiliser dans de bonnes conditions.

Connetez vous en tant que root.

> [!TIP]
> Quand vous taperez le mot de passe, celui-ci n'apparaitra pas. C'est le comportement par défaut des systèmes Unix qui permet de masquer le contenu du mot de passe ainsi que sa taille.

## Configuration de l'utilisateur `test`

L'utilisateur `test` est un utilisateur permettant de ... tester. À ce compte, il peut être intéressant de lui donner un dossier temporaire qui se viderait à chaque reboot. C'est pratique sur Linux car il en existe déjà un: `/tmp`. Pour modifier la configuration de l'utilisateur `test`, exécutez la commande suivante:

```bash
usermod -m -d /tmp test && rm -r /home/test
```

> [!NOTE]
> Cette commande attribue le dossier `/tmp` à l'utilisateur `test` et supprime l'ancien dossier de l'utilisateur `test`

## Initialisation d'APT

`APT` (Advanced Packaging Tool) est un outil Debian qui permet d'installer et de mettre à jour des logiciels ainsi que le système d'exploitaition.

Afin de l'utiliser, il faut lui spécifier l'emplacement des dépôts sur lesquels il doit se synchroniser.

Pour ce faire, suivez les étapes suivantes:

- ouvrez le fichier qui liste les dépôts via la commande suivante:

```bash
nano /etc/apt/sources.list
```

- remplacez le contenu du fichier par les lignes suivantes:

```bash
deb http://deb.debian.org/debian bookworm main contrib non-free non-free-firmware
deb http://deb.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
deb http://deb.debian.org/debian bookworm-updates main contrib non-free non-free-firmware
```

- sauvegardez le fichier: `CTRL+S`
- quittez l'éditeur: `CTRL+X`

## Mise à jour du système

Maintenant qu'APT sait dans quels dépôts chercher les logiciels, il est temps de mettre à jour le système via la command suivante:

```bash
apt update && apt upgrade -y
```

> [!NOTE]
> La commande `apt update` va rechercher toutes les mises à jour disponibles dans les dépôts que vous avez listés et `apt upgrade -y` va installer toutes les mises à jour sans vous demander de confirmation

## Installation de Gnome

Le système est un peu austère. En effet, il manque un environnement de bureau. Ce dernier nous permettra d'ouvrir des fenêtres et de pouvoir utiliser des logiciels avec interface graphique.

Dans ce tutoriel, je vous propose d'installer l'environnement de bureau Gnome (aujourd'hui dans sa 3ème version). Il est bien documenté, bénéficie d'une grande communauté d'utilisateurs et est grandement customisable. L'un de ses défauts est qu'il est un peu lourd par rapport à d'autres, donc si vous souhaitez un environnement plus léger je vous recommande vivement d'installer l'environement Mate (un fork de la 2ème version de Gnome).
Personnellement, j'ai opté pour la version actuelle de Gnome car je souhaite bénéficier d'une interface contemporaine et de fonctionnalités pré-installées et bien intégrées.

Pour installer Gnome, le plus simple serait de passer par l'outil Tasksel. Seulement celui-ci effectuerait une installation par défaut qui nous rajouterait des logiciels.

Nous allons donc faire une installation minimale manuellement.

Tout d'abord, installons un environnement Gnome minimal:

```bash
apt install -y gnome-core
```

Ensuite, nous allons modifier la configuration réseau du système car celle-ci sera désormais gérée par Gnome:

- exécutez la commande suivante:

```bash
apt purge -y ifupdown && nano /etc/NetworkManager/NetworkManager.conf
```

- dans l'éditeur nano qui s'ouvre, remplacez `[ifupdown] managed=false` par `[ifupdown] managed=true`

- exécutez les raccourcis `CTRL+S` et `CTRL+X` afin d'enregistrer vos modifications et de quitter l'éditeur nano

- exécutez la commande suivante pour redémarrer votre ordinateur:

```bash
shutdown -r now
```

Lors du redémarrage de votre ordinateur, vous vous apercevrez qu'un écran affichant l'heure s'affiche. Cet écran provient du gestionnaire de sessions `GDM3` qui est une application graphique de Gnome permettant de se connecter à un utilisateur.

- appuyez sur la touche `Entrée`

- connectez vous à votre utilisateur `test`

> [!TIP]
> Par défaut, vous ne pouvez pas vous connecter à l'utilisateur `root` depuis GDM3

Vous arrivez alors sur votre environnement de bureau en étant connecté en tant qu'utilisateur `test`.

## Configuration de Gnome

Ouvrez le terminal:

- saisissez `ALT+F2` (maintenez la touche `Fn` en même temps si besoin)
- saisissez `gnome-terminal` dans le champ `Lancer une commande`

Les configurations que nous allons modifier sont les suivantes:

- Activer `Verr. Num` au démarrage:

```bash
gsettings set org.gnome.desktop.peripherals.keyboard remember-numlock-state true
```

- Activer le redimensionnement automatique des fenêtres en fonction de la taille des moniteurs:

```bash
gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
```

> [!TIP]
> Si vous souhaitez ajuster le niveau de zoom des éléments affichés par Gnome et des fenêtres, vous pouvez ouvrir les paramètres (icône engrenage dans le coin en haut à droite), sélectionner l'onglet `Écrans` et changer l'attribut `Échelle`

## Installation des outils de base

À partir d'ici, nous allons nous connecter en tant que root afin d'exécuter des commandes qui nécessitent des privilèges administrateurs.

- exécutez la commande suivante pour se connecter en tant qu'utilisateur `root`:

```bash
su -l
```

- saisissez le mot de passe de l'utilisateur `root`

Quelques outils sont essentiels et vous seront à un moment donné nécessaires:

- `build-essential` qui contient un ensemble d'outils de compilation et de librairies C, C++ pour construire des exécutables binaires
- `curl` qui est un outil vous permettant d'effectuer des requêtes http sans passer par un navigateur
- `git` qui est un outil de contrôle de versions

Pour les installer, exécutez la commande suivante:

```bash
apt install -y build-essential curl git
```

## Création d'un utilisateur

Vous avez donc deux utilisateurs: `root` et `test`.

Il vous manque désormais un utilisateur principal.

Pour le créer, exécutez la commande suivante (en remplacant `<username>` par l'identifiant que vous voulez donner à votre nouvel utilisateur):

```bash
adduser <username>
```

> [!TIP]
> Si vous n'avez pas d'idée de nom d'utilisateur, une convention consiste à le nommer `prénom.nom` (exemple: `john.doe`)

Cette commande vous amène à remplir plusieurs attributs:

- `Enter new UNIX password`: entrez le mot de passe de l'utilisateur (saisissez un mot de passe fort, il peut être le même que le mot de passe de l'utilisateur `root`)
- `Retype new UNIX password`: saisissez à nouveau le mot de passe
- Vous pouvez laisser vide toutes les autres attributs (ils ne servent qu'à donner des métadonées à l'utilisateur)

> [!IMPORTANT]
> Si vous avez déjà touché à du Linux vous connaissez surement le préfixe `sudo` qui permet de donner les privilèges administrateurs à un utilisateur ordinaire. Si vous suivez ce tutoriel, vous ne verrez jamais ce préfixe. En effet, j'ai décidé de ne pas permettre l'utilisation de ce préfixe. J'ai effectué ce choix pour deux raisons principales:
>
> - Un utilisateur ordinaire est un utilisateur qui utilise le système qu'on lui met à disposition. Il peut, s'il le souhaite, se rajouter des logiciels et des fichiers dans son dossier mais il n'est pas là pour ajouter et/ou modifier des logiciels et des configurations sur tout le système (ce que fait APT par exemple)
> - Donner toutes les permissions administrateurs à un utilisateur lambda (ce que fait le préfixe `sudo`) est vecteur de failles de sécurité (coucou Windows et MacOS qui ne se privent pas de nous accorder ces privilèges administrateurs très/trop facilement). C'est l'une des raisons pour lesquelles vous trouverez peu d'anti-virus sur Linux (vous êtes censés savoir ce que vous faites sur votre système 😉)

> [!NOTE]
> Si vous souhaitez tout de même permettre l'utilisation de ce préfixe à vos utilisateurs, il vous suffit de les ajouter au groupe `sudo` via la commande `usermod -aG sudo <username>`. Cependant soyez certain que vos utilisateurs disposent d'un mot de passe assez fort car, avec ce préfixe, vos utilisateurs disposent de tous les droits administrateurs.

## Pour aller plus loin

> [!NOTE]
> Ce paragraphe s'actualisera en fonction du contenu de ce dépôt. Il regroupera des tutoriels sur l'installation, la configuration et l'utilisation de logiciels ainsi qu'une liste de bonnes pratiques et d'astuces.

## Remerciements

La réalisation de ce tutoriel n'aurait pas été possible sans l'aide de M. Michel Facerias et son [tutoriel](https://www.facerias.org/doku.php?id=michel:debian:debinstall:01-install) sur lequel repose ce présent tutoriel. Je vous invite à le consulter si vous souhaitez aller plus loin sur certaines étapes.

## Clause de non-responsabilité

Ce tutoriel est fourni à titre indicatif et ne garantit pas des résultats spécifiques. Je décline toute responsabilité en cas de perte de données, de dommages matériels ou de toute autre conséquence résultant de l'application de ce guide. Vous êtes seul responsable de vos actions et des décisions que vous prenez lors de l'installation de Debian sur votre ordinateur. Avant de commencer, assurez-vous d'avoir sauvegardé toutes vos données importantes et de bien comprendre chaque étape du processus.
