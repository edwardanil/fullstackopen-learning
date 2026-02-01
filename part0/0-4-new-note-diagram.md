sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Types note content into the text field
    User->>Browser: Clicks the "Save" button

    Note over Browser: Browser captures the input data

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note right of Browser: Data: { "note": "User's text" }

    Note over Server: Server saves the new note to the database/array

    Server-->>Browser: HTTP status code 302 (URL redirect to /notes)
    
    Note over Browser: The browser reloads the Notes page

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    Server-->>Browser: HTML document (the page structure)

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>Browser: the css file

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Server-->>Browser: the JavaScript file

    Note over Browser: Browser starts executing the JavaScript code

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>Browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]

    Note over Browser: Browser executes the callback function that renders the notes