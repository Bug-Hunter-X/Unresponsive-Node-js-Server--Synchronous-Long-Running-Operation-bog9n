# Unresponsive Node.js Server

This repository demonstrates a common issue in Node.js applications: an unresponsive server caused by a long-running synchronous operation within the request handler.  The event loop is blocked, leading to poor performance and unresponsiveness.

## Bug Description

A synchronous loop within the request handler of a Node.js HTTP server causes the server to become unresponsive.  New requests are queued but not processed until the loop completes.

## Solution

The solution involves refactoring the long-running operation to be asynchronous using techniques like asynchronous functions, promises, or worker threads to avoid blocking the main event loop.  This allows the server to remain responsive while handling the long operation concurrently.

## How to reproduce

1. Clone this repository.
2. Run `node bug.js`.
3. Attempt to make multiple requests to `http://localhost:3000/` using tools like `curl` or your browser.  You will observe that the server becomes unresponsive.
4. After a significant delay, the server will eventually respond to pending requests. 
5. Run `node bugSolution.js` and test again. The solution prevents the server from being unresponsive.
