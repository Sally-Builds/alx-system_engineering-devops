# Web Infrastructure Design

## 0) Simple Web stack
A lot of websites are powered by simple web infrastructure, a lot of time it is composed of a single server with a LAMP stack.

On a whiteboard, design a one server web infrastructure that hosts the website that is reachable via www.foobar.com. Start your explanation by having a user wanting to access your website.

Requirements:

    You must use:
        1 server
        1 web server (Nginx)
        1 application server
        1 application files (your code base)
        1 database (MySQL)
        1 domain name foobar.com configured with a www record that points to your server IP 8.8.8.8
* **Server**:
    A server is a computer or software program that provides functionality or services to other programs or devices, known as clients, over a network. Servers can range from simple file servers that store and distribute files to complex web servers that deliver web pages and applications to users.
  <br />
  <br />
* **Role of the Domain Name**:
    A domain name is a human-readable address used to identify a specific location on the internet, typically associated with a website. It provides a more user-friendly way to access resources on the internet than using numerical IP addresses. The domain name system (DNS) translates domain names into IP addresses, allowing users to access websites by typing in familiar names rather than complex strings of numbers.
  <br />
  <br />
* **Type of DNS Record for www.foobar.com**:
  The DNS record for www.foobar.com typically includes a "CNAME" (Canonical Name) record. A CNAME record is used to alias one domain name to another, allowing the www subdomain to point to the same location as the root domain (foobar.com). This aliasing simplifies maintenance and ensures that both www.foobar.com and foobar.com point to the same web server or hosting infrastructure.
  <br />
  <br />
* **Role of the Web Server**:
    The web server is responsible for handling HTTP requests from clients (web browsers) and serving web pages and other web-related content in response. It processes requests for web resources, retrieves the requested files from storage, and sends them to the client's browser for display.
  <br />
  <br />
* **Role of the Application Server**:
    The application server is responsible for executing application logic and processing dynamic content requested by clients. It handles tasks such as running server-side scripts, interacting with databases, and performing calculations or other operations required to generate dynamic web pages or deliver application-specific functionality.
  <br />
  <br />
* **Role of the Database**:
    The database stores and manages data used by the application server and other components of the infrastructure. It provides a structured way to organize and retrieve data, allowing applications to store and access information efficiently. In a web application context, databases are commonly used to store user accounts, content, preferences, and other persistent data.
<br />
<br />
* **Server Communication with User's Computer**:
    The server communicates with the user's computer over the internet using various network protocols, primarily HTTP (Hypertext Transfer Protocol) for web communication. When a user requests a website, their web browser sends an HTTP request to the server, specifying the desired resource (e.g., a web page). The server processes this request, retrieves the requested resource or generates a response dynamically, and sends it back to the user's browser over the internet using HTTP. This communication occurs over TCP/IP (Transmission Control Protocol/Internet Protocol) networks, which handle the transmission of data packets between devices on the internet.


### Issues with this Infrastructure design

* **Single Point of Failure (SPOF)**:
        Since all components are hosted on a single server, any failure of that server (hardware, software, or network) would result in the entire website becoming inaccessible. This represents a single point of failure.
  <br />
  <br />
* **Downtime During Maintenance**:
        Performing maintenance tasks, such as deploying new code or updating server software, requires restarting the web server (Nginx). During this time, the website will be unavailable to users, resulting in downtime.
  <br />
  <br />
* **Limited Scalability**:
        This infrastructure may struggle to handle significant increases in traffic since it relies on a single server. Scaling horizontally (adding more servers) becomes challenging due to the tightly coupled nature of the components on a single server. This limitation hampers the ability to accommodate high traffic loads effectively.