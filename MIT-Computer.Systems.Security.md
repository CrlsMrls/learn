MIT-Computer.Systems.Security.md


MIT 6.858 Computer Systems Security, Fall 2014
https://www.youtube.com/playlist?list=PLUl4u3cNGP62K2DjQLRxDNRi0z2IRWnNh
https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-858-computer-systems-security-fall-2014/readings/
23 videos - 1h20'


# Threads Models

En seguridad siempre el weakest link es quien define la seguridad del sistema
Por ejemplo, en iCloud se olvidaron de cancelar o añadir delay a los wrong password requests en solo uno de sus servicios online. 
El resultado es que el sistema entero se vio comprometido.

A veces un sistema puede parecer seguro pero en conjunto con otros sistemas no lo es.
Por ejemplo, si para resetear un correo de gmail, reenvia el reset a .me de icloud que hace que el reset de la contraseña sea más sencillo.

# Web Security Model

## Same-origin policy
**Goal:** Two websites should not be able to tamper each other

**Strategy:** each resource is assigned origin.JS so it can only access resources from its own origin.

**Origin:** scheme + hostname + port

**Implementation:**
* each resource has client-side resources: DOM storage, DOM tree, JS resources, cookies, etc.
* each frame gets the origin from its URL
* Passive content gets zero authority 

Different origin domains can communicate only through postMessage 

DOM - is a representation of the HTML content in JS


## Cross-site request forgery (CRSF)

### XMLHttpRequest 
Same origin, unless the cors header is enabled:
Access-Control-Allow-Origin: foo.com


## Cross-site Scripting (XSS)
XSS attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted web sites.

Ways to resolve it:

### Sanitize inputs
By constraining expressivity you can improve security

### Content Security Policy (CSP) 
CSP is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. 
TODO https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP

## SQL Injection
Inject some SQL query into an untrasted variables that executes SQL in DB.

### Sanitize
Escape dangerous chars

### Data layer
Data layers already implement sanitization 

## Cookies stealing
Are sent in every http request 
https://publicsuffix.org/list/

Be careful with shared domains, they access to cookies.

### Stateless cookies
Authenticate every request 
Message authentications codes: hash key and message => H(k,m)

### DOM storage
It is much easier to protect, since only exactly the same full domain can access them.

### Use X.509 certificates
There is no JS cannot access these certificates.
The problem is user has to install them. UX is really bad.

## Covert channel attacks

# Network security
## TCP sequence prediction attack
The attacker hopes to correctly guess the sequence number to be used by the sending host.
Finding the SYN (Sequence Number) of another stablished connection, so an attacker can supplant others IP

### Problems
* IP as authentication, like rlogin
* Resetting others session, like BGP routing protocol
* Data injection in a stablished connection

### Solutions
* Blocking internal IP comming from outside 
* TTL counter to 255, when direct connection (eg. BGP)
* Sequence is for each ip: SYN = SYNold + Hash(ip, port, secret key) 

## DNS 
Fake DNS response was quite easy, by injecting a packet earlier than valid DNS query.

Now the origin port is random, and there is also a DNS query id, that is used in the returned packet.

NSEC for signing non-existing DNS records.

## SYN flooding
Connection 




## DNS

