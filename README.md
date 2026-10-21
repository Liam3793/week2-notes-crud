
# Week 2 Notes CRUD API

## DESCRIPTION

A simple CRUD based API for managing notes while using a database.

Note: CRUD = Create/Read/Update/Delete

## TECHNOLOGIES USED:

- FastAPI for API
- SQLite for the database
- Uvicorn for running the API

## INSTRUCTIONS

### Create the Virtual Environment

**MacOS/Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows PowerShell:**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

### Install Packages

Inside terminal command: `python3 -m pip install -r requirements.txt`

### Activate the API

Inside terminal command: `uvicorn main:app --reload`

API URL: [http://127.0.0.1:8000](http://127.0.0.1:8000)

FastAPI Docs: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

## TESTING

Testing endpoints can be done via FastAPI Docs or Postman

### STATUS CODE DEFINITIONS:

| Status Code | Meaning |
|---------------------------|----------------------------------------------------------------|
| 200 OK | The request was successful. |
| 201 Created | A new note was created successfully. |
| 404 Not Found | The requested note could not be found. |
| 422 Unprocessable Content | The request contains invalid data or is missing required information. |

### Test the API is Activated

Procedure: `GET /`

Expected Response:  
Status Code: `200`

### Get all notes:

Procedure: `GET /notes`

Expected Response:  
Status Code: `200 OK`

### Create a note:

Procedure: `POST /notes`

JSON Body:

```json
{
    "title": "Postman note",
    "text" : "i created this note using Postman."
}
```

Expected Response:  
Status Code: `201 Created`

### Get one note:

Procedure: `GET /notes/{note_id}`

Expected Response: `200 OK`

### Update a note:

Procedure: `PATCH /notes/{note_id}`

JSON Body:

```json
{
    "title": "Updated from Postman"
}
```

Expected Response: `200 OK`

NB: This allows one to update selected portions (such as the title) whilst keeping the original text unchanged.

### Delete a note:

Procedure: `DELETE /notes/{note_id}`

Expected Response: `200 OK`

Response:

```json
{
    "message": "Note deleted"
}
```

### Checking for a deleted note:

Procedure: `GET /notes/{note_id}`

Expected Response: `404 Not Found`

### Testing a missing note:

Procedure: `PATCH /notes/9999` or `DELETE /notes/9999`

Expected Response: `404 Not Found`

### Test missing required information:

PROCEDURE: `POST /notes`

JSON Body:

```json
{
    "title": "Incomplete note"
}
```

Expected Response: `422 Unprocessable Content`

NB: When the API is stopped and restarted, the notes remain saved in the SQLite database.
