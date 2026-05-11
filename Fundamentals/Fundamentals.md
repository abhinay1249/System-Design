"Fundamentals" the most important thing that holds a huge importance in each individual.

Here we are to understand the core fundamental of System Design.

In our day to day lives, we constantly use websites, applications mostly. In this AI driven world, 99.9% of people across the world will use applications and websites itself which make things simpler.

For Curios Minds (like me & you) who want to understand how systems run in the backend, how architectures are designed internally, how applications function aand how modern advancements reduce the need for verbose manual code (make people more lazy) from the past in the present.

Here goes the core fundamentals Of System Design that follows below:- 

# 1. CLIENT - SERVER ARCHITECTURE

Client-Server Architecture is a model where two parties communicate over a network — the client sends a request and the server sends back a response. The client is the one asking and the server is the one answering.

### Real World Scenario:- 

Think of a restaurant. You are a customer (client). You call the waiter, place your order and wait. The kitchen (server) receives that order, prepares the food and sends it back to you through the waiter. You don't know how the kitchen works — you just asked and you received.

### Technical Example:-

When you type https://www.google.com in your browser, your browser (client) sends an HTTP GET request to Google's server. The server receives that request, processes it and sends back an HTTP response containing the HTML of the Google homepage. Your browser then renders it on your screen. The client and server are separate — they only interact through requests and responses over HTTP.

  <img width="478" height="236" alt="Client-Server Architecture" src="https://github.com/user-attachments/assets/a9513b5a-7804-4dda-9d34-fe576c13d07f" />


# 2. I.P ADDRESS

An IP (Internet Protocol) Address is a unique numerical label assigned to every device connected to a network. It acts as the identity and location of a device, so that data knows exactly where to go and where to come back from.

For a client to communicate with a server, it needs the server's IP address to locate and send a request to it. However, since IP addresses are just strings of numbers and difficult to remember, domain names are used instead, they are simple English words that are easy to recall and map directly to the underlying IP address.

### Real World Scenario:- 

Going back to our restaurant — before you can visit it, you need its address. Without the address, you wouldn't know where to go. Every restaurant has a unique address that sets it apart from every other place in the city. In the same way, every server on the internet has an IP address — a unique location that tells your request exactly where to be delivered.

### Technical Example:-

Every device on a network is assigned an IP address, for example 142.250.190.78 (one of Google's IPs). When your browser wants to reach Google, it first needs to find this address. Once it has the IP, it sends the HTTP request directly to that address over the network.

  <img width="657" height="223" alt="IP Address" src="https://github.com/user-attachments/assets/a004ed13-68c3-4783-a60e-8a230cb161ef" />

In order to obtain the IP address from the domain name, a core concept is used — which is known as,


# 3. DOMAIN NAME SYSTEM (DNS)

How does the internet actually convert a domain name into an IP address? That is exactly what DNS, the Domain Name System does. 
DNS is essentially the phone book of the internet. It is a system that maintains a massive directory of domain names and their corresponding IP addresses. Whenever you type a domain name, DNS works silently in the background to look it up, find the matching IP address and hand it back to your browser so the request can reach the right server.

### Real World Scenario:-

Think of it like a restaurant directory service. You call up the directory and say, "I want to visit The Grand Kitchen, what is their address?" The directory looks it up and tells you, "That's at 14B, 3rd Cross, 5th Block." Now you have the address and you can head there.

### Technical Example:-

When you type google.com in your browser, the following steps happen in milliseconds:

1) Your browser asks the DNS Resolver (usually provided by your internet provider) — "What is the IP for google.com?"
2) The DNS Resolver checks its cache. If it has seen this before, it returns the answer immediately.
3) If not, it contacts the Root DNS Server, which points it toward the right direction.
4) The resolver then queries the Authoritative DNS Server for google.com, which holds the definitive record.
5) The IP address 142.250.190.78 is returned to your browser.
6) Your browser now sends the HTTP request directly to that IP address.
This entire lookup chain is called a DNS Resolution. It happens every time you visit a new website and the result is cached temporarily so the full lookup does not have to repeat every single time.

     <img width="463" height="266" alt="03_Domain Name System" src="https://github.com/user-attachments/assets/81c48ec2-5af4-4e52-83f5-5373dbaf97a4" />


# 4. PROXY (FORWARD, REVERSE)

A proxy is an intermediary, a middleman that stands between the client and the server. Depending on which side it stands on, it takes one of two forms.

### Forward Proxy

A Forward Proxy sits on the client's side. The client sends its request to the proxy and the proxy forwards it to the server on the client's behalf. The server never directly sees who the original client is — it only sees the proxy. This is commonly used to hide the client's identity, bypass restrictions, or filter outgoing traffic.

### Real World Scenario:-

Think of a Forward Proxy like a personal assistant. You don't want to call the restaurant directly — so you ask your assistant to call on your behalf. The restaurant speaks to your assistant, not to you. You stay hidden behind that assistant. That assistant is the forward proxy.

### Technical Example:-

Forward Proxy - When an employee inside a corporate network tries to visit a website, the request first goes to the company's forward proxy server. The proxy checks if the website is allowed, then forwards the request on the employee's behalf. The website only sees the proxy's IP address, not the employee's. This is how VPNs and corporate firewalls work.

<img width="619" height="250" alt="04_Forward Proxy" src="https://github.com/user-attachments/assets/12cc727e-be13-4983-8c56-f82576bd1862" />

# Reverse Proxy

A Reverse Proxy sits on the server's side. The client sends its request thinking it is reaching the server directly, but it is actually hitting the reverse proxy first. The reverse proxy then decides which backend server to forward the request to. The client never directly sees the actual server, it only sees the proxy. This is widely used in production systems for security, performance and traffic management.

### Real World Scenario:-

Think of a Reverse Proxy like the front desk or reception of a large hotel restaurant. You walk up to the front desk and place your request. The front desk doesn't cook the food — it figures out which kitchen section (the starters section, the main course section, the desserts section) should handle your order, routes it there and brings the response back to you. You never interacted with any specific kitchen directly. That front desk is the reverse proxy.

### Technical Example:-

Reverse Proxy — When millions of users type www.netflix.com in their browser, they are not hitting a single Netflix server. Their request hits a reverse proxy first — in Netflix's case, this is managed through tools like NGINX or AWS CloudFront. The reverse proxy then routes each request to the appropriate backend service — one service for login, another for video streaming, another for recommendations — based on rules. The user never knows any of this is happening. To them, it is just Netflix.

This is why reverse proxies plays a major role in modern system design. They enable load distribution, SSL termination, caching, security filtering and centralized routing all without the client to be know anything about the backend infrastructure.

<img width="495" height="222" alt="04_Reverse Proxy" src="https://github.com/user-attachments/assets/31f84280-cbbb-4661-acbf-4a22cca838ca" />


# 5. LATENCY

When a client sends a request to a server, the response doesn't happen instantly. The time it takes for a data packet to travel from its source to its destination is called Latency.

Simply put, latency is a measure of delay. It's the waiting period between taking an action (making a request) and seeing the result(receving as response). It is typically measured in milliseconds (ms). A system with low latency feels fast and responsive, while a system with high latency feels sluggish and slow. In system design, minimizing latency is one of the most important goals for delivering a good user experience.

### Real World Scenario:-

Back in our restaurant, you've just placed your order with the waiter. The time it takes for the waiter to physically walk from your table to the kitchen to hand in the order ticket is your latency. If your table is right next to the kitchen, the waiter takes two steps and the delay is minimal (low latency). But if you are seated in the outdoor and the kitchen is all the way in the back of the building, the waiter has to walk much further, taking much longer to deliver the ticket (high latency).

Notice that the food takes the exact same amount of time to cook in both cases. The delay isn't in the preparation (processing) — the delay is purely in the travel time.

### Technical Example:-

Imagine a user in Mumbai, India, trying to access a website hosted on a server in New York, USA. When they click a button, their HTTP request has to physically travel through thousands of miles of fiber-optic cables across oceans to reach New York and the response has to travel all the way back. Even near the speed of light, this immense distance causes a noticeable delay — perhaps around 250 milliseconds. This is high latency.

If the company instead moves their server (or a copy of their data) to Mumbai, the data only has to travel a few miles. The response time drops to 20 milliseconds. This is low latency.

Physical distance is a primary cause of network latency, which is why global systems use strategies like placing servers geographically closer to their users to reduce the delay.

<img width="699" height="457" alt="image" src="https://github.com/user-attachments/assets/ff22ead0-d4cb-46ea-be3e-675e424a8ad5" />


# 6. HTTP/HTTPS

When a client and server talk to each other over a network, they need a shared language — a set of rules so they can understand each other. This is called a protocol. HTTP (Hypertext Transfer Protocol) is the universal language of the web. It defines how requests and responses are formatted and transmitted.

HTTP : It transmits data in plain text. Anyone intercepting the network traffic can easily read it.


HTTPS: HTTPS is simply HTTP with a secure, encrypted wrapper around it. It encrypts the data before it leaves the client and only the intended server can decrypt it, ensuring that sensitive information like passwords and credit card numbers remain safe from eavesdroppers.

### Real World Scenario:-

In our restaurant, imagine you want to order a secret menu item, but you don't want anyone else at nearby tables to hear what you are ordering. [Sounds Funny Right]

If you use HTTP, you just tell your order across the room to the waiter. Everyone sitting around you can hear exactly what you said.

If you use HTTPS, you write your secret order on a piece of paper, lock it inside a small box and hand the locked box to the waiter. Even if someone intercepts the waiter on the way to the kitchen, they cannot open the box. Only the kitchen staff has the key to unlock it, read your order and prepare your food.

### Technical Example:- 

When you visit a banking website and log in, your browser (client) sends your username and password to the bank's server.

If the site used HTTP, your password would be sent over the internet as plain text. A hacker sitting on the same public Wi-Fi network could easily intercept the traffic and read your password. Because the bank uses HTTPS (indicated by the lock icon and https:// in the URL), your browser encrypts the password into an unreadable string before sending it. 

Even if the hacker intercepts the network packet, all they see is encrypted data. The data remains encrypted during transit and is only decrypted once it safely reaches the bank's server, which holds the private key required to unlock it.

<img width="535" height="363" alt="image" src="https://github.com/user-attachments/assets/fe3bbc2f-38d4-48ec-93e1-3dc6a718039e" />


# 7. API

In our digital world, different software applications need a way to communicate and share data with each other. This is exactly what an API (Application Programming Interface) does. It is a set of defined rules that allows one piece of software to talk to another.
Instead of building complex features from scratch, developers use APIs to plug into existing services like checking the weather, processing a payment, or displaying a map. The API acts as a messenger: it takes your request, tells the other system what you want and returns the response back to you. You don't need to know how the other system is built or how its code works internally; you just need to know the correct way to ask it for what you want. The api can be fetched in different types such as in json and xml format.

### Real World Scenario:-

In our restaurant, you (the customer) want food from the kitchen, but you are not allowed to walk into the kitchen, open the fridge and start cooking yourself. The kitchen has its own complex internal operations that you don't need to understand. Instead, you interact with the menu. The menu provides a list of specific dishes you are allowed to order. The waiter takes your order from the menu, delivers it to the kitchen and brings the cooked food back to your table.

In this scenario, the menu is the API documentation (the rules defining what you can ask for) and the waiter is the API itself,the messenger that securely transports your request to the kitchen and brings the response back, without you ever having to step foot inside the kitchen.

### Technical Example:- 

Imagine you are using a ride-sharing app like Uber. Uber needs to show you a map of where your driver is, but Uber did not build their own global mapping system from scratch. Instead Uber uses the Google Maps API. When you open the Uber app, the app sends an HTTP request to the Google Maps API saying, "Can I get the map data for this specific location?". The Google Maps API receives the request, pulls the map data from Google's massive internal servers and sends it back to the Uber app to display on your screen. Uber gets to display world-class maps without ever having direct access to Google's backend code or private databases.

<img width="533" height="249" alt="image" src="https://github.com/user-attachments/assets/274213ce-f79b-470a-8a4b-0aeb9f3307d6" />


# 8. REST API

We now know what an API is? A set of rules that allows one piece of software to talk to another. But how should that API be designed? What structure should it follow? Here comes REST API in place.

REST API defines how client and servers communicate over HTTP in a structured way. The core idea behind REST is simple: every piece of data on the server (a user, a product, an order) is treated as a resource and each resource is accessed using a unique URL. The client interacts with these resources using standard HTTP methods:- 
  
  --> GET to read 
  --> POST to create 
  --> PUT to update 
  --> DELETE to remove 

The server responds with the data in a lightweight format, typically JSON. Each request is independent, the server does not remember anything about the previous request. This is called being "stateless".

### Real World Scenario:-

Let us go back to our restaurant. Imagine the restaurant introduces a standardized ordering system that every waiter should follow, a fixed set of actions and a clear way to use them.

--> If you want to see the menu, you say: Show me the menu. 
  → That is a GET request.
--> If you want to place a new order, you say: I'd like to order the pasta. 
  → That is a POST request.
--> If you want to change your order, you say: Actually, make that a pizza instead." 
  → That is a PUT request.
--> If you want to cancel your order, you say: Please cancel my order. 
  → That is a DELETE request.

Every customer follows the same four actions. Every waiter understands them. There is no confusion, no ambiguity. That standardized system is what REST brings to the world of APIs.

### Technical Example:- 

Consider X. When you interact with tweets, behind the scenes, your app is calling Twitter's REST API:

--> GET    -  /api/tweets/12345     → Fetches the tweet with ID 12345.
--> POST   -  /api/tweets           → Creates a new tweet (with the tweet content sent in the request body as JSON).
--> PUT    -  /api/tweets/12345     → Updates the tweet with ID 12345.
--> DELETE -  /api/tweets/12345     → Deletes the tweet with ID 12345.

Each URL represents a specific resource (tweet), each HTTP method represents a specific action and each request is completely independent, the server does not need to remember what you did before. The response comes back in JSON format, containing the data your app needs to present on the screen.

<img width="542" height="247" alt="image" src="https://github.com/user-attachments/assets/c4c0fbd0-d467-4ea0-9790-0974e2ac7bb0" />


# 9. GRAPHQL

GraphQL was created by Meta[FaceBook] in 2012 to solve exactly the drawback of REST.

REST APIs work well, but they come with a limitation. They return fixed data structures. When you hit a REST endpoint, the server decides what data to send back but not the client. Sometimes the response contains more data than the client needs (over-fetching) and sometimes it doesn't contain enough data forcing the client to make multiple requests to different endpoints to get everything it needs (under-fetching).

 It is a query language for APIs that lets the client specify exactly what data it requies nothing more or nothing less. Instead of multiple endpoints for different resources, GraphQL uses a single endpoint. The client sends a structured query describing the exact fields it wants and the server responds with that data in JSON format.

--> REST, the server is in control of the response.
--> GraphQL, the client is in control.

### Real World Scenario:-

Back in our restaurant, with the REST approach. You order a "Burger Combo Meal" and the kitchen sends you a burger, fries, a drink, a salad, and a dessert. But you only wanted the burger, fries and the drink. You got a lot more than you asked for (over-fetching). Or maybe you ordered the burger but it didn't come with potato chips, so you have to place a second order just for potatochips (under-fetching).

With GraphQL approach, You are handed a blank order slip and you write down exactly what you want, "I want a burger and drink itself". The kitchen reads your custom slip and sends you precisely a burger and drink. No extra salad you didn't ask for. No second trip to the waiter. You got exactly what you requested in a single order.

### Technical Example:- 

Imagine you are building the profile page for a social media app like Instagram. You need the user's name, their profile picture and their last 5 posts.

With a REST API, you might have to make three separate requests:

--> GET /api/users/42                   → Returns the user's name, email, date of birth, bio and 20 other fields you don't need.
--> GET /api/users/42/profile-picture   → Returns the profile picture.
--> GET /api/users/42/posts?limit=5     → Returns the last 5 posts.
That is three network round trips and a lot of unnecessary data.

With GraphQL, you make a single request to one endpoint and specify exactly just like below:-

<img width="230" height="292" alt="image" src="https://github.com/user-attachments/assets/2dad577a-a709-41ca-92a4-70899d72e359" />

The server responds with exactly the name, the profile picture and the last 5 posts with only their title and image. 
One request. No wasted data. No extra round trips.

This is why companies like Facebook, GitHub, Shopify, etc adopted GraphQL. It gives the client precise control over the data it receives by reducing bandwidth and improving performance.

<img width="539" height="264" alt="image" src="https://github.com/user-attachments/assets/1387e832-d235-4821-85e5-0134ed36394e" />


# 10. DATABASES

Every application needs a place to store, organize and retrieve data. When a user signs up, places an order, or posts a comment that data has to be present permanent so it can be accessed later. That place is a Database.

A database is like a storage system that the server uses to save information and pull it back whenever needed. Without a database, every piece of data would be lost the moment the server restarts. It is what makes applications remember your login credentials, your order history, your messages. 

In system design, the database is one of the most critical components because almost every operation such as reading, writing, updating, deleting happens on it.

### Real World Scenario:-

In our restaurant, the kitchen needs to remember things such as what dishes are available, what ingredients are in stock, which tables have placed orders and what each customer ordered. If the kitchen had no record of any of this and relied purely on memory then things would fall apart very quickly. Orders would be forgotten, ingredients would run out without warning and returning customers would have to explain their preferences every single time.

The database is the restaurant's record system, A register where every order, every reservation and every inventory count is stored so it can be looked up at any time.

### Technical Example:-

When you create an account on Amazon, your name, email, password and address are sent to Amazon's server. The server doesn't just hold that data in temporary memory it writes it into a database. The next time you log in, the server queries the database, finds your record, verifies your password and loads your profile. When you place an order, a new entry is written to the database. When you check your order history, the server reads from the database and sends it back to your browser.

Every action you take such as signing up, logging in, ordering, reviewing is a read or write operation against the database. 


# 11. SQL VS NOSQL

We know what a database is, the next question is how is the data actually organized inside it? Which depends on the type of database you choose. There are two major types:-

→ SQL
→ NOSQL

SQL

A SQL Database (Relational Database) stores data in tables in the form of rows and columns like a spreadsheet. Every row follows the same fixed structure and tables can be linked to each other through relationships. You interact with the data using a language called Structured Query Language (SQL). Examples are PostgreSQL, MySQL and Oracle.

### Real World Scenario:- 

A restaurant's holds a reservation book. Every entry follows the exact same format — customer name, date, time, number of guests, table number. If you want to find all reservations for a particular date, you simply look down that column. It is structured, predictable and organized.

### Technical Example:-

A banking application needs to store each transaction with an exact amount, a sender account, a receiver account and a timestamp. The data is highly structured and every record looks the same. Relationships does matter here as an account belongs to a customer, a transaction belongs to an account. A SQL database like PostgreSQL handles this perfectly because it enforces structure and ensures accuracy.

SQL databases does maintain predefined schema, acid properties and strong consistency to hold the data in it.

NOSQL

A NoSQL Database (Non-Relational) does not use tables or fixed structure. Instead, it stores data in flexible formats like documents, key-value pairs, or graphs. Each record can look completely different from the next. Examples include MongoDB, Redis and Cassandra.

### Real World Scenario:-

A chef has his own personal notebook. One page has a recipe. The next page has a quick note stating "Table 7 is allergic to peanuts." Another page has a supplier's phone number. There is no fixed format where in each page stores whatever is needed at that moment. It is flexible and fast but not organized.

### Technical Example:-

Let us consider Instagram where One user's feed has photos, another has reels, another has stories with polls and stickers. The data varies wildly from user to user and changes constantly. A NoSQL database like MongoDB handles this well because it can store each user's activity as a flexible document without forcing every record into a same table format.


# 12. SCALING - VERTICAL SCALING

When an application starts getting more users and more traffic, the server handling all those requests will struggle to keep it efficient. It becomes slow, overloaded and unresponsive. The solution is Scaling, by increasing the capacity of your system so it can handle more load.

Vertical Scaling (also called scaling up). It means making your existing server more powerful by adding more CPU, more RAM, more storage to the same machine. You are not adding new servers; you are upgrading the one you already have. Vertical scaling is simple and straightforward but it has a hard limitatiton where in there is only so much hardware you can pack into a single machine. Even the most powerful server in the world will have a bottleneck at some point of time.

### Real World Scenario:-

Our restaurant is getting popular and the kitchen is struggling to handle the growing number of orders. One approach is to upgrade the kitchen itself by installing a bigger stove, add a larger oven, get a wider countertop. The same kitchen, the same space but with more powerful equipment so it can handle more orders at once. This works well up to a point, but there is a limit. You can only fit so much equipment into one kitchen before there is physically no more room to upgrade.

### Technical Example:-

A startup runs its entire application on a single server with 4 GB RAM and 2 CPU cores. As traffic grows, the server starts slowing down. The team vertically scales by upgrading to a machine with 32 GB RAM and 16 CPU cores. The application runs faster and handles more users without changing any code or architecture. But if traffic keeps growing, that single machine will eventually max out again and there is no bigger machine left to upgrade.


Here is the catch, where in:-
→ You cant keep upgarding a server forever.
→ More powerful servers becomes exponentially more expensive.
→ Single Point of Failure - Even if one issue rises then the server shall be down.


# 13. HORIZONTAL SCALING

We saw that vertical scaling has a bottleneck.As you need to upgrade a single machine itself. To overcome this we have a concept known as 

Horizontal Scaling (also called scaling out) takes a completely different approach. Instead of making one server more powerful, you add more servers and distribute the load across them. Each server handles a portion of the incoming traffic such that no single machine is overwhelmed. If traffic grows further you simply add another server. There is no limit over here, you can keep adding machines as demand increases. This is why horizontal scaling is the preferred strategy for large-scale systems that is capable to serve millions of users.

### Real World Scenario:-

Our restaurant has upgraded its kitchen as much as physically possible, but orders are still piling up. Instead of trying to squeeze more into the same kitchen, the owner opens a second kitchen branch across town. Now orders are split between two kitchens. If demand grows even more, a third branch is opened. Each branch handles its own share of customers and together they serve far more people than a single location ever could.

### Technical Example:-

Netflix serves over 200 million users worldwide. It runs its application across hundreds of servers. When a user in India streams a movie then one server handles their request. When a user in the US streams at the same time, a different server handles theirs. If a new show launches and traffic spikes, Netflix spins up additional servers automatically to absorb the surge. Once the spike passes the extra servers are removed. This ability to scale in and out on demand is the core advantage of horizontal scaling.


# 14. LOAD BALANCER

With horizontal scaling, we now have multiple servers handling incoming traffic. But there will be a question stating when a request comes in, who decides which server should handle it? If all requests accidentally go to one server while the others sit idle, horizontal scaling becomes pointless.

A Load Balancer is the component that is answer to the above question. It sits in front of all the servers and distributes incoming requests evenly across them, making sure no single server is overloaded while others are underutilized. If one server goes down, the load balancer detects it and stops sending traffic to it and routing requests to the remaining healthy servers instead.

Load Balancer does route this traffic to multiple servers by using few algorithms such as Round Robin, I.P Hashing, Least Connections etc.. 

### Real World Scenario:-

Our restaurant now has multiple order counters to handle the rush. But if there is no one managing the crowd then all customers might line up at the first counter while the other counters remain empty. To fix this the restaurant places a floor manager at the entrance. The floor manager looks at all the counters then sees which one has the shortest queue and directs each incoming customer to the least busy counter. This results every counter stays evenly loaded and customers get served faster. The floor manager is the load balancer.

### Technical Example:-

When you visit www.amazon.com, your request does not go directly to a single server. It first hits Amazon's load balancer. The load balancer checks which of the hundreds of backend servers is least busy at that moment and forwards your request over there. The next user's request might go to a completely different server. If one server crashes, the load balancer automatically removes it from the pool and redirects traffic to the others this cannot be noticed by the user.

Common load balancers used in production include NGINX, HAProxy and cloud-managed solutions like AWS Elastic Load Balancer (ELB).


Until, here the fundamental concepts till the servers is presented. Hope this would be useful and helpful for the basic understanding of how the backend systems runs which is completely unknown for the user on the frontend screen. Let us move ahead and deep dive into the core part of the databases section in Part - 2. Stay Tuned.



