# Ejercicio 0.4: Nuevo diagrama de nota

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: El usuario escribe la nota y hace clic en "Save"

    browser->>server: POST [https://studies.cs.helsinki.fi/exampleapp/new_note](https://studies.cs.helsinki.fi/exampleapp/new_note)
    activate server
    server-->>browser: HTTP 302 Found (Redirect to /exampleapp/notes)
    deactivate server

    Note over browser: El navegador recarga la página debido a la redirección

    browser->>server: GET [https://studies.cs.helsinki.fi/exampleapp/notes](https://studies.cs.helsinki.fi/exampleapp/notes)
    activate server
    server-->>browser: El documento HTML
    deactivate server

    browser->>server: GET [https://studies.cs.helsinki.fi/exampleapp/main.css](https://studies.cs.helsinki.fi/exampleapp/main.css)
    activate server
    server-->>browser: El archivo CSS
    deactivate server

    browser->>server: GET [https://studies.cs.helsinki.fi/exampleapp/main.js](https://studies.cs.helsinki.fi/exampleapp/main.js)
    activate server
    server-->>browser: El archivo JavaScript
    deactivate server

    Note right of browser: El navegador ejecuta el código JS que solicita el JSON actualizado

    browser->>server: GET [https://studies.cs.helsinki.fi/exampleapp/data.json](https://studies.cs.helsinki.fi/exampleapp/data.json)
    activate server
    server-->>browser: El JSON con todas las notas (incluyendo la nueva)
    deactivate server

    Note right of browser: El navegador ejecuta la función callback y renderiza la lista de notas actualizada