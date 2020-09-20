# TLSTun

TLSTun is a [Go](http://golang.org/) client server application to tunnel through highly intelligent
firewalls.


The client will connect to the server component over a [WebSocket](http://www.rfc-editor.org/rfc/rfc6455.txt).
All client connections are then muxed over the WebSocket
to the server which connects the to a [Socks5](https://en.wikipedia.org/wiki/SOCKS) proxy.
The server then proxies the connection from the mux to the real
destination.

This will punch through firewalls that do actual inspection of
traffic.


### SEE ALSO
* [tlstun certificate](doc/tlstun_certificate.md)	 - Generate certificates
* [tlstun client](doc/tlstun_client.md)	 - Start TLSTun client
* [tlstun server](doc/tlstun_server.md)	 - Start TLSTun server
* [tlstun version](doc/tlstun_version.md)	 - Print the version number of TLSTun

### TODO:
- add passthrough functionality to server to allow running it in front of an existing
webserver

### BUILD
go get github.com/jsimonetti/tlstun/cli
go build -o tlstun main.go

### CA

openssl genrsa -out rootca.key 4096

openssl req -sha256 -new -x509 -days 1826 -key rootca.key -out rootca.crt

tlstun certificate ca --certfile ./rootca.crt --keyfile ./rootca.key --cacert ./ca.crt --cakey ./ca.key

Contributions to this project are welcomed!
