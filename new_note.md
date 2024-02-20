```mermaid
sequenceDiagram
    participant browser
    participant server

browser->>server:POST https://studies.cs.helsinki.fi/exampleapp/new_note
Note right of browser:data is sended by submiting form with attribute action='Url adress' and method ='POST'
activate server
server-->>browser:Redirect 302 status code send new location:/exampleapp/notes
deactivate server

Note right of browser:browser goes to new location, that causes page reload, means 3 more get requests for HTM, CSS,JS files for new Notes Page to render
Note left of server: server push body of Post request in to the notes, but not saving data in ?data base?
browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
activate server
server-->>browser: here is your HTML file for NOtes page
deactivate server
Note right of browser: After HtML browser goes to link css line, and sends new request

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
server-->>browser: here is file with css rules for Notes Page

Note right of browser: new line with script of main.js, so browser request this file from server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
activate server
server-->>browser: here is JS script for you to work on
deactivate server
Note right of browser: browser executes code that as to fetch data from the browser by making another request

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
activate server
server-->>browser: here is all data with updates request
deactivate server
Note right of browser: Browser executes callback function that doing manipulation with DOM by updating notes with new data




