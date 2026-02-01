sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Enters URL /spa in the address bar
    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    Server-->>Browser: HTML document (the SPA structure)

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>Browser: The CSS file

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    Server-->>Browser: The JavaScript file (spa.js)

    Note over Browser: Browser starts executing spa.js

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>Browser: [{ "content": "SPA is different", "date": "2026-02-01" }, ... ]

    Note over Browser: Browser executes the callback function to render notes locally