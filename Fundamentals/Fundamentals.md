## 1. CLIENT - SERVER ARCHITECTURE

Client-Server Architecture is a model where two parties communicate over a network — the client sends a request and the server sends back a response. The client is the one asking, and the server is the one answering.

Real World Scenario:- 

Think of a restaurant. You are a customer (client). You call the waiter, place your order, and wait. The kitchen (server) receives that order, prepares the food, and sends it back to you through the waiter. You don't know how the kitchen works — you just asked, and you received.

Technical Example:-

When you type https://www.google.com in your browser, your browser (client) sends an HTTP GET request to Google's server. The server receives that request, processes it, and sends back an HTTP response containing the HTML of the Google homepage. Your browser then renders it on your screen. The client and server are separate — they only interact through requests and responses over HTTP.

## 2. I.P ADDRESS

An IP (Internet Protocol) Address is a unique numerical label assigned to every device connected to a network. It acts as the identity and location of a device, so that data knows exactly where to go and where to come back from.

Real World Scenario:- 

Going back to our restaurant — before you can visit it, you need its address. Without the address, you wouldn't know where to go. Every restaurant has a unique address that sets it apart from every other place in the city. In the same way, every server on the internet has an IP address — a unique location that tells your request exactly where to be delivered.

Technical Example:-

Every device on a network is assigned an IP address, for example 142.250.190.78 (one of Google's IPs). When your browser wants to reach Google, it first needs to find this address. Once it has the IP, it sends the HTTP request directly to that address over the network.

