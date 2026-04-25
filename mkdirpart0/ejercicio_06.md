sequenceDiagram
    participant browser
    participant server

    Note right of browser: El usuario hace clic en "Save"
    Note right of browser: El JS captura el evento, añade la nota a la lista local y limpia el input

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note left of server: El payload contiene: {"content": "prueba", "date": "2026-04-24..."}
    
    server-->>browser: {"message":"note created"} (Status 201 Created)
    deactivate server

    Note right of browser: Como el JS ya actualizó la página localmente, no hace falta recargar nada