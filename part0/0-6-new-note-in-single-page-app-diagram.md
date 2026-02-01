sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Types note and clicks "Save"
    
    Note over Browser: JavaScript intercepts the form submit event
    Note over Browser: JS adds new note to the local list
    Note over Browser: JS re-renders the note list on the page immediately

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note right of Browser: Content-Type: application/json<br/>{ "content": "SPA is fast", "date": "2026-02-01" }

    Note over Server: Server saves the new note to the database

    Server-->>Browser: HTTP 201 Created
    Note over Browser: The browser stays on the same page; no reload occurs