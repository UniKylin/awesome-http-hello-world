# Hello World

## Python 
```python
from http.server import BaseHTTPRequestHandler, HTTPServer

class HelloHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-type', 'text/html')
        self.end_headers()
        self.wfile.write(b"<h2>>>> Hello Python...</h2>\n")

host = 'localhost'
port = 8000
server = HTTPServer((host, port), HelloHandler)

print(f">>> Server running at http://{host}:{port}")
server.serve_forever()
```

## Go
```go
package main

import (
    "net/http"
)

func helloHandler(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "text/html")
    w.Write([]byte("<h2>Hello Go...</h2>"))
}

func main() {
    http.HandleFunc("/", helloHandler)
    println("Server running at http://localhost:8000/")
    err := http.ListenAndServe(":8000", nil)
    if err != nil {
        panic(err)
    }
}
```

## Node.js
```javascript
const http = require('http');
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/html');
  res.end('<h2>Hello Node...</h2>\n');
});

const PORT=8000
server.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}/`);
});
```
