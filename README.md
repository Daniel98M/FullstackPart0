# FullstackPart0

Parte 0 del curso virtual Fullstack

0.4. Nuevo diagrama de nota

```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    user->>browser: Escribe una nueva nota y hace clic en Save
    browser->>server: POST /new_note
    activate server
    server-->>browser: 302 Redirect (la nota fue guardada)
    deactivate server

    browser->>server: GET /notes
    activate server
    server-->>browser: 304 Not Modified
    deactivate server

    browser->>server: GET /main.js
    activate server
    server-->>browser: 304 Not Modified
    deactivate server

    browser->>server: GET /data.json
    activate server
    server-->>browser: 200 OK (datos JSON incluyendo la nueva nota)
    deactivate server

    Note right of browser: El navegador actualiza la página para mostrar la nueva nota
```

0.5 Diagrama de aplicación de una sola página

```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    user->>browser: Accede a /spa
    browser->>server: GET /spa
    activate server
    server-->>browser: 304 Not Modified (usa versión en caché)
    deactivate server

    browser->>server: GET /main.css
    activate server
    server-->>browser: 304 Not Modified (usa versión en caché)
    deactivate server

    browser->>server: GET /spa.js
    activate server
    server-->>browser: 304 Not Modified (usa versión en caché)
    deactivate server

    browser->>server: GET /data.json
    activate server
    server-->>browser: 200 OK (datos JSON)
    deactivate server

    Note right of browser: El navegador renderiza las notas usando los datos JSON
```

0.6 Nueva nota en diagrama de aplicación de una sola pagina

```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    user->>browser: Escribe una nueva nota y presiona "Guardar"
    browser->>server: POST /new_note_spa (nueva nota en JSON)
    activate server
    server-->>browser: 201 Created (nota creada)
    deactivate server

    Note right of browser: El navegador actualiza la lista de notas localmente sin recargar la página
```
