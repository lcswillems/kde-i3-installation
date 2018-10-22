# Installer et configurer Kubuntu et i3wm

Ce document a pour but de vous proposer la marche que j'ai suivie (et mis beaucoup de temps à trouver) pour installer et configurer Kubuntu et i3wm en un minimum de temps. Il s'adresse à des personnes ayant déjà un petit peu d'expérience avec Linux.

## VirtualBox

Commencez par installer [VirtualBox](https://www.virtualbox.org/). Ce logiciel vous permet de créer et faire tourner des machines virtuelles dans votre système d'exploitation. Par exemple, si vous êtes sous Windows, VirtualBox va pouvoir simuler une machine avec une certaine RAM et un certain espace de stockage (que vous pourrez définir) dans laquelle vous allez pouvoir installer et configurer Kubuntu et i3wm. Cette machine virtuelle sera isolée de la machine hôte, votre Windows en l'occurrence.

Installer et configurer Kubuntu et i3wm dans une machine virtuelle avant de le faire véritablement sur votre ordinateur vous permettra de vous entraîner : de telles installations peuvent mener à des situations critiques. Si vous rencontrez une telle situation dans une machine virtuelle, vous pouvez :
- supprimer et recréer la machine virtuelle en 2 clics, ou alors encore mieux, repartir d'un [clône de la machine virtuelle](http://www.6ma.fr/astuce/comment+cloner+une+machine+virtuelle+sur+virtualbox-329) à un état antérieur
- utiliser votre système d'exploitation hôte pour faire des recherches internet et trouver comment débloquer la situation.

Pour apprendre à manipuler VirtualBox (créer et lancer des machines virtuelles), je vous recommande de regarder [ce très bon tutoriel](https://www.youtube.com/watch?v=sB_5fqiysi4) de 13 mns.

Une fois appris, vous pouvez [télécharger l'ISO de Kubuntu](https://kubuntu.org/getkubuntu/) et créer une machine virtuelle avec Kubuntu. Vous pouvez suivre les deux parties suivantes pour installer et configurer Kubuntu et i3wm.

Une fois que vous saurez comment les installer et les configurer dans une machine virtuelle, vous pourrez le faire sur votre ordinateur.

## Kubuntu

[Kubuntu](https://kubuntu.org/) est une [distribution linux](https://fr.wikipedia.org/wiki/Distribution_Linux). Elle diffère d'Ubuntu par son environnement : elle utilise l'environnement KDE quand Ubuntu utilise l'environnement Gnome. L'environnement est ce qui fournit l'interface graphique du système d'exploitation ainsi que les utilitaires de base (launcher, explorateur de fichiers, visionneuse d'images...).

L'installation et la configuration de Kubuntu sont normalement très simples. Il n'y a aucune difficulté dans cette partie.

Vous pouvez regarder [ce petit tutoriel](https://www.youtube.com/watch?v=MfEehZFv5Y8&t=141s) de 3 mns pour l'installation. Pour la configuration, je n'ai rien fait de spécial. Je vous conseille juste de tester tout ce qui est possible : les paramètres, les utilitaires et leurs paramètres.

## i3wm

[i3wm](https://i3wm.org/) est un gestionnaire de fenêtre. Avant de continuer, je vous conseille très fortement de regarder les deux excellentes vidéos faites par [Grafikart](https://www.grafikart.fr/) pour comprendre :
- [ce qu'est i3wm](https://www.youtube.com/watch?v=oHbJK6r2Xwo)
- [comment configurer i3wm](https://www.youtube.com/watch?v=J07s8C8IvT4).

Ensuite, vous pouvez suivre la marche que je vous propose pour installer i3wm **dans KDE** et profiter de tous ses utilitaires. Je vous propose aussi ma configuration (la plus petite possible) pour profiter de toutes les fonctionnalités de KDE et de ses utilitaires en installant un minimum de paquets supplémentaires (seulement `feh` pour le fond d'écran et `fonts-font-awesome` pour les icônes dans le nom des workspaces).

Dans tous les autres tutoriaux proposés sur internet, il faut normalement installer de nombreux paquets supplémentaires, les configurer et il n'est pas forcément possible d'utiliser tous les utilitaires de l'environnement.

Voici donc comment je m'y prends :

1. Exécuter la commande `sudo apt install fonts-font-awesome feh i3`. \
Elle permet d'installer `fonts-font-awesome`, `feh` et `i3wm` avec la commande : \
2. Exécuter la commande `echo "export KDEWM=/usr/bin/i3" > ~/.config/plasma-workspace/env/set_window_manager.sh`. \
Elle crée un script dans le dossier `~/.config/plasma-workspace/env` (qui sera exécuté à chaque début de session) pour définir i3wm comme le gestionnaire de fenêtre.
3. Copier mes fichiers de configuration de i3 qui se trouvent dans le dépôt : `.config/i3/config` et `.config/i3status/config`.

**Attention** : avant de redémarrer votre session pour pouvoir utiliser i3wm, je vous conseille très fortement de :
1. lire les 2 fichiers de configuration, surtout `.config/i3/config`, dans lequel je définis des raccourcis claviers qui doivent être nécessairement connus sous peine de ne pouvoir rien faire.
2. adapater certaines parties de la configuration en fonction des fichiers et des applications que vous avez. Ces parties sont exactement :
    - L'image de fond (ligne 123). \
    Remplacez le fichier par l'endroit où se trouve votre image de fond.
    - Le nom des workspaces (lignes 65 à 74). \
    Définissez les workspaces que vous voulez en fonction de vos applications.
    - Les applications : raccourcis, workspace de lancement, lancement à l'ouverture de la session... (lignes 143 à 176).

Si quand vous démarrez votre session, vous n'avez pas internet. Faîtes `$mod+n` : le gestionnaire de réseau va s'ouvrir et vous pourrez vous connecter au réseau que vous souhaitez.
