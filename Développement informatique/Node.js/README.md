# Comment utiliser Node.js sur Linux ?

## Installation de Node.js

Node.js est une plateforme JavaScript côté serveur qui repose sur le moteur JavaScript V8 (moteur de Chromium). Pour gérer différentes versions de Node.js, il est recommandé d'utiliser NVM (Node Version Manager), qui facilite l'installation et le changement de version de Node.js.

### Installation de NVM (Node Version Manager)

Pour installer NVM, suivez les étapes suivantes :

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash # pour télécharger et installer la dernière version de NVM
source ~/.bashrc # pour charger NVM dans le shell actuel
```

Vérifiez que NVM est installé correctement :

```bash
nvm --version
```

### Installation de Node.js via NVM

Une fois NVM installé, vous pouvez installer la dernière version stable de Node.js :

```bash
nvm install --lts # pour installer la dernière version LTS (Long Term Support) de Node.js
nvm use --lts # pour utiliser la version LTS installée par défaut
```

Vous pouvez également installer une version spécifique de Node.js :

```bash
nvm install 18.0.0 # remplacez 18.0.0 par la version souhaitée
nvm use 18.0.0 # pour utiliser la version installée
```

Pour lister les versions de Node.js installées et disponibles :

```bash
nvm ls # pour lister les versions installées localement
nvm ls-remote # pour lister toutes les versions disponibles à l'installation
```

## npm : Node Package Manager

`npm` est le gestionnaire de paquets par défaut de Node.js. Il vous permet d'installer, de mettre à jour et de gérer les dépendances pour vos projets Node.js.

### Commandes npm

- **Initialiser un nouveau projet Node.js** :

  ```bash
  npm init # pour initialiser un projet avec des questions interactives
  # ou
  npm init -y # pour initialiser un projet avec les valeurs par défaut
  ```

  > [!NOTE]
  > Ces commandes créent un fichier `package.json` qui contient les informations de votre projet:
  >
  > - les métadonnées: nom, version, description, auteur, license, description, mots clés
  > - les dépendances (paquets installés pour le projet)
  > - les scripts
  > - le point d'entrée `main`

- **Installer un paquet** :

  ```bash
  npm install <nom_du_paquet>
  ```

> [!NOTE]
> Les paquets installés via cette commande seront installés dans le dossier `node_modules` avec toutes ces dépendances (à la racine du projet). De plus, ce paquet sera listé dans la liste des paquets installés dans le fichier `package.json`.

Pour installer un paquet de manière globale (disponible sur tout le système) :

```bash
npm install -g <nom_du_paquet>
```

- **Installer une version spécifique d'un paquet** :

  ```bash
  npm install <nom_du_paquet>@<version>
  ```

- **Mettre à jour un paquet** :

  ```bash
  npm update <nom_du_paquet>
  ```

- **Supprimer un paquet** :

  ```bash
  npm uninstall <nom_du_paquet>
  ```

- **Lister les paquets installés** :

  ```bash
  npm list
  ```

- **Exécuter un projet Node.js** :

  ```bash
  node <nom_du_fichier>.js # pour exécuter un fichier javascript
  # ou
  npm run start # pour exécuter le script `start` définit dans le fichier `package.json`
  ```

> [!TIP]
> Vous pouvez créer autant de scripts que vous souhaitez dans le fichier de configuration `package.json`.
> Les scripts les plus courants sont :
>
> - `start` : pour exécuter le projet
> - `dev` : pour exécuter le projet en environnement de développement
> - `test` : pour exécuter les tests
> - `build` : pour compiler le projet pour un environnement de production
>
> Ils sont exécutables via la commande `npm run <nom_du_script>`.

## Yarn : Une alternative à npm

Yarn est une autre gestionnaire de paquets pour JavaScript, souvent préféré pour sa rapidité et son traitement efficace des dépendances.

> [!CAUTION]
> N'utlisez pas `yarn` et `npm` sur un même projet. Faites votre choix avant de créer un nouveau projet car mélanger les deux gestionnaires de paquets peut entraîner des conflits de dépendances, des duplications de paquets dans le répertoire node_modules, et d'autres problèmes imprévus.

### Installation de Yarn

Pour installer Yarn via npm, utilisez la commande suivante :

```bash
npm install -g yarn
```

### Commandes Yarn

Les commandes Yarn sont similaires à celles de npm :

- **Initialiser un projet** :

  ```bash
  yarn init
  ```

- **Installer un paquet** :

  ```bash
  yarn add <nom_du_paquet>
  ```

- **Installer une version spécifique d'un paquet** :

  ```bash
  yarn add <nom_du_paquet>@<version>
  ```

- **Mettre à jour un paquet** :

  ```bash
  yarn upgrade <nom_du_paquet>
  ```

- **Supprimer un paquet** :

  ```bash
  yarn remove <nom_du_paquet>
  ```

- **Lancer un script** :

  ```bash
  yarn <nom_du_script>
  ```

## Vite : Un Bundler pour créer des applications Web front-end

Vite est un outil de build moderne qui offre un développement rapide et une expérience utilisateur fluide. Il est souvent utilisé pour les projets React, Vue, et autres frameworks JavaScript modernes.

### Exemple: Création d'un projet React Typescript avec Vite

Pour installer Vite et créer un nouveau projet React avec TypeScript, suivez ces étapes :

```bash
npm create vite@latest <nom_du_projet> -- --template react-ts
cd <nom_du_projet>
npm install # pour installer les dépendances
```

### Lancer le serveur de développement

Pour démarrer le serveur de développement :

```bash
npm run dev
```

Le serveur Vite démarrera et le projet sera accessible par défaut à l'adresse [http://localhost:5173](http://localhost:5173).

> [!TIP]
> En mode `dev`, le serveur Vite écoute les modifications que vous effectuez sur votre code source et modifie le contenu du navigateur en fonction. Cela permet de voir les changements instantanément.

### Construction du projet pour un environnement de production

Pour construire le projet pour un environnement de production :

```bash
npm run build
```

Cela créera un dossier `dist` contenant les fichiers (html, css, js, "assets") optimisés pour un environnement de production. Ces fichiers ne dépendront plus de Node.js ni de Vite et pourront être hébergés par un serveur statique.

### Aperçu du projet en mode production

Pour prévisualiser le projet construit :

```bash
npm run preview
```

Cela lancera un serveur pour prévisualiser le projet comme s'il était en production.

## Quelques bonnes practiques

### Le fichier .gitignore

Si vous souhaitez déposer votre projet Node.js sur un dépôt Git, n'oubliez pas de créer un fichier `.gitignore` à la racine de votre projet et d'y ajouter au moins le dossier `node_modules`. Cela permettra à Git de ne pas avoir à enregistrer toutes les dépendances du projet. Cela vous fera gagner de l'espace sur votre dépôt Git et du temps de `push` et de `pull` de votre projet.

Cependant, si vous clonez votre dépôt, n'oubliez pas d'exécuter la commande `npm install` afin de télécharger à nouveau toutes les dépendances.
