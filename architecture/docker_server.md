# Architecture Serveur Docker

## Technologies

* **PHP 7.2**
* API : Framework **Symfony**
* Utilise la même base de données que le serveur web : **MariaDB**
* Serveur Websocket : [**Ratchet**](http://socketo.me/), intégré dans Symfony.

## Authentification

L'authentification des utilisateur par [Oauth2](https://oauth.net/2/). Le token d'authentification est généré par le serveur web, et stocké dans la base de donnée commune.

## API

Ce serveur permet la gestion des projets utilisateurs. Pour cela, il met à disposition une API permettant d'accèder aux projet et fichiers.
* [Voir la description de l'API pour les projets](../api/api_project.md)
* [Voir la description de l'API pour les fichiers](../api/api_file.md)

## Execution des programmes des utilisateurs

Les programmes des utilisateurs sont compilés et exécutés dans des conteneurs docker. La communication s'effectue par WebSocket
* [Voir le protocole websocket de l'application](../api/websocket.md)