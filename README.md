# FullstackPart0

Parte 0 del curso virtual Fullstack

0.4. Diagrama mermaid del flujo de la página de ejemplo

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
