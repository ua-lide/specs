# API Gestion Environnement

Cette API disponible sur le serveur Docker a pour but de gérer l'environnement lié à Docker en permettant d'utiliser les fonctionnalités de base de Docker et plus particulièrement
la création d'images soumises par les administrateurs. Cette API sera utilisée par le serveur WebSocket lors de ses intéractions avec Docker.

## lister les images disponibles
```
/env/images
```
Réponse Json :
```
{
  "data": {
      [
        {
          'tag' : 'tag1',
          'id' : 'id1',
          'label' : ['label1','label2']
        }
      ]
  }
}
```

## lister les conteneurs en fonctionnement
```
/env/containers
```
Réponse Json :
```
{
  "data": {
      [
        {
          'name' : 'name1',
          'id' : 'id1',
        }
      ]
  }
}
```

## ajouter une nouvelle image
```
POST /env/add/{tag}
```
Réponse Json :
```
{
  "data": {
      "message" => "building in progress"
  }
}
```

## supprimer une image
```
/env/delete/{image}
```
Réponse Json :
```
{
  "data": {
      "message" => "container started"
  }
}
```

## récupère les logs d'un container
```
/env/log/{id}
```
Réponse HTTP avec le contenu des logs du conteneur