# Fundamentals

"Fundamentals" the most important thing that holds a huge importance in each individual.

Here we are to understand the core fundamental of System Design.

In our day to day lives, we constantly use websites, applications mostly. In this AI driven world, 99.9% of people across the world will use applications and websites itself which make things simpler.

For Curios Minds (like me & you) who want to understand how systems run in the backend, how architectures are designed internally, how applications function aand how modern advancements reduce the need for verbose manual code (make people more lazy) from the past in the present.

Here goes the core fundamentals Of System Design that follows below:- 

# 1. CLIENT - SERVER ARCHITECTURE

Client-Server Architecture is a model where two parties communicate over a network the client sends a request and the server sends back a response. The client is the one asking and the server is the one answering.

### Real World Scenario:- 

Think of a restaurant. You are a customer (client). You call the waiter, place your order and wait. The kitchen (server) receives that order, prepares the food and sends it back to you through the waiter. You don't know how the kitchen works you just asked and you received.

### Technical Example:-

When you type https://www.google.com in your browser, your browser (client) sends an HTTP GET request to Google's server. The server receives that request, processes it and sends back an HTTP response containing the HTML of the Google homepage. Your browser then renders it on your screen. The client and server are separate they only interact through requests and responses over HTTP.

  <img width="478" height="236" alt="Client-Server Architecture" src="https://github.com/user-attachments/assets/a9513b5a-7804-4dda-9d34-fe576c13d07f" />


# 2. I.P ADDRESS

An IP (Internet Protocol) Address is a unique numerical label assigned to every device connected to a network. It acts as the identity and location of a device, so that data knows exactly where to go and where to come back from.

For a client to communicate with a server, it needs the server's IP address to locate and send a request to it. However, since IP addresses are just strings of numbers and difficult to remember, domain names are used instead, they are simple English words that are easy to recall and map directly to the underlying IP address.

### Real World Scenario:- 

Going back to our restaurant before you can visit it, you need its address. Without the address, you wouldn't know where to go. Every restaurant has a unique address that sets it apart from every other place in the city. In the same way, every server on the internet has an IP address a unique location that tells your request exactly where to be delivered.

### Technical Example:-

Every device on a network is assigned an IP address, for example 142.250.190.78 (one of Google's IPs). When your browser wants to reach Google, it first needs to find this address. Once it has the IP, it sends the HTTP request directly to that address over the network.

  <img width="657" height="223" alt="IP Address" src="https://github.com/user-attachments/assets/a004ed13-68c3-4783-a60e-8a230cb161ef" />

In order to obtain the IP address from the domain name, a core concept is used which is known as,


# 3. DOMAIN NAME SYSTEM (DNS)

How does the internet actually convert a domain name into an IP address? That is exactly what DNS, the Domain Name System does. 
DNS is essentially the phone book of the internet. It is a system that maintains a massive directory of domain names and their corresponding IP addresses. Whenever you type a domain name, DNS works silently in the background to look it up, find the matching IP address and hand it back to your browser so the request can reach the right server.

### Real World Scenario:-

Think of it like a restaurant directory service. You call up the directory and say, "I want to visit The Grand Kitchen, what is their address?" The directory looks it up and tells you, "That's at 14B, 3rd Cross, 5th Block." Now you have the address and you can head there.

### Technical Example:-

When you type google.com in your browser, the following steps happen in milliseconds:

1) Your browser asks the DNS Resolver (usually provided by your internet provider) "What is the IP for google.com?"
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

A Forward Proxy sits on the client's side. The client sends its request to the proxy and the proxy forwards it to the server on the client's behalf. The server never directly sees who the original client is it only sees the proxy. This is commonly used to hide the client's identity, bypass restrictions, or filter outgoing traffic.

### Real World Scenario:-

Think of a Forward Proxy like a personal assistant. You don't want to call the restaurant directly so you ask your assistant to call on your behalf. The restaurant speaks to your assistant, not to you. You stay hidden behind that assistant. That assistant is the forward proxy.

### Technical Example:-

Forward Proxy - When an employee inside a corporate network tries to visit a website, the request first goes to the company's forward proxy server. The proxy checks if the website is allowed, then forwards the request on the employee's behalf. The website only sees the proxy's IP address, not the employee's. This is how VPNs and corporate firewalls work.

<img width="619" height="250" alt="04_Forward Proxy" src="https://github.com/user-attachments/assets/12cc727e-be13-4983-8c56-f82576bd1862" />

# Reverse Proxy

A Reverse Proxy sits on the server's side. The client sends its request thinking it is reaching the server directly, but it is actually hitting the reverse proxy first. The reverse proxy then decides which backend server to forward the request to. The client never directly sees the actual server, it only sees the proxy. This is widely used in production systems for security, performance and traffic management.

### Real World Scenario:-

Think of a Reverse Proxy like the front desk or reception of a large hotel restaurant. You walk up to the front desk and place your request. The front desk doesn't cook the food it figures out which kitchen section (the starters section, the main course section, the desserts section) should handle your order, routes it there and brings the response back to you. You never interacted with any specific kitchen directly. That front desk is the reverse proxy.

### Technical Example:-

Reverse Proxy, When millions of users type www.netflix.com in their browser, they are not hitting a single Netflix server. Their request hits a reverse proxy first in Netflix's case, this is managed through tools like NGINX or AWS CloudFront. The reverse proxy then routes each request to the appropriate backend service one service for login, another for video streaming, another for recommendations based on rules. The user never knows any of this is happening. To them, it is just Netflix.

This is why reverse proxies plays a major role in modern system design. They enable load distribution, SSL termination, caching, security filtering and centralized routing all without the client to be know anything about the backend infrastructure.

<img width="495" height="222" alt="04_Reverse Proxy" src="https://github.com/user-attachments/assets/31f84280-cbbb-4661-acbf-4a22cca838ca" />


# 5. LATENCY

When a client sends a request to a server, the response doesn't happen instantly. The time it takes for a data packet to travel from its source to its destination is called Latency.

Simply put, latency is a measure of delay. It's the waiting period between taking an action (making a request) and seeing the result(receving as response). It is typically measured in milliseconds (ms). A system with low latency feels fast and responsive, while a system with high latency feels sluggish and slow. In system design, minimizing latency is one of the most important goals for delivering a good user experience.

### Real World Scenario:-

Back in our restaurant, you've just placed your order with the waiter. The time it takes for the waiter to physically walk from your table to the kitchen to hand in the order ticket is your latency. If your table is right next to the kitchen, the waiter takes two steps and the delay is minimal (low latency). But if you are seated in the outdoor and the kitchen is all the way in the back of the building, the waiter has to walk much further, taking much longer to deliver the ticket (high latency).

Notice that the food takes the exact same amount of time to cook in both cases. The delay isn't in the preparation (processing) the delay is purely in the travel time.

### Technical Example:-

Imagine a user in Mumbai, India, trying to access a website hosted on a server in New York, USA. When they click a button, their HTTP request has to physically travel through thousands of miles of fiber-optic cables across oceans to reach New York and the response has to travel all the way back. Even near the speed of light, this immense distance causes a noticeable delay perhaps around 250 milliseconds. This is high latency.

If the company instead moves their server (or a copy of their data) to Mumbai, the data only has to travel a few miles. The response time drops to 20 milliseconds. This is low latency.

Physical distance is a primary cause of network latency, which is why global systems use strategies like placing servers geographically closer to their users to reduce the delay.

<img width="699" height="457" alt="image" src="https://github.com/user-attachments/assets/ff22ead0-d4cb-46ea-be3e-675e424a8ad5" />


# 6. HTTP/HTTPS

When a client and server talk to each other over a network, they need a shared language a set of rules so they can understand each other. This is called a protocol. HTTP (Hypertext Transfer Protocol) is the universal language of the web. It defines how requests and responses are formatted and transmitted.

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

Back in our restaurant, with the REST approach. You order a "Burger Combo Meal" and the kitchen sends you a burger, fries, a drink, a salad and a dessert. But you only wanted the burger, fries and the drink. You got a lot more than you asked for (over-fetching). Or maybe you ordered the burger but it didn't come with potato chips, so you have to place a second order just for potatochips (under-fetching).

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

<img width="704" height="200" alt="image" src="https://github.com/user-attachments/assets/91c4e415-3847-4411-b368-03e1b464611a" />


# 11. SQL VS NOSQL

We know what a database is, the next question is how is the data actually organized inside it? Which depends on the type of database you choose. There are two major types:-

→ SQL
→ NOSQL

SQL

A SQL Database (Relational Database) stores data in tables in the form of rows and columns like a spreadsheet. Every row follows the same fixed structure and tables can be linked to each other through relationships. You interact with the data using a language called Structured Query Language (SQL). Examples are PostgreSQL, MySQL and Oracle.

### Real World Scenario:- 

A restaurant's holds a reservation book. Every entry follows the exact same format customer name, date, time, number of guests, table number. If you want to find all reservations for a particular date, you simply look down that column. It is structured, predictable and organized.

### Technical Example:-

A banking application needs to store each transaction with an exact amount, a sender account, a receiver account and a timestamp. The data is highly structured and every record looks the same. Relationships does matter here as an account belongs to a customer, a transaction belongs to an account. A SQL database like PostgreSQL handles this perfectly because it enforces structure and ensures accuracy.

SQL databases does maintain predefined schema, acid properties and strong consistency to hold the data in it.

<img width="319" height="225" alt="image" src="https://github.com/user-attachments/assets/74533633-57cb-4562-a67e-e0dbade6434d" />

NOSQL

A NoSQL Database (Non-Relational) does not use tables or fixed structure. Instead, it stores data in flexible formats like documents, key-value pairs, or graphs. Each record can look completely different from the next. Examples include MongoDB, Redis and Cassandra.

### Real World Scenario:-

A chef has his own personal notebook. One page has a recipe. The next page has a quick note stating "Table 7 is allergic to peanuts." Another page has a supplier's phone number. There is no fixed format where in each page stores whatever is needed at that moment. It is flexible and fast but not organized.

### Technical Example:-

Let us consider Instagram where One user's feed has photos, another has reels, another has stories with polls and stickers. The data varies wildly from user to user and changes constantly. A NoSQL database like MongoDB handles this well because it can store each user's activity as a flexible document without forcing every record into a same table format.

<img width="521" height="210" alt="image" src="https://github.com/user-attachments/assets/ac42c918-2452-4b4e-a27e-7b63180922a2" />


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

<img width="683" height="317" alt="image" src="https://github.com/user-attachments/assets/726c333f-27ae-41ef-a91f-64c0ba6cbeb1" />


# 13. HORIZONTAL SCALING

We saw that vertical scaling has a bottleneck.As you need to upgrade a single machine itself. To overcome this we have a concept known as 

Horizontal Scaling (also called scaling out) takes a completely different approach. Instead of making one server more powerful, you add more servers and distribute the load across them. Each server handles a portion of the incoming traffic such that no single machine is overwhelmed. If traffic grows further you simply add another server. There is no limit over here, you can keep adding machines as demand increases. This is why horizontal scaling is the preferred strategy for large-scale systems that is capable to serve millions of users.

### Real World Scenario:-

Our restaurant has upgraded its kitchen as much as physically possible, but orders are still piling up. Instead of trying to squeeze more into the same kitchen, the owner opens a second kitchen branch across town. Now orders are split between two kitchens. If demand grows even more, a third branch is opened. Each branch handles its own share of customers and together they serve far more people than a single location ever could.

### Technical Example:-

Netflix serves over 200 million users worldwide. It runs its application across hundreds of servers. When a user in India streams a movie then one server handles their request. When a user in the US streams at the same time, a different server handles theirs. If a new show launches and traffic spikes, Netflix spins up additional servers automatically to absorb the surge. Once the spike passes the extra servers are removed. This ability to scale in and out on demand is the core advantage of horizontal scaling.

<img width="989" height="327" alt="image" src="https://github.com/user-attachments/assets/a9c9f8cb-bc70-4cf5-b79c-686bebdae4ef" />


# 14. LOAD BALANCER

With horizontal scaling, we now have multiple servers handling incoming traffic. But there will be a question stating when a request comes in, who decides which server should handle it? If all requests accidentally go to one server while the others sit idle, horizontal scaling becomes pointless.

A Load Balancer is the component that is answer to the above question. It sits in front of all the servers and distributes incoming requests evenly across them, making sure no single server is overloaded while others are underutilized. If one server goes down, the load balancer detects it and stops sending traffic to it and routing requests to the remaining healthy servers instead.

Load Balancer does route this traffic to multiple servers by using few algorithms such as Round Robin, I.P Hashing, Least Connections etc.. 

### Real World Scenario:-

Our restaurant now has multiple order counters to handle the rush. But if there is no one managing the crowd then all customers might line up at the first counter while the other counters remain empty. To fix this the restaurant places a floor manager at the entrance. The floor manager looks at all the counters then sees which one has the shortest queue and directs each incoming customer to the least busy counter. This results every counter stays evenly loaded and customers get served faster. The floor manager is the load balancer.

### Technical Example:-

When you visit www.amazon.com, your request does not go directly to a single server. It first hits Amazon's load balancer. The load balancer checks which of the hundreds of backend servers is least busy at that moment and forwards your request over there. The next user's request might go to a completely different server. If one server crashes, the load balancer automatically removes it from the pool and redirects traffic to the others this cannot be noticed by the user.

Common load balancers used in production include NGINX, HAProxy and cloud-managed solutions like AWS Elastic Load Balancer (ELB).

<img width="621" height="317" alt="image" src="https://github.com/user-attachments/assets/fcd9f453-952b-4186-89d5-0cf6262369b4" />


# 15. INDEXING

As a database grows and stores millions of records, finding one specific piece of information can get very slow. Without any help the database would have to go through every single record one by one until it finds what you are looking for.

An Index solves this by acting as a shortcut. Think of it like a table of contents in a book instead of reading every page to find a topic, you check the table of contents, it tells you the exact page number and you jump straight there. An index in a database works the same way it helps the database skip straight to the data it needs without scanning everything.

### Real World Scenario:- 

Imagine our restaurant has a thick recipe binder with hundreds of recipes. The chef needs to find the recipe for "Potato Fry." Without any help, the chef would have to flip through every single page until finding it that could take a long time.

But the receipe book has an index page at the very front an alphabetical list of all dish names with their page numbers. The chef looks up "Potato Fry" sees it is on page 87 and opens directly to that page. The recipes themselves haven't changed the index just made finding the right one much faster.

### Technical Example:-

When you go to Amazon and search for "wireless headphones". Amazon's database has hundreds of millions of products stored. Without an index the database would check every single product one by one to see if the name matches that would take far too long.

Instead, Amazon keeps an index on the product names. When you search the database looks at the index first and quickly finds where "wireless headphones" is located and pulls up the results almost instantly. The index is the reason your search results appear in milliseconds instead of minutes.


# 16. REPLICATION

We saw that Indexing helps to speed up how fast the database finds data. But what happens when millions of users are reading from the same database at the same time? Even with indexes, a single database can only handle so many requests before it becomes a bottleneck. There is a risk, if one database crashes then all your data becomes inaccessible.

Replication solves both problems. It is the practice of creating and maintaining copies of your database across multiple servers. There is one primary database (also called as master database) and one or more replica databases (also called slave databases). All write operations such as inserts, updates, deletes happen on the primary database. All read operations are directed to the replica databases. This way, the primary is not occupied with handling both reads and writes at the same time and the read load is distributed across multiple replicas. Once the inserts/updates/deletes are performed in the primary database they are simply replicated to the replica databases such that it maintains uniformity across all the replica databases and primary database upto date.

If the primary database ever goes down one of the replica database can take over, ensuring your system stays available and no data is lost.

### Real World Scenario:-

Our restaurant's original branch has a master recipe book where all new recipes are added and existing ones are updated. But every branch also has a copy of that book for their chefs to read from.

Whenever a new recipe is created or an existing one is changed, it is written into the master book at the original branch and then copied to all the other branches. The chefs at the other branches never write into their book they only read from them. In this way the original branch is not flooded with calls from every chef asking for recipes and if the master book is ever damaged, the copies at the other branches still have the respective book and will be converted into a master book.

### Technical Example:-

A banking application has millions of customers checking their balances and transaction history throughout the day. If all those read requests hit the same database that is also processing new transactions (writes), it would slow down everything.

Instead, the bank uses one primary database for all writes such as every new transaction, every account update goes here. It then maintains two replica databases that are kept in sync with the primary. All read requests such as checking balances, viewing statements are routed to the replicas. This splits the traffic so no single database is overwhelmed, If the primary crashes then one of the replicas is promoted to become the new primary and the system continues without the customer ever noticing.


# 17. SHARDING

With replication, we create copies of the same data across multiple servers to handle more reads and provide backup. But what happens when the data itself becomes so massive that a single database cannot store it all? No matter how many replicas you create each one still holds the entire dataset, one machine simply cannot hold everything.

Sharding solves this by splitting the data itself across multiple databases. Instead of every database holding all the data each database holds only a portion of it. Each portion is called a shard. For example, you could split users by region such as users from Asia go to Shard 1, users from Europe go to Shard 2 and users from America go to Shard 3. Each shard is a separate database that is responsible for only its own slice of data. This means no single database has to store or process everything and the system can scale to handle enormous amounts of data. Sharding is done with the help of sharding key(such as primary key). It is also known as Horizontal Partitioning. The data here is split with the help of rows.

### Real World Scenario:-

Our restaurant has grown massively and now serves hundreds of dishes. One kitchen trying to handle every type of dish such as starters, main course, desserts, beverages is chaotic and slow.

So the owner decides to split the menu across specialized kitchens. Kitchen A handles only starters. Kitchen B handles only main course items. Kitchen C handles only desserts. Each kitchen stores only the recipes it is responsible for and handles only the orders related to its section. No single kitchen is overloaded with everything and each one works faster because it focuses on a smaller set of items. Each of those specialized kitchens is a Shard.

### Technical Example:-

A social media platform like Instagram has over a billion users. Storing all their profiles, posts and messages in a single database is simply not possible the data is too large for one machine.

Instead, Instagram shards its database by region. Users from India are stored in one database server, users from the US in another and  users from Europe in another. When a user from India logs in the system knows to query the India shard directly such as it never touches the US or Europe shards. This keeps each database smaller, faster and more manageable. As the user base grows in a new region, a new shard is simply added for that region.


# 18. VERTICAL PARTITIONING

With sharding, we split the data by rows in different groups of records that go to different databases. But there is another way to split data by columns. That is Vertical Partitioning.

Instead of keeping all the information about something in one place, vertical partitioning separates it into groups based on what is accessed together. Columns that are frequently used are kept in one table or database and columns that are rarely used are of very large in size and are moved to a separate one. This way, when the system needs to read the commonly accessed data, it does not have to load all the heavy, rarely needed data along with it making queries faster and more efficient.

### Real World Scenario:-

In our restaurant, each recipe in the book contains two things, the cooking steps and the full ingredient list with supplier details. The chef uses the cooking steps every single time an order comes in but the ingredient and supplier details are only needed once a week when restocking.

So the owner splits the book into two. One book has just the cooking steps which is light, quick to flip through and used constantly. The other book has the ingredient and supplier details that are heavier but only pulled out when needed. The chef's daily work becomes faster because the book on the counter only contains what is needed in the moment.

### Technical Example:-

An e-commerce website like Flipkart stores product information such as name, price, category, description and high-resolution images. Every time a user browses the product listing page, the system only needs the name, price and category. The large description and heavy images are only needed when the user clicks into a specific product.

With vertical partitioning, the product table is split. One table stores name, price and category which resembles small, fast to query and accessed on every page load. A separate table stores description and images that are larger in size but only queried when a user opens a specific product page. This keeps the frequently accessed table lean and fast.


# 19. CACHING

Every time the server needs data, going all the way to the database takes time. But what if the same data is being requested again and again like a popular product page or a trending post? Querying the database every single time for the same result is wasteful and slow.

Caching solves this by storing frequently accessed data in a fast, temporary layer that sits between the server and the database. When a request comes in, the server checks the cache first. If the data is there (called a cache hit), it is returned immediately without touching the database. If the data is not there (called a cache miss), the server fetches it from the database and then returns it to the client and also stores a copy in the cache so the next request for the same data is faster.

Caches are much faster than databases because they store data in memory (RAM) rather than on disk. The trade-off is that cache storage is limited and temporary such as it is not meant to replace the database, just to speed up repeated access to the same data.

A common question that arises after understanding the above trade-off is: if the data stored in the cache is temporary, what happens to it after some time? To manage this, cache systems use a concept called TTL (Time To Live). TTL defines how long a particular piece of data can remain in the cache. Once the specified TTL duration expires, the data is automatically removed from the cache and will no longer be available.

Redis is one of the most used cache in real time.

### Real World Scenario:-

During dinner time at a restaurant, the chef notices that 8 out of 10 orders are for the same five popular dishes. Instead of going to the storage room every single time to fetch ingredients, the chef sets up a prep station right next to the stove with pre-chopped vegetables, spices and pre-portioned sauces for those five dishes. Now when an order comes in for a popular dish everything is already within near distance and no trip to the storage room needed.

That prep station is the cache. It holds the most commonly needed items close by so the chef can work faster. If someone orders a rare dish that is not on the prep station, the chef goes to the storage room (the database), fetches what is needed and may even add it to the prep station if it starts getting ordered frequently.

### Technical Example:-

1) When millions of users visit a celebrity's Instagram profile, the server does not query the database for the same profile data every single time. The first time the profile is requested, the server fetches it from the database and stores a copy in a cache like Redis. For every subsequent request the server checks Redis first and finds the data is already there and returns it instantly without ever touching the database.

This is why popular pages load just as fast no matter how many people are viewing them at the same time. The database is only hit once and the cache handles the rest.

2) This scenario helps in understanding how cache works in real-time applications.

Suppose you will open the PhonePe application and check your account balance. The system fetches the balance from the database, 
For example Rs.49000 and stores this result temporarily in the cache for faster future access. Now, within a few seconds Rs. 1000 gets credited to your bank account. Ideally, your updated balance should now be Rs.50000. However, when you check the balance again, the application may fetch the old value (Rs.50000) from the cache instead of querying the database again. This happens because the cached data has not yet expired. 

In this challenging scenario there have been few cache consistent strategies to avoid such kind of race condition. One of it is the most common one known as Cache-Aside Pattern. This pattern ensures that once the database update is successful, the cache is either updated with the latest value internally or the existing cached data is invalidated (removed). During the next read operation, the latest data is fetched and stored back into the cache.


# 20. NORMALIZATION - DENORMALIZATION

When storing data in a database, you have to decide how to organize it. There are two approaches.

1) Normalization
2) Denormalization

Normalization means splitting your data across multiple tables to avoid repetition. Each piece of information is stored only once and tables reference each other when they need related data. This keeps the data clean, consistent and easy to update but when you need to read something, the database may have to look across several tables and join them together which can be slower.

Denormalization is the opposite. It means combining related data back into a single table, even if that causes some information to be repeated. This makes reading faster because the database can grab everything it needs from one place without joining multiple tables but updating becomes harder because the same data may exist in more than one place and all copies need to stay in sync.

In short, Normalization prioritizes clean and organized storage. Denormalization prioritizes fast reads.

### Real World Scenario:-

In our restaurant, every recipe uses ingredients from various suppliers. 

The normalized approach is to keep a separate supplier list of each recipe just mentions the ingredient name and if you need supplier details, you look them up in the supplier list. Clean and no repetition but you have to check two places every time.

The denormalized approach is to write the supplier name and phone number directly on every recipe page that uses their ingredients. Now the chef has everything on one page without flipping anywhere else faster to read but if a supplier changes their phone number then you have to update it on every single recipe page where it appears.

### Technical Example:-

An online store has a table for orders and a separate table for customer details. In a normalized setup, the orders table only stores the customer ID. To display an order with the customer's name and address the database has to join both tables which is accurate but takes more time.

In a denormalized setup, the customer's name and address are stored directly inside the orders table alongside each order. Now displaying an order is instant with one table and one query. But if the customer updates their address then it has to be changed in every order record where it was copied.

Systems that need strict accuracy like banking uses Normalization.
Systems that need fast reads at massive scale like news feeds or dashboards often uses Denormalization. 


# 21. CAP THEOREM

When you build a system that stores data across multiple servers (which we do with replication and sharding), three things become very important:

Consistency (C) — Every server in the system has the exact same, most up-to-date data at all times. If a user updates their profile on one server, every other server should immediately reflect that change. No matter which server you ask, you always get the same answer.

Availability (A) — The system always responds to every request, no matter what. Even if something goes wrong internally, the user never sees an error or a blank page they always get a response.

Partition Tolerance (P) — The system continues to work even if the connection between servers breaks down. In a real-world network, servers communicate with each other constantly. A "partition" happens when that communication is disrupted and one server can no longer talk to another. Partition tolerance means the system does not collapse when this happens.

The CAP Theorem states that in any distributed system you can only guarantee two out of these three at the same time but never all three. When a network partition happens (and in real systems, it eventually will), you are forced to make a choice: do you prioritize consistency (make sure data is correct, even if it means some requests are rejected) or availability (make sure every request gets a response, even if the data might be slightly outdated)?

This is not a design flaw, it is a fundamental rule of how distributed systems work.

### Real World Scenario:- 

A restaurant has two kitchen branches, Branch A and Branch B. They share the same menu and keep each other updated over a phone line. If a dish is removed from the menu at Branch A they call Branch B to update them.

Now imagine the phone line goes down (this is the partition). A customer at Branch B orders a dish that Branch A just removed from the menu. Branch B has no way to know about the change. Now the restaurant has two choices:

Choose Consistency:- Branch B says, I'm not sure if this dish is still available. Let me not serve it until, I can confirm with Branch A.The customer gets no food (the request is rejected) but the restaurant avoids serving something that is no longer on the menu.

Choose Availability:- Branch B says, I will serve what I have on my current menu. The customer will get their food (the request is fulfilled) but there is a chance the dish is outdated and no longer supposed to be served.

Neither option is wrong, it depends on what matters more for that restaurant.

### Technical Example:-

A banking application cannot show a wrong account balance. If a user transfers money and one server has not yet received the update, showing the old balance could lead to double spending. So banks choose Consistency over Availability, if the servers cannot confirm they are in sync, the system will reject the request or show an error rather than display incorrect data. This is a CP [Consistent - Partition] system.

A social media feed like Twitter prioritizes keeping the experience alive. If one server has not received the latest tweet yet, it is perfectly acceptable to show the feed without it, the tweet will appear a few seconds later. Twitter chooses Availability over Consistency, every request gets a response even if the data is slightly behind. This is an AP [Availability - Partition] system.

In both cases, Partition Tolerance is always present because network failures are unavoidable in the real world. The real decision is always between Consistency and Availability.


# 22. BLOB STORAGE

We know that databases are great for storing structured data like names, emails, prices and timestamps. But what about large files like images, videos, audio files or PDFs?

These files can be massive in size and databases are simply not designed to store and serve them efficiently.

This is where Blob Storage comes in. Blob stands for Binary Large Object. Blob storage is a specialized storage system built specifically for storing large unstructured files. Instead of putting a video or an image inside your database, you upload it to blob storage and store just the link (URL) to that file in your database. When the application needs to display the file it uses the link to fetch it directly from blob storage.

### Real World Scenario:- 

Our restaurant's kitchen has shelves for everyday items such as spices, sauces, utensils. These shelves are organized and are easy to access. But the kitchen also receives bulk supplies such as 50 kg of rice, boxes of vegetables, large tins of oil. Trying to fit all of that on the kitchen shelves would make everything cluttered and slow to navigate.

So the owner rents a separate warehouse nearby for all the bulk items. The kitchen shelves only keep a note like "Rice: Warehouse, Shelf 3, Row B." When the chef needs rice, they check the note and fetch it from the warehouse. The kitchen stays clean and organized and the warehouse handles the heavy storage.

That warehouse is Blob storage. The note on the kitchen shelf is the URL stored in the database.

### Technical Example:- 

When you upload a video to YouTube then that video file could be several gigabytes in size. YouTube does not store the actual video inside a database. Instead, the video is uploaded to Google Cloud Storage (a blob storage service). The database only stores the video's metadata such as title, description, upload date and the URL pointing to where the video file lives in cloud storage. When someone watches the video, the browser uses that URL to stream the file directly from blob storage.

Common blob storage services include Amazon S3, Google Cloud Storage and Azure Blob Storage.


# 23. CDN

We know that large files like images and videos are stored in blob storage and we know from the latency concept that farther the user is from the server, the longer it takes to get a response. So if your blob storage is in the US and a user is in India requests a video, that file has to travel thousands of miles which will be resulting in slow load times.

A CDN (Content Delivery Network) solves this by placing copies of your files on multiple servers spread across different locations around the world. These servers are called edge servers. When a user requests a file, instead of fetching it from the original server far away, the CDN delivers it from the nearest edge server which is the one closest to the user's location. This will reduce latency and makes content load much faster.

CDNs are especially useful for serving static content such as images, videos, CSS files, JavaScript files etc that does not change with every request.

### Real World Scenario:- 

Our restaurant is based in one location, but customers from all across the city are ordering the same popular dishes for takeaway. If every single order has to be prepared and delivered from the original kitchen, customers on the far side of the city will wait much longer than those nearby to the restaurant.

To fix this, the owner sets up small satellite food counters in different parts of the city. Each counter keeps a stock of the most popular dishes that are ready to serve. When a customer places an order, it will be provided by the nearest counter instead of the main kitchen. The food reaches the customer faster and the main kitchen is not overwhelmed with every single order.

Those satellite counters are the CDN edge servers.

### Technical Example:-

When a user in Mumbai opens Netflix and presses play on a movie, the video does not stream all the way from Netflix's main servers in the US. Netflix uses a CDN to store copies of popular movies and shows on edge servers located in cities around the world that will include servers near Mumbai. The video streams from the nearest edge server, so it starts playing almost instantly with minimal buffering.

Popular CDN providers include Cloudflare, AWS CloudFront and Akamai.


# 24. WEB SOCKETS

With HTTP communication follows a strict pattern where the client sends a request, the server sends back a response and the connection is closed. If the client wants new data, it has to send another request. The server can never reach out to the client on its own, it can only respond when asked.

This works fine for loading a webpage or fetching search results, but what about applications that need real-time and instant communication such as chat app, a live score update or a multiplayer game. Having the client constantly ask the server "Any new messages? Any new messages? Any new messages?" every second is not the efficient approach to perform.

WebSockets solve this by opening a persistent, two-way connection between the client and the server. Once the connection is established, both sides can send data to each other at any time without waiting for the other to ask first. The connection stays open for as long as needed, and data flows freely in both directions — instantly.

