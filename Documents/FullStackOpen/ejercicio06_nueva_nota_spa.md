# Ejercicio 0.6: Nueva nota en diagrama de aplicación de una sola página (SPA)

El ejercicio pide crear un diagrama que represente la situación en la que el usuario crea una nueva nota utilizando la versión de una sola página de la aplicación (`https://studies.cs.helsinki.fi/exampleapp/spa`).


```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: El usuario escribe una nueva nota en el campo de texto y hace clic en el botón "Save".

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: HTTP 201 Created (o similar, indicando éxito, y la nueva nota en formato JSON)
    deactivate server

    Note right of browser: El JavaScript de la SPA recibe la respuesta del servidor con la nueva nota.

    Note right of browser: El JavaScript de la SPA actualiza dinámicamente el estado de la aplicación y renderiza la nueva nota en la lista sin recargar la página.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON con todas las notas (incluyendo la nueva)
    deactivate server

    Note right of browser: (Opcional) El JavaScript de la SPA podría volver a solicitar todos los datos para asegurar la consistencia, o simplemente agregar la nueva nota al estado local si la respuesta POST ya la contenía.