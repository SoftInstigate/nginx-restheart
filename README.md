# RESTHeart and NGINX with SSL

This repository shows an example of NGINX as a SSL frontend for [RESTHeart](https://github.com/SoftInstigate/restheart/).

It uses Docker images to setup a complete stack made with NGINX, RESTHeart and MongoDB.

NGINX acts as a HTTPS reverse proxy for RESTHeart and it uses a self-signed certificate for the SSL connection.

To create the stack:

```bash
docker-compose up
```

To test that it works with `curl`:

```bash
curl --insecure https://localhost/ping

Greetings from RESTHeart!
```

The `--insecure` parameter is necessary because we are using a self-signed certifcate.

To test that it works with `http`:

```bash
http --verify=no https://localhost/ping
 
HTTP/1.1 200 OK
Access-Control-Allow-Credentials: true
Access-Control-Allow-Origin: *
Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, X-Powered-By
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 45
Content-Type: text/plain
Date: Tue, 22 Jun 2021 09:06:02 GMT
Server: nginx/1.21.0
X-Powered-By: restheart.org

Greetings from RESTHeart!
```

To stop:

```bash
docker-compose stop
```

To clean-up:

```bash
docker-compose down
```
