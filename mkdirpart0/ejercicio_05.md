sequenceDiagram
    participant browser
    participant server

    
    Note right of browser: El servidor responde con 200 OK porque  entrega los archivos directamente.
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML DOCUMENT
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser:  THE CSS FILE
    deactivate server


    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser:  the JavaScript file
    deactivate server

    Note right of browser: El navegador ejecuta el JS que dispara la petición XHR para el JSON

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser:  [{ "content": "nota spa test 1", "date": "2026-04-23" }, ... ]
    deactivate server

    Note right of browser: El JS procesa los datos y crea la lista de notas en el DOM

    