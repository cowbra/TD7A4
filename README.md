# TD7A4 - Projet Docker-Compose &Git-githubpour un serveur Minecraft
## 🌟 Objectifs
> Ce projet va exécuter un serveur Minecraft avec une base de données MySQL sous Docker via un doker_compose. Le serveur Minecraft est exécuté dans un conteneur Docker avec une image personnalisée "marctv/ minecraft-papermc-server:latest" (typer de serveur qui permet de faire de l'asynchrone). une base de données MySQL est également exécutée dans un conteneur Docker.

## 👷 Installation
### Prérequis
1. Docker et Docker Compose doivent être installés sur votre machine.

2. Étapes
- Clonez ce dépôt Git sur votre machine locale.
- Créez un fichier `.env` à la racine du projet et définissez les variables d'environnement suivantes :
> ```shell
> MYSQL_ROOT_PASSWORD=<votre_mot_de_passe>
> MYSQL_DATABASE=<nom_de_votre_base_de_données>
> MYSQL_USER=<votre_user>
> MYSQL_PASSWORD=<votre_mot_de_passe>
> ```
- Ouvrez un terminal dans le dossier du projet et exécutez la commande suivante :
> ```shell
> docker-compose up -d
> ```
- Attendez que les conteneurs soient démarrés et que le serveur Minecraft soit entièrement configuré, cela peut prendre quelques minutes (Connexion à la BDD, chargement des mondes,plugins,...).

- Connectez-vous au serveur Minecraft à l'adresse `localhost:25565``. Vous pouvez également accéder à la carte du serveur à l'adresse localhost:8123 (générée par le plugin Dynmap).
## 🔨 Configuration
### Base de données MySQL
La base de données MySQL est configurée à l'aide des variables d'environnement définies dans le fichier `.env`. Vous pouvez modifier ces valeurs pour adapter la configuration à vos besoins.

### Serveur Minecraft
1. Le serveur Minecraft est configuré via les variables d'environnement définies dans le fichier docker-compose.yml. La variable `MEMORYSIZE` définit la quantité de mémoire allouée au serveur Minecraft. Vous pouvez modifier cette valeur en fonction des besoins de votre serveur (attention à ne pas dépasser 70% de la RAM totale utilisable par le conteneur pour prendre en compte les dépendances du serveur minecraft sous JAVA).

2. Le serveur Minecraft est automatiquement redémarré en cas de panne grâce à l'option restart: always définie dans le fichier docker-compose.yml.

3. Pour mettre à jour le serveur Minecraft, vous pouvez  utiliser l'outil Watchtower pour mettre à jour automatiquement le conteneur du serveur Minecraft en fonction des nouvelles versions de l'image publié sur le Registry officiel (non recommendé pour les versions de jeu des clients, la compatibilité des plugins,...).

### Gestion de la base de données
La base de données MySQL est configurée pour stocker ses données sur votre machine locale dans le dossier ./mariadb/minecraft. Vous pouvez modifier cet emplacement en modifiant la section volumes du fichier `docker-compose.yml` (bind mount pour ne pas perdre nos données). 

## Conclusion
Ce projet Docker Compose fournit une configuration simple pour exécuter un serveur Minecraft avec une base de données MySQL. Vous pouvez facilement le personnaliser en modifiant les variables d'environnement et les options de configuration dans le fichier docker-compose.yml.