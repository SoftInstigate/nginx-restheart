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
curl -k -u admin:secret https://localhost/ping

{"msg":"Hello World!"}
```

To test that it works with `httpie`:

```bash
http --verify no -a admin:secret https://localhost/ping

HTTP/1.1 200 OK
Access-Control-Allow-Credentials: true
Access-Control-Allow-Origin: *
Access-Control-Expose-Headers: Location, ETag, X-Powered-By
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 42
Content-Type: application/json
Date: Tue, 16 Jul 2019 14:36:22 GMT
Server: nginx/1.17.1
X-Powered-By: restheart.org

{
    "msg": "Hello World!"
}

```

To stop:

```bash
docker-compose stop
```

To clean-up:

```bash
docker-compose down
```
