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

## Java
```java
import com.sun.net.httpserver.HttpServer;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpExchange;

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;

public class SimpleHttpServer {
	public static void main(String[] args) throws IOException {
		HttpServer server = HttpServer.create(new InetSocketAddress(8000), 0);

		server.createContext("/", exchange -> {
			exchange.getResponseHeaders().set("Content-Type", "text/html");
			String response = "<h2>Hi Java...</h2>\n";
			exchange.sendResponseHeaders(200, response.getBytes().length);
			try (OutputStream os = exchange.getResponseBody()) {
				os.write(response.getBytes());
			}
		});

		server.start();
		System.out.println("Server running at http://localhost:8000/");
	}
}
```
编译启动
```shell
javac SimpleHttpServer.java

java SimpleHttpServer
```

