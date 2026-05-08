# How the Web Works

## DNS in Detail

### What is DNS?

DNS (Domain Name System) provides a simple way for us to communicate with devices on the Internet without remembering complex numbers.

Instead of remembering `104.26.10.229`, you can remember `tryhackme.com` instead.

---

## Domain Hierarchy

### TLD (Top-Level Domain)

A TLD is the most right-hand part of a domain name.
- Example: the `tryhackme.com` TLD is `.com`

**Two types of TLD:**
1. **gTLD** (Generic Top Level)
2. **ccTLD** (Country Code Top Level Domain)

- A **gTLD** was meant to tell the user the domain name's purpose. For example, `.com` would be for commercial purposes.
- A **ccTLD** was used for geographical purposes. For example, `.ca` for sites based in Canada.

### Second Level Domain

Taking `tryhackme.com` as an example, the `.com` part is the TLD and `tryhackme` is the Second Level Domain.

- Limited to **63 characters** + the TLD.
- Can use **a–z**, **0–9**, and **hyphens**.

### Subdomain

A subdomain sits on the left-hand side of the Second-Level Domain, using a period to separate it.
- Example: in `admin.tryhackme.com`, the `admin` part is the subdomain.
- Length must be kept to **253 characters or less**.

---

## DNS Record Types

Multiple types of DNS records exist.

### A Record
These records resolve to **IPv4 addresses**.
- Example: `104.26.10.229`

### AAAA Record
These records resolve to **IPv6 addresses**.
- Example: `2606:4700:20::681a:be5`

### CNAME Record
These records resolve to **another domain name**.
- Example: TryHackMe's online shop has the subdomain `store.tryhackme.com` which returns a CNAME record of `shops.shopify.com`. Another DNS request would then be made to `shops.shopify.com` to work out the IP address.
# DNS Record Types (Continued)

### MX Record
These records resolve to the address of the servers that handle the **email** for the domain you are querying.
- Example: an MX record response for `tryhackme.com` would look something like `alt1.aspmx.l.google.com`.

### TXT Record
TXT records are **free text fields** where any text-based data can be stored.

---

## What Happens When You Make a DNS Request

1. When you request a domain name, your computer first checks its **local cache**.

2. A **Recursive DNS Server** is usually provided by your ISP, but you can also choose your own. If the request cannot be found locally, a journey begins to find the correct answer, starting with the Internet's **root DNS servers**.

3. The **root servers** act as the backbone of the Internet. Their job is to redirect you to the correct Top Level Domain server, depending on your request.
   - Example: if you request `www.tryhackme.com`, the root server will recognise the Top Level Domain of `.com` and refer you to the correct TLD server that deals with `.com` addresses.

4. The **TLD server** holds records for where to find the **authoritative server** to answer the DNS request.

5. An **authoritative DNS server** is the server responsible for storing the DNS records for a particular domain name, and where any updates to your domain name DNS records would be made.
   - DNS records all come with a **TTL (Time to Live) value**.
# HTTP in Detail

## What is HTTP(S)?

**HTTP** (Hyper Text Transfer Protocol) is what is used whenever you view a website, developed by **Tim Berners-Lee** and his team between **1989–1991**.

HTTP is the set of rules used for communicating with web servers for the transmitting of web page data, whether that is HTML, Images, Videos, etc.

---

**HTTPS** (Hyper Text Transfer Protocol Secure) is the **secure version** of HTTP.

HTTPS data is **encrypted** so it:
- Stops people from seeing the data you are receiving and sending.
- Gives you assurance that you're talking to the **correct web server** and not something impersonating it.

---

## Requests and Responses

When we access a website, you need to tell the browser specifically how and when to access their resources — this is where **URLs** will help.

### What is a URL? (Uniform Resource Locator)

A URL is predominantly an instruction on how to access a resource on the Internet.

```
http://user:password@tryhackme.com:80/view/room?id=1#task3
  ↑         ↑              ↑          ↑     ↑       ↑       ↑
Scheme     User        Host/Domain  Port  Path  Query   Fragment
                                               String
```

| Component | Description |
|-----------|-------------|
| **Scheme** | What protocol to use for accessing the resource, such as HTTP, HTTPS, FTP (File Transfer Protocol). |
| **User** | Some services require authentication to log in; you can put a username and password into the URL to log in. |
| **Host** | The domain name or IP address of the server you wish to access. |
| **Port** | The port that you are going to connect to. |
| **Path** | The file name or location of the resource. |
| **Query String** | Extra bit of information that can be sent to the requested path. |
| **Fragment** | A reference to a location on the actual page requested. |

---

## HTTP Methods

HTTP methods are a way for the client to show their **intended action** when making an HTTP request.

| Method | Description |
|--------|-------------|
| **GET** | Used for getting information from a web server. |
| **POST** | Used for submitting data to the web server and potentially creating new records. |
| **PUT** | Used for submitting data to a web server to update information. |
| **DELETE** | Used for deleting information/records from a web server. |
# HTTP Status Codes

When an HTTP server responds, the first line always contains a **status code** informing the client of the outcome of their request.

These status codes can be broken down into **5 different ranges**:

| Range | Category |
|-------|----------|
| 100–199 | Information Response |
| 200–299 | Success |
| 300–399 | Redirection |
| 400–499 | Client Errors |
| 500–599 | Server Errors |

---

## Common HTTP Status Codes

| Code | Meaning |
|------|---------|
| **200** | OK |
| **201** | Created |
| **301** | Moved Permanently |
| **302** | Found |
| **400** | Bad Request |
| **401** | Not Authorised |
| **403** | Forbidden |
| **404** | Page Not Found |
| **405** | Method Not Allowed |
| **500** | Internal Server Error |
| **503** | Service Unavailable |

---

## Headers

Headers are **additional bits of data** you can send to the web server when making requests.

### Common Request Headers

These are headers sent from the **client** (usually your browser) to the server.

| Header | Description |
|--------|-------------|
| **Host** | Some web servers host multiple websites, so by providing the host header you can tell it which one you require. |
| **User-Agent** | Your browser software and version number. |
| **Content-Length** | Tells the web server how much data to expect in the web request. |
| **Accept-Encoding** | Tells the web server what types of compression methods the browser supports so the data can be made smaller for transmitting over the internet. |
| **Cookie** | Data sent to the server to help remember your information. |
# Common Response Headers

These are the headers returned to the **client** from the **server** after a request.

| Header | Description |
|--------|-------------|
| **Set-Cookie** | Information to store which gets sent back to the web server on each request. |
| **Cache-Control** | How long to store the content of the response in the browser's cache before it requests it again. |
| **Content-Type** | Tells the client what type of data is being returned. |

---

## Cookies

Cookies can be used for many purposes but are most commonly used for **website authentication**.

It is in the form of a **token** (unique secret code that isn't easily humanly guessable).

---

# How Websites Work

When you visit a website, your browser (like Safari or Google Chrome) makes a request to a web server asking for information about the page you're visiting.

A web server is just a **dedicated computer** somewhere else in the world that handles your requests.

```
Browser  --[Request from browser]-->  Internet  --[Request from browser]-->  Server
         <--[Response from server]--            <--[Response from server]--
```

---

## Two Major Components of a Website

1. **Front End (Client Side)** — The way your browser renders a website.
2. **Back End (Server Side)** — A server that processes your request and returns a response.

---

## HTML (Hyper Text Markup Language)

HTML is the language websites are written in.

- **HTML** — To build websites and define their structure.
- **CSS** — To make websites look pretty by adding styling options.
- **JavaScript** — Implement complex features on pages using interactivity.
# Putting It All Together

When you request a website, your computer needs to know the server's **IP address** it needs to talk to. For this, it uses **DNS**.

Your computer then talks to the web server using a special set of commands called the **HTTP protocol**. The web server then returns HTML, JavaScript, CSS, etc. which your browser uses to correctly format and display the website to you.

```
Request website   -->   Find web server IP   -->   Connect to   -->   View
in your browser         address with DNS           server             website
```

---

## Load Balancers

Load balancers provide **two main features**:
1. Ensuring high traffic websites can **handle the load**.
2. Providing a **failover** if a server becomes unresponsive.

Load balancers also perform **periodic health checks** with each server to ensure they are running correctly.

---

## CDN (Content Delivery Networks)

A CDN can be an excellent resource for **cutting down traffic** to a busy website.

---

## Databases

Web servers can communicate with **databases** to store and recall data from them.

---

## WAF (Web Application Firewall)

A WAF sits between your web request and the web server. Its primary purpose is to **protect the web server** from hacking or denial of service attacks.

---

## What is a Web Server?

A web server is a software that **listens for incoming connections** and then utilises the HTTP protocol to deliver web content to its clients.

The most common web server software you'll come across:
- **Apache**
- **Nginx**
- **IIS**
- **Node.js**

### Virtual Hosts

Web servers can host **multiple websites** with different domain names; to achieve this, they use **virtual hosts**.
