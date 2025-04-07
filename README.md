# Hello World

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
