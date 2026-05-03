## 1. CLIENT - SERVER ARCHITECTURE

Client-Server Architecture is a model where two parties communicate over a network — the client sends a request and the server sends back a response. The client is the one asking, and the server is the one answering.

Real World Scenario:- 

Think of a restaurant. You are a customer (client). You call the waiter, place your order, and wait. The kitchen (server) receives that order, prepares the food, and sends it back to you through the waiter. You don't know how the kitchen works — you just asked, and you received.

Technical Example:-

When you type https://www.google.com in your browser, your browser (client) sends an HTTP GET request to Google's server. The server receives that request, processes it, and sends back an HTTP response containing the HTML of the Google homepage. Your browser then renders it on your screen. The client and server are separate — they only interact through requests and responses over HTTP.

  <img width="478" height="236" alt="Client-Server Architecture" src="https://github.com/user-attachments/assets/a9513b5a-7804-4dda-9d34-fe576c13d07f" />

## 2. I.P ADDRESS

An IP (Internet Protocol) Address is a unique numerical label assigned to every device connected to a network. It acts as the identity and location of a device, so that data knows exactly where to go and where to come back from.

For a client to communicate with a server, it needs the server's IP address to locate and send a request to it. However, since IP addresses are just strings of numbers and difficult to remember, domain names are used instead, they are simple English words that are easy to recall and map directly to the underlying IP address.

Real World Scenario:- 

Going back to our restaurant — before you can visit it, you need its address. Without the address, you wouldn't know where to go. Every restaurant has a unique address that sets it apart from every other place in the city. In the same way, every server on the internet has an IP address — a unique location that tells your request exactly where to be delivered.

Technical Example:-

Every device on a network is assigned an IP address, for example 142.250.190.78 (one of Google's IPs). When your browser wants to reach Google, it first needs to find this address. Once it has the IP, it sends the HTTP request directly to that address over the network.

  <img width="657" height="223" alt="IP Address" src="https://github.com/user-attachments/assets/a004ed13-68c3-4783-a60e-8a230cb161ef" />

In order to obtain the IP address from the domain name, a core concept is used — which is known as,

## 3. DOMAIN NAME SYSTEM (DNS)

How does the internet actually convert a domain name into an IP address? That is exactly what DNS, the Domain Name System does. 
DNS is essentially the phone book of the internet. It is a system that maintains a massive directory of domain names and their corresponding IP addresses. Whenever you type a domain name, DNS works silently in the background to look it up, find the matching IP address, and hand it back to your browser so the request can reach the right server.

Real World Scenario:-

Think of it like a restaurant directory service. You call up the directory and say, "I want to visit The Grand Kitchen, what is their address?" The directory looks it up and tells you, "That's at 14B, 3rd Cross, 5th Block." Now you have the address and you can head there.

Technical Example:-

When you type google.com in your browser, the following steps happen in milliseconds:
1) Your browser asks the DNS Resolver (usually provided by your internet provider) — "What is the IP for google.com?"
2) The DNS Resolver checks its cache. If it has seen this before, it returns the answer immediately.
3) If not, it contacts the Root DNS Server, which points it toward the right direction.
4) The resolver then queries the Authoritative DNS Server for google.com, which holds the definitive record.
5) The IP address 142.250.190.78 is returned to your browser.
6) Your browser now sends the HTTP request directly to that IP address.
This entire lookup chain is called a DNS Resolution. It happens every time you visit a new website, and the result is cached temporarily so the full lookup does not have to repeat every single time.

     <img width="463" height="266" alt="03_Domain Name System" src="https://github.com/user-attachments/assets/81c48ec2-5af4-4e52-83f5-5373dbaf97a4" />
