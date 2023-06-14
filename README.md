
Bonjour,
Voici un petit projet de "containerisation" pour les personnes (féneantess comme moi) qui on besoin d'un environement de développement PHP avec une base des données relationnelle et qui ne veulent pas installer la pile LAMP, WAMP, XAMP ou MAMP sur sa machine tout en bénéficiant des avantage de cette "stack".

Prérequis :
    .- Installer "Docker" (voire Docker Desktop) sur sa machine
    .- Créer un compte sur DockerHub pour pouvoir rappatrier les images
    .- Créer un dossier sur sa machine pour contenir votre projet (éviter les espaces dans le nom du dossier)
        - Créer un dossier "app" et un dossier "db" dans votre dossier projet
    .- Copiez le fichier docker-compose.yml dans votre dossier projet (au même niveau que vos dossers "app" et "db")
 
Serveurs présents dans les containers de la pile :
    .- Apache
    .- MySQL
    .- PHP

Outil graphique pour la gestion des bases des données via navigateur web :
    .- PHP_MyAdmin (vous pouvez utiliser aussi la console pour saisir manuellement les commandes afin de vous entraîner).

Persistence des données :
    Les données du serveur sont conservées dans des "volumes" locaux sur la machine hôte (c'est à dire notre PC) et rendus visibles sur les containers Docker comme ci-dessous :
        .- Sur le PC hôte le site web est stocqué dans le dossier app "app" qui doit se trouver au même endroit que le fichier docker-compose.yml
        .- Dans le container Docker (c'est à dire le serveur http de la stack) le site web est hébergé dans le dossier /var/www.html

Création des containers à proprement parler :
    .- Ouvrez une invite de commande et positionnez vous dans votre dossier projet
    .- Exécutez la commande "docker-compose up -d"
    A M U S E Z      V O U S !

Acces au site web et/ou à la base des données :
    .- Pour accéder au site web avec un navigateur internet il faut taper l'adrese http://localhost
    .- Pour accéder aux bases de données via un navigateur web avec PHP-MyAdmin il faut taper l'adresse http://localhost:8080

Identifiants et mots de passe :
    Administration de la BDD :
        login : root
        password : example

    Utilisation de la BDD :
        login : myappuser
        password : myapppassword
