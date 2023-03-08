# http-and-https-honeypot
The web equivalent of slamming a door shut. Has the capability of printing the incoming request for logging reasons.

## What is this for?

Just some experiment in python3 to get rid of bots by simply closing the connection. This is used with sniproxy in a manner that sends every incoming connection without a domain- or hostname into the void.

Since HTTPS-servers require a cert, our honeypot may use a self-signed one as the bots do not care anyways.

```
mkdir dummy
cd dummy
openssl ecparam -genkey -name secp384r1 -out secret.key
openssl req -new -x509 -sha256 -key secret.key -out cert.crt -days 3650
```
or
```
mkdir dummy
cd dummy
openssl req -new -x509 -nodes -newkey ec:<(openssl ecparam -name secp384r1) -keyout secret.key -out cert.crt -days 3650
```

## Used with
https://github.com/ran-sama/sniproxy-tutorial

## License
Licensed under the WTFPL license.
