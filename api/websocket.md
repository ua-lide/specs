# [WIP] Protocole Websocket

## Initialisation de la connexion

## Lancement programme

Afin de lancer le programme, le client envoie un message de la forme suivante :
```json
{
    "type": "execute",
    "data": {
        "compile_options": "", //Options de compilation
        "launch_options": "", //Arguments donnés au programme à l'éxecution
    }
}
```

## Envoi d'une entrée

Client -> Serveur

```json
{
    "type": "input",
    "data": {
        "input": "input utilisateur"
    }
}
```

## Envoi sortie

Serveur -> Client
```json
{
    "type": "stdout", //ou stderr
    "data": {
        "output": "output programme",        
    }
}
```

## Fin du programme

À la fin de l'éxécution, le serveur envoie un message de la forme
```json
{
    "type": "end"
    "data": {
        "return": "0" //Code de retour, pour savoir si le programme s'est éxecuté jusqu'à la fin ou a été interrompu (timeout, depassement mémoire...)
    }
}
```

## Forcer l'arrêt

Afin de forcer l'arrêt, le client peut envoyer le message : 
```json
{
    "type": "force_stop",
    "data": {}
}
```
## Fermeture de la connexion

TODO