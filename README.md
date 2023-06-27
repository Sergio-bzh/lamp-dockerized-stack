# Containerisation Apache/MySQL/PHP (avec PHPMyAdmin) pour environement de devéloppement

Bonjour,

Voici un petit projet de "containerisation" pour les personnes (féneantess comme moi) qui ont besoin d'un environnement de développement PHP avec une base de données relationnelle et qui ne veulent pas installer la pile LAMP, MAMP, WAMP ou XAMP sur leurs machines tout en bénéficiant des avantages de cette "stack".

## Prérequis
- Installer "Docker" (voire Docker Desktop) sur sa machine
- Créer un compte sur DockerHub pour pouvoir rappatrier les images
- Créer un dossier sur sa machine pour contenir votre projet (éviter les espaces dans le nom du dossier)
  - Créer un dossier **"app"** et un dossier **"db"** dans votre dossier projet
- Copiez le fichier docker-compose.yml dans votre dossier projet (au même niveau que vos dossers **"app"** et **"db"**)
 
## Serveurs présents dans les containers de la pile
- Apache
- MySQL
- PHP

## Outil graphique pour la gestion des bases des données via navigateur web
- PHP_MyAdmin que vous pouvez utiliser via la console SQL intégrée pour saisir manuellement les commandes afin de vous entraîner.

## Persistence des données
Les données du serveur sont conservées dans des "volumes" locaux sur la machine hôte (c'est-à-dire notre PC) et rendus visibles sur les containers Docker comme ci-dessous :
- Sur le PC hôte, le site web est stocké dans le dossier **"app"** qui doit se trouver au même endroit que le fichier docker-compose.yml
- Dans le container Docker (c'est-à-dire le serveur HTTP de la stack), le site web est hébergé dans le dossier /var/www/html

## Création des containers à proprement parler
- Ouvrez une invite de commande sur votre machine et positionnez-vous dans votre dossier projet
- Exécutez la commande "docker-compose up -d"
- A M U S E Z      V O U S !

## Accès au site web et/ou à la base des données
- Pour accéder au site web avec un navigateur internet, il faut taper l'adresse http://localhost
- Pour accéder aux bases de données via un navigateur web avec PHP-MyAdmin, il faut taper l'adresse http://localhost:8080

## Identifiants et mots de passe
Administration de la BDD :
- Login : root
- Password : mot2passeRoot

Utilisation de la BDD :
- Login : monutilisateur
- Password : mot2passUser

## NOTA IMPORTANTE

**ATTENTION !!**

Sachez qu'il n'est pas considéré comme une bonne pratique du point de vue de la sécurité de mettre en clair les informations de connexion dans le fichier docker-compose.yml.

Il est préférable de renseigner ces informations dans un fichier d'environnement séparé et de faire référence aux variables d'environnement présentes dans le fichier ".env" à l'intérieur du fichier docker-compose.yml.

*J'ai mis cette information en clair dans le fichier YAML pour faciliter la compréhension et la lecture aux personnes qui n'ont pas encore eu contact avec Docker.*

Le fichier docker-compose.yml peut être refactorisé en faisant mention du fichier .env au lieu de nommer les variables, mais cette démarche le rend plus difficile à comprendre lorsqu'on débute sur Docker.

**/ATTENTION !!**

## = = = = = = = = = PARTICULARITÉS QUE J'AI RENCONTRÉES SELON LE SYSTÈME UTILISÉ = = = = = = = = =

## Sur MAC :
    .- Un serveur http est installé par défaut sur le système :
        - Pour savoir s'il tourne et connaître son port :
            sudo launchctl list | grep 'apache'
                    ou
            sudo apachectl status

        - Pour arrêter le service :
            sudo apachectl stop

    .- Si (comme moi) vous aviez installé MySQL en local sur votre Mac pour apprendre le SQL et ne voulez pas le désinstaller :
        - Pour savoir si le service MySQL est en cours d'exécution et connaître son port :
            sudo launchctl list | grep 'mysql'
        - Pour l'arrêter en fonction de votre système et selon vos préférences :
            sudo mysqladmin stop
                    ou
            sudo mysqladmin shutdown
                    ou
            sudo /usr/local/mysql/support-files/mysql.server stop

## Sur GNU/Linux :
    AUCUNE PARTICULARITÉ TROUVÉE

## Sur Windows(11) :
    AUCUNE PARTICULARITÉ TROUVÉE
