# Comment utiliser Python sur Linux ?

## Installation de Python

Par défaut, une distribution Python est déjà installée dans Debian. Vous pouvez vérifiez cette installation ainsi que sa version avec la commande suivante :

```bash
python3 --version
```

Si cette commande vous renvoie un numéro de version, cela signifie que Python est déjà installé. Par exemple :

```bash
python 3.11
```

Si la commande python3 n'est pas trouvée ou que vous obtenez une erreur, cela signifie que Python 3 n'est pas installé. Vous pouvez l'installer comme ceci :

```bash
su -l # pour se connecter en tant que root et avoir les permissions pour utiliser APT
apt update # pour obtenir les dernières mises à jour
apt install python3 # pour installer la dernière version stable de python depuis les dépôts APT
exit # pour fermer la connexion root
```

## Python package manager (Pip)

`pip` est l'outil de gestion de paquets pour Python. Il vous permet d'installer, de mettre à jour et de gérer les bibliothèques Python que vous souhaitez utiliser dans vos projets.

Vous pouvez vérifier la version de `pip` avec la commande :

```bash
python3 -m pip --version
```

### Commandes `pip`

- Installer un paquet :

```bash
python3 -m pip install <nom_du_paquet>
```

- Installer une version spécifique d'un paquet :

```bash
python3 -m pip install <nom_du_paquet>==<version_du_paquet>
```

- Mettre à jour un paquet :

```bash
python3 -m pip install --upgrade <nom_du_paquet>
```

- Supprimer un paquet :

```bash
python3 -m pip uninstall <nom_du_paquet>
```

- Lister les paquets installeés :

```bash
python3 -m pip list
```

- Enregistrer la liste des paquets installés dans un fichier :

```bash
python3 -m pip freeze > requirements.txt
```

- Charger la liste des paquets installeés depuis un fichier :

```bash
python3 -m pip install -r requirements.txt
```

> [!NOTE]
> Le fichier requirements.txt doit avoir le format suivant :
>
> ```txt
> <nom_du_paquet1>==<version_du_paquet1>
> <nom_du_paquet2>==<version_du_paquet2>
> ...
> ```

### Installation du paquet apt `python3-pip`

Si vous souhaitez installer `pip` et ne pas avoir à passer par python pour l'utiliser, vous pouvez installer `pip` comme ceci :

```bash
su -l # pour se connecter en tant que root et avoir les permissions pour utiliser APT
apt-get update # pour obtenir les dernières mises à jour
apt-get install python3-pip # pour installer la version de pip
exit # pour fermer la connexion root
```

## Environnements virtuels (venv)

Depuis Python 3.3, Python inclut un module appelé venv, qui permet de créer des environnements virtuels. Un environnement virtuel est un espace isolé où vous pouvez installer des paquets spécifiques à un projet sans affecter les autres projets ou le système global.

### Création d'un environnement virtuel

Pour créer un environnement virtuel, utilisez la commande suivante :

```bash
python3 -m venv venv
```

### Activation d'un environnement virtuel

Pour activer un environnement virtuel, utilisez la commande suivante :

```bash
source venv/bin/activate
```

Après activation, le nom de l'environnement (par exemple venv) apparaîtra dans le terminal entre parenthèses avant l'invite de commande. Cela signifie que vous êtes maintenant dans l'environnement virtuel, et toutes les commandes Python ou pip que vous exécuterez se feront dans cet environnement isolé.

### Desactivation d'un environnement virtuel

Pour desactiver un environnement virtuel, utilisez la commande suivante :

```bash
deactivate
```
