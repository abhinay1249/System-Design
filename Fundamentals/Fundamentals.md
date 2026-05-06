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


## 4. PROXY (FORWARD, REVERSE)

A proxy is an intermediary, a middleman that stands between the client and the server. Depending on which side it stands on, it takes one of two forms.

Forward Proxy

A Forward Proxy sits on the client's side. The client sends its request to the proxy, and the proxy forwards it to the server on the client's behalf. The server never directly sees who the original client is — it only sees the proxy. This is commonly used to hide the client's identity, bypass restrictions, or filter outgoing traffic.

Real World Scenario:-

Think of a Forward Proxy like a personal assistant. You don't want to call the restaurant directly — so you ask your assistant to call on your behalf. The restaurant speaks to your assistant, not to you. You stay hidden behind that assistant. That assistant is the forward proxy.

Technical Example:-

Forward Proxy - When an employee inside a corporate network tries to visit a website, the request first goes to the company's forward proxy server. The proxy checks if the website is allowed, then forwards the request on the employee's behalf. The website only sees the proxy's IP address, not the employee's. This is how VPNs and corporate firewalls work.

Reverse Proxy

A Reverse Proxy sits on the server's side. The client sends its request thinking it is reaching the server directly, but it is actually hitting the reverse proxy first. The reverse proxy then decides which backend server to forward the request to. The client never directly sees the actual server, it only sees the proxy. This is widely used in production systems for security, performance, and traffic management.

Real World Scenario:-

Think of a Reverse Proxy like the front desk or reception of a large hotel restaurant. You walk up to the front desk and place your request. The front desk doesn't cook the food — it figures out which kitchen section (the starters section, the main course section, the desserts section) should handle your order, routes it there, and brings the response back to you. You never interacted with any specific kitchen directly. That front desk is the reverse proxy.

Technical Example:-

Reverse Proxy — When millions of users type www.netflix.com in their browser, they are not hitting a single Netflix server. Their request hits a reverse proxy first — in Netflix's case, this is managed through tools like NGINX or AWS CloudFront. The reverse proxy then routes each request to the appropriate backend service — one service for login, another for video streaming, another for recommendations — based on rules. The user never knows any of this is happening. To them, it is just Netflix.

This is why reverse proxies plays a major role in modern system design. They enable load distribution, SSL termination, caching, security filtering, and centralized routing all without the client to be know anything about the backend infrastructure.