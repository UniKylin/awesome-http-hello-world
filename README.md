# Hello World

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
    println("Server running at http://localhost:8080/")
    err := http.ListenAndServe(":8080", nil)
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

const PORT=3000
server.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}/`);
});
```
