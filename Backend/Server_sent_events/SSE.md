- let's discuss server-sent events, what they are in backend programming, how they are different from web sockets, and what is the need for such a system.

- There are couple of ways in which we send data from server to client over internet when you're a browser.
  - Establish a http connection over tcp , visiting index.html
    - Http is a Short live connection - send request - server responds - http connection is closed
      ![SSE_HTTP](images/SSE_1.png)
  - Establish connection with web sockets , open-up bi-directional tcp connection with client and server
    - Opens a pipe between server and client - chat application
      ![SSE_WEB_Sockets](images/SSE_2.png)
  - Server sent events built on http - it's like polling - compromise between http and websockets
    - Polling says ping the server every once in a while like for every couple of seconds & ask if there is new information - short polling
      ![Short Polling](images/SSE_3.png)
    - Long polling - as a client send the request & the server doesn't respond until it has data - delay might 20 30 seconds as weell
      ![Long polling](images/SSE_4.png)
- Out of three Architectures , The Polling one makes a little bit of sense
  - When only server needs to send data to the client
    - ex: Applications like dashboards - system like polling or SSE wpuld be useful , but `how is SSE different from polling`
- SSE is a special form of polling but not polling at all - special form of conveying data to client , where the connection over here is stable in a way that if your server implements SSE's - open a SSE and event source - using event source with the client , where the server has capability of sending unidirectional messages that means it almost acts like a single flow pipe , where the server can inform the client about all the neccessary updates which the server wants
- Adv over websockets:
  - Work only on http layer , friendly with Firewall , Load balancer , Reverse proxy
  - Stick to the same server for the whole lifecycle
- ![SSE](images/SSE_5.png)

# To Simplify;

```
Server-Sent Events (SSE) are a powerful technology that allows web servers to push data to clients in real-time. This means that instead of the client constantly asking the server for updates (polling), the server can send new data to the client whenever it becomes available.

Here's a breakdown of how SSE works and why it's useful:

How SSE Works:

Connection Establishment: The client establishes a persistent HTTP connection to the server.
Data Stream: The server sends a stream of data to the client in a special text-based format called text/event-stream.
Event Handling: The client receives the data stream and processes it as a series of events. Each event can contain different types of data.
Key Features of SSE:

Server-Initiated: The server pushes data to the client, eliminating the need for constant polling.
Persistent Connection: A single connection is used for continuous data transfer.
Lightweight: SSE is simpler and more efficient than other real-time technologies like WebSockets, especially for one-way data flow.
Built-in Browser Support: Most modern browsers have native support for SSE, making it easy to implement.
Common Use Cases:

Real-time Updates: Displaying live updates like stock prices, news feeds, or social media notifications.
Progress Indicators: Showing the progress of long-running tasks, such as file uploads or downloads.
Monitoring and Alerts: Sending alerts for system events, such as server status changes or security breaches.
Chat Applications: Enabling real-time messaging between users.
Advantages of SSE:

Efficiency: Reduces network overhead compared to polling.
Simplicity: Easier to implement than WebSockets for unidirectional data flow.
Real-time Updates: Provides instant updates to clients.
Limitations of SSE:

Unidirectional: Data flows only from the server to the client. For bi-directional communication, WebSockets are a better choice.
Limited Browser Support: While most modern browsers support SSE, older browsers may not.
Example:

Imagine a website that displays live scores for a sports game. With SSE, the server can push score updates to the client as they happen, without the client needing to refresh the page.

If you're interested in learning more about SSE, here are some resources:

MDN Web Docs: https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events
```
