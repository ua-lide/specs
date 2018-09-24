# API Fichier

## Récuperer tout les fichiers d'un projet

```
GET /api/projet/{idProject}/files
```

Return :
```json
{
    "data": [
        {
            "id": "1",
            "name": "file_name",
            "path": "/path/in/project",
            "created_at": "YYYY-MM-DD HH:mm:ss",
            "updated_at": "YYYY-MM-DD HH:mm:ss"
        },
        {
            "id": "3",
            "name": "file_name",
            "path": "/path/in/project",
            "created_at": "YYYY-MM-DD HH:mm:ss",
            "updated_at": "YYYY-MM-DD HH:mm:ss"
        },
        ...
    ]
}
```
Le contenu des fichiers n'est pas retourné, afin d'éviter des réponses trop lourdes.

## Récuperer un fichier

```
GET /api/projet/{idProject}/files/{idFile}
```
Return :
```json
{
    "data": {
        "id": "1",
        "name": "file_name",
        "path": "/path/in/project",
        "content": "content",
        "created_at": "YYYY-MM-DD HH:mm:ss",
        "updated_at": "YYYY-MM-DD HH:mm:ss"
    }
}
```
Paramètres de la requête :
* ``withContent`` : booléen (true/false/0/1), si vrai le contenu du fichier est retourné

## Ajouter un fichier à un projet
```
POST /api/projet/{idProject}/files
```
```json
{
    "data":{
        "name": "file_name",
        "path": "/path/in/project",
        "content": "content"
    }
}
```
Tout les champs sont requis. Le couple (`name`, `path`) est unique dans un projet.

Si la requête est valide, le fichier est créer et la response est la même que pour une requête GET. 

If the form is not valid, the response will be a 422 http code with a content like
Si le formulaire n'est pas valide, la reponse doit avoir un code htpp 422, avec un contenue tel :
```json
[
    {
        "field": "nom_champ_invalide",
        "error": "message decrivant l'erreur"
    },
    ...
]
```
## Update a file
```
PUT /api/projet/{idProject}/files
```
```json
{
    "data":{
        "name": "file_name",
        "path": "/path/in/project",
        "content": "content"
    }
}
```
Aucun champ n'est requis. Les champs manquant seront traité avec la valeur existante sur le serveur. Les champs présents ont les même règles de validations que pour la création.

Si la requête est valide, les données sont modifiées et la response est la même que pour une requête GET. 

Si le formulaire n'est pas valide, la reponse doit avoir un code htpp 422, avec un contenue tel :
```json
[
    {
        "field": "non_valid_field_name",
        "error": "message describing the error"
    },
    ...
]
```
## Supprimer un fichier

```
DELETE /api/projet/{idProject}/files
```

Reponse : code HTTP 200 (corps vide) si succès.

