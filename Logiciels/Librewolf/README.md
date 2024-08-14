# LLibreWolf : Un Navigateur Web Open Source Centré sur la Confidentialité et la Sécurité

LibreWolf est un fork de Firefox. Par défaut, l'installation de Gnome entraine également l'installation de Firefox ESR (Extended Support Release) qui est la version stable de Firefox.

Cependant, il peut être intéressant de migrer vers un navigateur minimaliste et déjà équipé de fonctionnalités que vous aurez de toute façon installlées et configurées sur votre Firefox.

## Installation de LibreWolf

Pour installer LibreWolf sur votre système, suivez les étapes suivantes :

```bash
su -l # pour se connecter en tant que root et avoir les permissions pour utiliser APT
curl -fsSL https://deb.librewolf.net/keyring.gpg | gpg --dearmor -o /etc/apt/trusted.gpg.d/librewolf.gpg # pour ajouter la clé de distribution de LibreWolf à APT
echo "deb https://deb.librewolf.com.net bookworm main" > /etc/apt/sources.list.d/librewolf.list # pour ajouter le depot de LibreWolf à APT
apt update # pour obtenir les dernières mises à jour
apt install -y librewolf # pour installer LibreWolf
exit # pour fermer la connexion root
```

> [!NOTE]
> Une fois installé, vous retrouverez LibreWolf dans votre bibliothèque d'applications.
