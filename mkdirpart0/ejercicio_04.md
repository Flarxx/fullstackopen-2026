sequenceDiagram
    participant browser
    participant server

    Note over browser: El usuario hace clic en "Save"


    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of server: El servidor guarda la nota en la base de datos
    server->>browser: HTTP 302 redirect /exampleapp/notes
    deactivate server

    browser->>server: Get https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server->>browser: HTML document
    deactivate server

    
    browser->>server: Get https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server->>browser: the css file
    deactivate server

    browser->>server: Get https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server->>browser: the js file
    deactivate server

    Note right of browser: El navegador ejecuta el JS que pide el JSON al servidor

    browser->>server: Get https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "test", "date": "2026-04-18" }, ... ]
    deactivate server

    Note right of browser: El navegador renderiza las notas incluyendo la nueva
  