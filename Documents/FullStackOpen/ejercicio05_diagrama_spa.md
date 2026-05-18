# Ejercicio 0.5: Diagrama de aplicación de una sola página (SPA)

El ejercicio pide crear un diagrama que describa la situación en la que el usuario accede a la versión de aplicación de una sola página (SPA) de la aplicación de notas en `https://studies.cs.helsinki.fi/exampleapp/spa`.


```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: El usuario navega a la URL https://studies.cs.helsinki.fi/exampleapp/spa

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: Documento HTML inicial (vacío o con un loader)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: Archivo CSS
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: Archivo JavaScript principal de la SPA
    deactivate server

    Note right of browser: El navegador comienza a ejecutar el JavaScript de la SPA, que se encarga de renderizar el contenido inicial y de solicitar los datos.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON con todas las notas
    deactivate server

    Note right of browser: El JavaScript de la SPA procesa los datos JSON y renderiza dinámicamente la lista de notas en la página.