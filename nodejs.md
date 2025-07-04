
# Streams in nodejs
Streams in Node.js are a way to handle reading or writing data efficiently, especially for large files or real-time data processing. Streams work with chunks of data rather than loading everything into memory, making them memory-efficient and fast.

Types of Streams in Node.js:
Readable Streams – Used for reading data.

Writable Streams – Used for writing data.

Duplex Streams – Can read and write data (e.g., sockets).

Transform Streams – A type of Duplex stream that can modify data as it passes through (e.g., compression, encryption).

1. Readable Stream
Example: Reading a file using a stream.

javascript
Copy
Edit
const fs = require('fs');

const readableStream = fs.createReadStream('input.txt', { encoding: 'utf8' });

readableStream.on('data', (chunk) => {
    console.log('Received chunk:', chunk);
});

readableStream.on('end', () => {
    console.log('Finished reading');
});

2. Writable Stream
Example: Writing to a file using a stream.

javascript
Copy
Edit
const fs = require('fs');

const writableStream = fs.createWriteStream('output.txt');

writableStream.write('Hello, this is a writable stream!\n');
writableStream.end('Writing completed.');

writableStream.on('finish', () => {
    console.log('Finished writing to file');
});

3. Piping Readable to Writable
Example: Copying a file efficiently using a pipe.

javascript
Copy
Edit
const fs = require('fs');

const readableStream = fs.createReadStream('input.txt');
const writableStream = fs.createWriteStream('output.txt');

readableStream.pipe(writableStream);

writableStream.on('finish', () => {
    console.log('File copied successfully');
});

4. Transform Stream (Compression)
Example: Compressing a file using zlib.

javascript
Copy
Edit
const fs = require('fs');
const zlib = require('zlib');

const gzip = zlib.createGzip();
const readableStream = fs.createReadStream('input.txt');
const writableStream = fs.createWriteStream('input.txt.gz');

readableStream.pipe(gzip).pipe(writableStream);

writableStream.on('finish', () => {
    console.log('File compressed successfully');
});
When to Use Streams?
Processing large files (e.g., reading/writing logs).

Streaming real-time data (e.g., audio/video).

Efficient handling of network requests (e.g., sending files over HTTP).

Would you like an example of using streams in an HTTP server or something else? 🚀


# Rate limiting in nodejs

***You can implement rate limiting in an Express application using the express-rate-limit middleware. This helps prevent abuse and protects your API from excessive requests by setting a limit on the number of requests a client can make within a specified time frame***

1. Apply Rate Limiting in Your Express App
npm install express-rate-limit


const express = require("express");
const rateLimit = require("express-rate-limit");

const app = express();

// Define the rate limiter middleware
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // Limit each IP to 100 requests per windowMs
  message: { error: "Too many requests, please try again later." },
  standardHeaders: true, // Return rate limit info in headers
  legacyHeaders: false, // Disable X-RateLimit-* headers
});

// Apply the rate limiter to all requests
app.use(limiter);

app.get("/", (req, res) => {
  res.send("Welcome to the Express API");
});

const PORT = 5000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});

2. Apply Rate Limiting to Specific Routes

const loginLimiter = rateLimit({
  windowMs: 5 * 60 * 1000, // 5 minutes
  max: 5, // Limit each IP to 5 login attempts per window
  message: { error: "Too many login attempts, please try again later." },
});

app.post("/login", loginLimiter, (req, res) => {
  res.send("Login route");
});


**Advance Nodejs concepts**

Here are some advanced Node.js concepts that are useful for building robust, scalable, and production-ready applications:

1. Event Loop & Concurrency Model
Understanding phases of the event loop

How asynchronous operations are handled

Microtasks vs Macrotasks

2. Streams and Buffers
Readable, Writable, Duplex, and Transform streams

Efficient file handling and network communication

Piping and chaining streams

3. Cluster and Worker Threads
Utilizing multiple CPU cores using cluster module

Worker Threads for CPU-intensive tasks

Difference between cluster and worker_threads

4. Child Processes & Inter-Process Communication
child_process.fork, spawn, and exec

Messaging between parent and child processes

5. Performance Optimization
Profiling with clinic.js, node --inspect

Memory leaks and garbage collection

Async optimization, avoiding blocking code

6. Custom Event Emitters
Creating and handling custom events

Decoupling logic using EventEmitter class

7. Caching Strategies
In-memory cache (e.g., lru-cache, node-cache)

Redis-based caching

Cache invalidation patterns

8. Security Best Practices
Preventing XSS, CSRF, SQL/NoSQL injection

Secure headers with Helmet

Rate limiting and request validation

JWT, OAuth2, and sessions

9. Building and Using Native Addons (C++)
Integrating C/C++ libraries into Node using N-API or node-gyp

10. Advanced Error Handling
Centralized error handlers

Error boundaries in async code (e.g., try/catch with promises, async/await)

Domain module (deprecated but still worth knowing)

11. Advanced Middleware Patterns
Writing reusable, dynamic, and configurable middleware

Middleware chains and error propagation

12. Microservices with Node.js
Service communication using gRPC, REST, or message queues

Service discovery and load balancing

API Gateway pattern

13. Message Queues & Pub/Sub
Using RabbitMQ, Kafka, or Redis Pub/Sub for async communication

Decoupling services via queues

14. Logging and Monitoring
Using Winston, Bunyan, or Pino for structured logging

Integrating with tools like Logstash, Kibana, Datadog, or Grafana

15. Testing at Scale
Unit, Integration, and E2E testing with Jest, Mocha, Supertest, Cypress

Test coverage and mocking dependencies

16. Dependency Injection (DI)
Managing dependencies cleanly using libraries like awilix or inversify










