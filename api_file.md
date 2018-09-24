# File API

## Get all existing files in a projet

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
            "path": "/path/in/project"
        },
        {
            "id": "3",
            "name": "file_name",
            "path": "/path/in/project"
        },
        ...
    ]
}
```
Content of files is not returned by this request to avoid a heavy response.

## Get a file

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
        "content": "content"
    }
}
```
Accepted parameters :
* ``withContent`` : boolean (true/false/0/1), if false file content will not be returned.

## Add a file to a project
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
All fields are required. The tuple (name, path) must be unique in the project.

If success, the response will have a http code 200, and the same content as a GET response.

If the form is not valid, the response will be a 422 http code with a content like
```json
[
    {
        "field": "non_valid_field_name",
        "error": "message describing the error"
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
No field is required. Missing field will be consired as if the value is not changed. Present fields have the same validation rules as in the create file request.

If success, the response will have a http code 200, and the same content as a GET response.

If the form is not valid, the response will be a 422 http code with a content like
```json
[
    {
        "field": "non_valid_field_name",
        "error": "message describing the error"
    },
    ...
]
```
