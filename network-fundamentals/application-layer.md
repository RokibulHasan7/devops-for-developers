# Application Layer

- The main job of the application layer is to enable end-users to access the Internet via a number of applications.
- Client-Server Architecture: Consists of two parts. One is client-side software and server-side software. These 
  pieces of software are generally called processes, and they communicate with each other through messages.
- Peer-to-Peer Architecture(P2P): In this architecture, applications on end-systems called ‘peers’ communicate with each 
  other. No dedicated server or large data center is involved. Peers mostly reside on PCs like laptops and desktops in 
  homes, offices, and universities. The key advantage of the P2P architecture is that it can scale rapidly - without
  the need of spending large amount of money, time or effort. Each peer can be categorized as servers or clients.
- ```BitTorrent``` are based on P2P architecture. When a file is downloaded via BitTorrent, the downloading party 
  accesses ```bits``` of the file on several other user's computers and puts them together on its end. No traditional
  'server' is involved in this scenario.
- ```P2P is not the same as File Sharing.``` P2P is a design principle for distributed systems and an application architecture.
- Example of P2P: Streaming media, telephony, content distribution, routing and volunteer computing.
- ```Hybrid``` architecture involves server involvement to some degree. It's a combination of the P2P and client-server
  architecture.
- ```P2P networks are extremely mathematically scalable.``` The resources of a P2P system grows with the number of peers in the system. 
  Thus, applications with P2P architecture are self-scaling.
- Program vs Process vs Thread
    - A program is simply an executable file. An application such as MS Word is one example.
    - A process is any currently running instance of a program. So one program can have several copies of it running at once. 
      One MS Word program can have multiple open windows.
    - A thread is a lightweight process. One process can have multiple running threads. The difference between threads 
      and processes is that threads do lightweight singular jobs.
- The interface between a process and the computer network is called a ```socket```. Socket do not have anything to do
  with hardware - they are software interface. Process simply direct their messages to sockets.
- Socket is a combination of the IP address and a Port number. 
- URLs(Universal Resource Locator) consist of the following parts:
    - Protocol in use
    - The hostname of the server
    - The location of the file
    - Arguments to the file
- HTTP is a ```stateless protocol```. Servers do not store any information about clients by default.
- HTTP uses TCP as its underlying transport protocol so that messages are guaranteed to get delivered in
  order. 
- TCP is connection-oriented, meaning a connection has to be initiated with servers using a series of
  starting messages. Once the connection has been made, the client exchanges messages with the server
  until the connection is officially closed by sending a few ending messages.
- Types of HTTP connections:
  - Non-persistent HTTP connections.
    - Non-persistent HTTP connections use ```one TCP connection per request```. 
    - The underlying TCP connection requires three TCP messages are sent between the client and
      server. Similarly, when the connection is closed, three TCP messages are sent back and forth
      between the client and server.
  - Persistent HTTP connections.
    - An HTTP session typically involves multiple HTTP request-response pairs, for which separate
      TCP connections are established and then torn down between the same client and server.
    - This is ```inefficient```.
    - Typically, if there have been no requests for a while, the server closes the connection. The duration 
      of time before the server closes the connection is configurable.
- The HTTP Request line consists of three parts:
  - Method
  - URL
  - Version
- Most forms are sent from the POST method, the GET method is also used sometimes with the entries of 
  the form appended to the URL. However, sending forms with a POST request is generally better because:
  - The amount of data that can be sent via post request is unlimited.
  - The form's fields are not shown in the URL.
- URI: Uniform Resource Identifiers, it can be more specific than URLs in such a way that they can locate
  fragments within objects too.
- URL: Uniform Resource Locators, it used to identify an object over the web. This is the location
  that any HTTP method is referring to.
- Important HTTP headers:
  - ```Host```
  - ```connection```
  - ```user-agent```
  - ```Accept-language```
  - ```Accept```
- HTTP Response Message:
  - It has 3 parts: an initial ```status line```, some ```header lines``` and an ```entity body```.
  - **HTTP response messages don't have the URL or the method fields. Those are for request message.
  - There are a lot of status code:
    - 1xx codes fall in the informational category.
    - 2xx codes fall in the success category.
    - 3xx codes are for redirection.
    - 4xx is client error.
    - 5xx is server error.
  - Header Lines:
    - Connection type
    - Date
    - Server
    - Last Modified
    - Content Length
    - Content Type
  - How HTTP headers are chosen?
    - It depends on a complex mix of factors such as the browser, the user configuration and products.
- ```cURL``` stands for **Client URL**.
- Cookies are ```set by the server through HTTP headers``` when the client first navigates to the website.
- The Cookie file contains:
  - The website's domain
  - The string value of the cookie
  - The data that the cookie expires
- If a website has stored a cookie on your browser, ```it knows exactly when you visit it, what pages you visit and in what order```.
- ```Third-party cookies are cookies set for domains that are not being visited.```
- Example of Third party cookies:
  - A user visits amazon.com.
  - A cookie for free-stats.com is subsequently set on their browser because free-stats has placed 
    an advertisement on Amazon. Notice that this is a third-party cookie!
  - Suppose, the user visits ebay.com, and eBay also has placed an advertisement for free-stats.com.
  - The same cookie set on the Amazon site will be reused and sent to free-stats along in an HTTP 
    request with the name of the host that the user is on.
  - Free-stats can in this way track every website the user visits that they are advertising on 
    and create more targeted ads in order to generate greater revenue.
- ```discuss.educative.io```: io is top-level domain, educative is second-level domain and discuss is sub-domain.
- Local DNS cache is done via an entity called the ```local resolver library```, which is part of the OS. The application
  makes an API call to this library. If the local resolver library does not have a cached answer for the client, it 
  will contact the organization’s local DNS server. 
- Local DNS server is typically configured on the client machine either using a protocol called DHCP or can be 
  configured statically.


