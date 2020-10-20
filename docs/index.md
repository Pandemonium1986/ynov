# Ynov Docker Lab 2020

Le but de cet examen est de tester vos connaissances sur les concepts que nous avons vu autour de docker et la containérisation.  
Vous avez 2 heures pour réaliser l’examen.  
La correction est réalisée via une procédure automatique. Aussi soyez **rigoureux** sur le respect des consignes et le nommage des différents objets que vous manipulerez tout au long de l’examen.

Quelques remarques général

-   L’ensemble de l’examen doit se faire sur la machine <span style="color:orange">docker</span>. La machine <span style="color:red">operator</span> n’est là que pour faire rebond.
-   L’utilisateur de la machine <span style="color:orange">docker</span> est "docker". Il est sudoer et vous pouvez installer tous les outils nécessaires que vous souhaitez.

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

3.  Créer un répertoire exo0 qui contient un fichier nommé init.txt dans lequel vous écrivez la date du jour ainsi que votre nom prénom.

```sh
mkdir -p ~/exo0 && touch ~/exo0/init.txt && echo "2020-10-22 Maffait Michael"
```

## Installation de Docker

## Exercice 1

1.  Connectez-vous en ssh sur la machine <span style="color:red">ansible</span> du lab
2.  Effectuer un ping sur les machines <span style="color:orange">haproxy </span><span style="color:blue">blue </span><span style="color:green">green</span>

## Récupération d'images

### Exercice 2

1.  Installer ansible avec pip (--user) sur la machine <span style="color:red">ansible</span>
2.  Contrôler l'installation en affichant la version d'ansible

## Instanciation d'une image

### Exercice 3

1.  Créer une clef ssh pour l'utilisateur "prénom" sur la machine <span style="color:red">ansible</span>
2.  Copier la clef publique (ssh-copy-id) de l'utilisateur "prénom" sur les machines <span style="color:orange">haproxy </span><span style="color:blue">blue </span><span style="color:green">green </span> depuis la machine <span style="color:red">ansible</span>
3.  Vérifier le bon déploiement des clefs en vous connectant sur les machines <span style="color:orange">haproxy </span><span style="color:blue">blue </span><span style="color:green">green</span> depuis la machine <span style="color:red">ansible</span>

## Ad-Hoc

### Exercice 4

1.  Créer un fichier "inventory" sur la machine <span style="color:red">ansible</span> qui contient un groupe [cd] avec la machine <span style="color:blue">blue </span> et <span style="color:green">green </span> et un goupe [lb] avec la machine <span style="color:orange">haproxy </span>
2.  Utiliser la commande ansible ad-hoc et le module ping sur votre inventaire
3.  Observer le résultat
4.  Utiliser la commande ansible ad-hoc et le module yum pour installer vim
5.  Observer le résultat

### Exercice 4

6.  Utiliser la même commande avec une élévation de privilège
7.  Observer le résultat
8.  Assurez-vous de l'idempotence de la commande précédante
9.  Observer le résultat

## Playbook

### Exercice 5

1.  Écrire un playbook qui installe haproxy sur les machines du groupe [lb] et apache sur la machine du groupe [cd]
2.  Exécuter le playbook
3.  Observer le résultat
4.  Assurez-vous de l'idempotence du playbook

### Exercice 5

5.  Modifier le playbook pour activer les services
6.  Exécuter le playbook
7.  Observer le résultat
8.  Assurez-vous une dernière fois de l'idempotence du playbook
9.  Tester les services  
    **<span style="color:orange">!!!!!!(Me Demander pour HA-PROXY)!!!!!!</span>**
10. Observer le résultat

## HAPROXY

### Exercice 6

1.  Utiliser le module template pour configurer HAProxy avec le fichier fourni  
    **<span style="color:orange">!!!!!!(Me Demander le fichier)!!!!!!</span>**
2.  Exécuter le playbook
3.  Observer le résultat
4.  Tester le service
5.  Observer le résultat

### Exercice 6

6.  Ajouter le redémarrage du service et tester l'idempotence
7.  Observer le résultat et rejouer aussitôt l'idempotence
8.  Ajouter un hanlder pour redémarrer le service
9.  Observer le résultat

## Blue Green

### Exercice 7

1.  Modifier le fichier d'index.html sur le machines <span style="color:blue">blue </span> et <span style="color:green">green </span> via la commande sed suivante :


        sudo vim /usr/share/httpd/noindex/index.html
        # Blue
        :%s/Testing 123../Blue/g
        # Green
        :%s/Testing 123../Green/g

2.  Tester le service haproxy et observer
3.  Modifier la conf de la machine HAProxy pour pointer sur <span style="color:blue">blue </span> depuis la machine <span style="color:red">ansible</span>
4.  Exécuter le playbook
5.  Observer le résultat et assurez-vous de l'idempotence
6.  Tester de nouveau le service HAProxy

## Continous Delivery

### Exercice 8

1.  Utilisez le module copy pour copier la page "Yellow" fourni sur la machine <span style="color:green">green</span> depuis la machine <span style="color:red">ansible</span> en utilisant un flag booleen
2.  Modifier le fichier d'inventaire pour prendre en compte le flag `bg_flag="false"` sur <span style="color:blue">blue</span> et `bg_flag="true"` sur <span style="color:green">green</span>
3.  Exécuter le playbook
4.  Observer le résultat
5.  Tester le service sur <span style="color:green">green</span>
6.  Modifier la conf de HAProxy pour passer de <span style="color:blue">blue</span> à <span style="color:green">green</span>
7.  Exécuter le playbook et testé l'url HAProxy
8.  Observer le résultat

## Push Button

### Exercice 9

1.  Utiliser des variables de prompt pour déployer sur <span style="color:blue">blue</span> et passer sur <span style="color:green">green</span>
2.  Modifier le fichier de configuration d'haproxy en conséquence
3.  Exécuter le playbook
4.  Observer le résultat
