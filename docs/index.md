# Ynov Docker Lab 2020

Le but de cet examen est de tester vos connaissances sur les concepts que nous avons vu autour de docker et la containérisation.  
Vous avez 2 heures pour réaliser l’examen.  
La correction est réalisée via une procédure automatique. Aussi soyez **rigoureux** sur le respect des consignes et le nommage des différents objets que vous manipulerez tout au long de l’examen.

Quelques remarques générales:

-   L’ensemble de l’examen doit se faire sur la machine <span style="color:orange">docker</span>. La machine <span style="color:red">operator</span> n’est là que pour faire rebond.
-   L’utilisateur de la machine <span style="color:orange">docker</span> est "docker". Il est sudoer et vous pouvez installer tous les outils nécessaires que vous souhaitez.
-   Sauf contre indication dans l’énoncer de l’exercice tous les container devront :
    -   Être détaché du prompt.
    -   Être mappé sur un port **aléatoire**.
    -   Ne **pas être détruit** en cas de **stop**.
-   Les répertoires sont à créer dans le $HOME de l'utilisateur **docker**.
-   Le container est une debian 10, le répertoire par défault de nginx est le suivant `/usr/share/nginx/html`.
-   Au sein du container le fichier `index` s’appellera toujours `index.html`.

Bon courage

## Vérification des pré-requis

1.  Connectez-vous à la machine <span style="color:red">operator</span>

```sh
ssh VOTRE_LOGIN@85.158.8.48 -p 443
```

2.  Depuis la machine <span style="color:red">operator</span> connectez-vous à votre machine <span style="color:orange">docker</span>

```sh
ssh docker@VOTRE_LOGIN-docker-vm
```

3.  Créer un répertoire `exo0` qui contient un fichier nommé `init.txt` dans lequel vous écrivez la date du jour ainsi que votre nom prénom.

```sh
mkdir -p ~/exo0 && touch ~/exo0/init.txt && echo "2020-10-22 Maffait Michael" > ~/exo0/init.txt
```

4.  Créer un répertoire `ressources` qui contiendra l'ensemble des ressources nécessaire à l'examen.

```sh
mkdir -p ~/ressources
```

## Installation de Docker

### Exercice 1

1.  Installer Docker pour une CentOs en vous appuyant sur la documentation officiel disponible à l'adresse [Doc Docker](https://docs.docker.com/).
    -   L'utilisateur **docker** à les droits suffisant pour effectuer toutes installations sur la mahcine <span style="color:orange">docker</span>.
    -   Ne vous occupez pas des **Optionnal**
    -   **Démarrer** et **Activer** le service
    -   L'utilisateur **docker** est déjà dans le groupe docker (pas besoin de sudo pour vos commande docker).  
2.  Contrôler l'installation en affichant la version de docker et en effectuant un run de l'image `hello-world`.
3.  Créer un répertoire `exo1` qui contient un fichier nommé `docker.txt` dans lequel vous écrivez la version de docker.

```sh
mkdir -p ~/exo1 && touch ~/exo1/docker.txt && docker --version > ~/exo1/docker.txt
```

## Récupération d'images

### Exercice 2

1.  Depuis le hub de docker récupérer la version de l'image Nginx 1.19.3.
2.  Créer un répertoire `exo2` qui contient un fichier nommé `nginx.txt` dans lequel vous écrivez l'id de l'image nginx (préfixé par sha:256).

## Création d'un container

### Exercice 3

1.  Créer un container depuis l'image nginx 1.19.3:
    -   Le container se nomme `ynov-nginx-exo345`.
    -   Il suit les règles cités plus haut :up:.
2.  Récupérer le port associé.
3.  Faite un test local pour vérifier la bonne exécution de votre container.

```sh
curl http://localhost:VOTRE_PORT
```

4.  Créer un répertoire `exo3` qui contient un fichier nommé `run.txt` dans lequel vous écrivez la commande que vous avez exécutée pour instancier le container.
5.  Dans le répertoire `exo3` créer fichier nommé `port.txt` dans lequel vous écrivez le port Host mappé par votre container.

## Modification d'un container

### Exercice 4

1.  Modifier le contenu de la page container `ynov-nginx-exo345`.
    -   Utiliser le fichier index.html présent à l'adrsse suivante [index-copy.html](./ressources/index-copy.html).
2.  Faite un test local pour vérifier la bonne modification de votre contenu.
3.  Créer un répertoire `exo4` qui contient un fichier nommé `copy.txt` dans lequel vous écrivez la commande que vous avez exécutée pour modifier le contenu du container.

## Création d'une image

### Exercice 5

1.  Depuis le container `ynov-nginx-exo345`, créé une image  que vous allez nommer `ynov-nginx-commit`.
2.  Tagguer la en version 1.0
3.  Créer un container depuis l'image `ynov-nginx-commit` 1.0:
    -   Le container se nomme `ynov-nginx-exo5`.
    -   Il suit les règles cités plus haut :up:.
4.  Récupérer le port associé.
5.  Modifier le contenu de la page container `ynov-nginx-exo5`
    -   Utiliser le fichier index.html présent à l'adresse suivante [index-image.html](./ressources/index-image.html)
6.  Faite un test local pour vérifier la bonne exécution de votre container.
7.  Créer un répertoire `exo5` qui contient un fichier nommé `commit.txt` dans lequel vous écrivez la commande que vous avez exécutée pour créer le container

### Exercice 6

1.  Créer un répertoire `exo6` qui contient un fichier nommé `Dockerfile`.
2.  Le fichier Dockerfile doit:
    -   Construire une image depuis l'image nginx 1.19.3.
    -   Copier le fichier suivant [index-dockerfile](./ressources/index-dockerfile.html) dans le repertoire `/usr/share/nginx/html`.
3.  Construiser l'image et nommé la`ynov-nginx-dockerfile`.
4.  Taggué là en 1.0
5.  Créer un container depuis l'image ynov-nginx-dockerfile 1.0:
    -   Le container se nomme `ynov-nginx-exo6`.
    -   Il suit les règles cités plus haut :up:.
6.  Récupérer le port associé.
7.  Faite un test local pour vérifier la bonne exécution de votre container.
8.  Dans le répertoire `exo6` créer fichier nommé `dockerfile.txt` dans lequel vous écrivez la commande pour instancier le container `ynov-nginx-exo6`.

## Volumes

### Exercice 7

1.  Créer un container depuis l'image `ynov-nginx-dockerfile`:
    -   Le container se nomme `ynov-nginx-exo7`.
    -   Il suit les règles cités plus haut :up:.
    -   Vous allez devoir utiliser un bind-mount pour monter le dossier suivant [ressources/html](./ressources/html/) à la place du répertoire `/usr/share/nginx/html`
    -   Le répertoire doit être présent sur la machine <span style="color:orange">docker</span> dans le dossier ressources.
2.  Récupérer le port associé.
3.  Faite un test local pour vérifier la bonne exécution de votre container.
4.  Modifier dans le répertoire `~/ressources/html/` le fichier `index.html` afin d'afficher la date du jour après _Exo7 Volumes Bind Mount_.
5.  Re-faite un test local pour vérifier la bonne exécution de votre container et l'affichage de votre page.
6.  Créer un répertoire `exo7` qui contient un fichier nommé `bind.txt` dans lequel vous écrivez la commande que vous avez exécuter pour bind mounter le volume dans le container.

### Exercice 8

1.  Créer un volume nommé `ynov-nginx-volumes`.
2.  Créer un container depuis l'image `ynov-nginx-dockerfile`:
    -   Le container se nomme `ynov-nginx-exo81`.
    -   Vous allez devoir y monter le volume `ynov-nginx-volumes` dans le repertoire `/usr/share/nginx/html`
3.  Copier le fichier [index-volume](./ressources/index-volume.html) dans le volume `ynov-nginx-volumes`.
4.  Créer un container depuis l'image `ynov-nginx-dockerfile`:
    -   Le container se nomme `ynov-nginx-exo82`.
    -   Vous allez devoir y monter le volume `ynov-nginx-volumes` dans le repertoire `/usr/share/nginx/html`
5.  Récupérer les ports associés à vos container.
6.  Vérifier que vos deux container affiche bien la même page.
7.  Créer un répertoire `exo8` qui contient un fichier nommé `mount.txt` dans lequel vous écrivez la commande que vous avez exécuter pour monter le volume dans les deux containers.

## Network

### Exercice 9

1.  Créer un network bridge nommé

-   Nommé le ynov-nginx-network.

2.  Créer deux container

-   ynov-net-01
-   ynov-net-02
-   Ils doivent avoir le host qui s'appele comme leur nom.

3.  Pinguer les  container entre eux (si besoin installer ping depuis avec la commande)

4.  

## All In One

### Exercice 10

1.  Créer un volume nommé `ynov-nginx-blue`.
2.  Créer un volume nommé `ynov-nginx-green`.
3.  Lancer un container traefik qui publie le port 80.
4.  Lancer un container ynov blue avec comme volume blue.
5.  Lancer un container ynov green avec comme volume Green.
6.  Copier le fichier blue dans le volume blue.
7.  Copier le fichier green dans le volume green.
8.  Tester depuis l'ip public.
