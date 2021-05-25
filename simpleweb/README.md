# Simple web app
Created using just node.js to run a web app. To build this app, use the following
code:
```bash
docker build -t <username>/simpleweb .
```
To run the app,
```bash
docker run -p 8080:8080 <username>/simpleweb
```
The port number 8080 from the client (left side of colon) can be specified to 
any other ports, but the port number 8080 from the container (right side of colon)
must be 8080, unless specified otherwise on index.js. Try opening up your browser
and type in __localhost:8080__ or __192.168.99.100:8080__ to test whether the
app has been success after running the container.