# HTTP 

Topics:
Chapter 5 Web Servers
Chapter 6 Proxies
Chapter 7 Caching
Chapter 11 Client Identification and Cookies
Chapter 12 Basic Authentication
Chapter 13 Digest Authentication
Chapter 14 Secure HTTP
Chapter 20 Redirection and Load Balancing

## Some definitions

* Web server: http server
* Web client: browser
* Web resources: web content (i.e. HTML files, images, JS files, etc)

## Media types

`Content-Type` entity header is used to indicate the content type of the resource.

In requests, (such as POST or PUT), the client tells the server what type of data is actually sent.

### MIME (Multipurpose Inernet Mail Extensions) types
* Texts: **text/html**, **text/plain** (unknown textual data), text/javascript, **text/css** (CSS resources are ignored if not defined like this)
* Images: image/jpeg or image/gif
* Video: video/ogg, video/webm
* Audio: audio/mpeg, audio/wav
* Application: application/pdf, application/xml, **application/octet-stream** (unknown binary file)
* Multipart:  multipart/form-data (a completed HTML Form)

### MIME sniffing
In the absence of a MIME type, some browser guess the correct MIME type.
Servers can block MIME sniffing by sending the `X-Content-Type-Options: nosniff` along the `Content-Type`.




