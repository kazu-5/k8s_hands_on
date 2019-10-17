
```
> kubectl apply -f .
configmap/nginx-config created
pod/nginx created

> kubectl -n app exec -it nginx ash
# apk add --update curl
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/4) Installing ca-certificates (20190108-r0)
(2/4) Installing nghttp2-libs (1.39.2-r0)
(3/4) Installing libcurl (7.66.0-r0)
(4/4) Installing curl (7.66.0-r0)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 30 MiB in 41 packages

# curl -I localhost
HTTP/1.1 302 Moved Temporarily
Server: nginx/1.17.4
Date: Thu, 17 Oct 2019 02:10:09 GMT
Content-Type: text/html
Content-Length: 145
Connection: keep-alive
Location: https://google.com

```
