# Node.js Server Hang
This repository demonstrates a common issue in Node.js applications: blocking the event loop with a long-running synchronous operation.  This leads to the server becoming unresponsive to new requests.

The `bug.js` file shows a simple HTTP server that performs a 5-second blocking operation.  This prevents the server from handling other requests during that time.  The solution, `bugSolution.js`, demonstrates how to use asynchronous operations to avoid this problem. 

## How to Reproduce
1. Clone this repository.
2. Navigate to the directory.
3. Run `node bug.js`.
4. Open multiple browser tabs and try to access `http://localhost:3000`.  You'll observe that after the first request, subsequent requests hang.
5. Run `node bugSolution.js`.  This version will handle multiple requests concurrently without blocking.

## Solution
The solution lies in utilizing asynchronous programming concepts. Node.js is built on an event-driven, non-blocking I/O model.  Blocking the event loop negates this advantage. The improved version uses asynchronous techniques to avoid this issue. 