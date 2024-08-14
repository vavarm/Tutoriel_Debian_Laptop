# VSCodium: Un IDE open-source polyvalent et grandement customisable

VSCodium est un fork de VSCode. Il est en tout point équivalent et retire les outils de télémétrie de Microsoft.

## Installation de VSCodium

Afin d'installer VSCodium sur votre ordinateur, suivez les étapes suivantes :

```bash
su -l # pour se connecter en tant que root et avoir les permissions pour utiliser APT
curl -fsSL https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg | gpg --dearmor -o /etc/apt/trusted.gpg.d/vscodium.gpg # pour ajouter la clé de distribution de VSCodium à APT
echo "deb https://download.vscodium.com/debs vscodium main" > /etc/apt/sources.list.d/vscodium.list # pour ajouter le depot de VSCodium à APT
apt update # pour obtenir les dernières mises à jour
apt install -y codium # pour installer VSCodium
exit # pour fermer la connexion root
```

> [!NOTE]
> Une fois installé, vous retrouverez LibreWolf dans votre bibliothèque d'applications.

> [!TIP]
> Vous pouvez également lancer VSCodium depuis votre terminal avec la commande `codium` ou `codium <nom_du_fichier>` ou `codium <répertoire_de_travail>`. (Exemple: pour ouvrir VSCodium depuis votre répertoire courant, exécutez `codium .`)

## Ajout du Marketplace de VSCode à VSCodium

Le marketplace de VSCodium est une bibliothèque d'extensions open-source reposant sur la [Open VSX Registry](https://open-vsx.org/). Cependant cette bibliothèque n'inclut pas les extensions Microsoft propriétaires telles que [`ms-python.python`](https://marketplace.visualstudio.com/items?itemName=ms-python.python) ou [`ms-vscode.cpptools`](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) qui vous permettent respectivement d'avoir un ensemble d'outils pour des projets Python et C/C++.

Pour ajouter le marketplace VSCode à VSCodium, utilisez la commande suivante :

```bash
su -l # pour se connecter en tant que root et avoir les permissions d'écrire dans un fichier système
sed -i 's|https://open-vsx.org/vscode/gallery|https://marketplace.visualstudio.com/_apis/public/gallery|g; s|https://open-vsx.org/vscode/item|https://marketplace.visualstudio.com/items|g' /usr/share/codium/resources/app/product.json
exit # pour fermer la connexion root
```

> [!CAUTION]
> Installer une extension depuis le marketplace de VSCode vous expose à de l'envoi d'informations de télémétrie par l'extension.
