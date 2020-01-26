eval (minikube  docker-env)

docker build -t app:1 .

kubectl -n app exec -it -c nginx (kubectl get po -l app=rails -o json | jq -r ".items[0].metadata.name") -- ash -c "apk add --update curl && curl -I localhost"

```
> kubectl exec -it -c app (kubectl get pod -l app=rails -o json | jq -r ".items[0].metadata.name") -- curl -I localhost:3000
HTTP/1.1 200 OK
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Content-Type: text/html; charset=utf-8
ETag: W/"3b996074c6b54ecadcd45fc99af8d168"
Cache-Control: max-age=0, private, must-revalidate
Content-Security-Policy: script-src 'unsafe-inline'; style-src 'unsafe-inline'
X-Request-Id: 615f963b-a0e5-4fcc-b319-ec86115f0919
X-Runtime: 0.010104
```

```
> kubectl -n app exec -it -c nginx (kubectl get po -l app=rails -o json | jq -r ".items[0].metadata.name") -- ash -c "apk add --update curl && curl -I localhost"
OK: 30 MiB in 41 packages
HTTP/1.1 200 OK
Server: nginx/1.17.6
Date: Mon, 09 Dec 2019 15:00:49 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
ETag: W/"3b996074c6b54ecadcd45fc99af8d168"
Cache-Control: max-age=0, private, must-revalidate
Content-Security-Policy: script-src 'unsafe-inline'; style-src 'unsafe-inline'
X-Request-Id: 711b9bb7-cd06-453a-acce-a67130605025
X-Runtime: 0.003727
```

```
> curl -I (minikube ip):(kubectl -n app get service rails-service -o json | jq ".spec.ports[0].nodePort")
HTTP/1.1 200 OK
Server: nginx/1.17.6
Date: Mon, 09 Dec 2019 15:12:25 GMT
Content-Type: text/html; charset=utf-8
Connection: keep-alive
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
ETag: W/"3b996074c6b54ecadcd45fc99af8d168"
Cache-Control: max-age=0, private, must-revalidate
Content-Security-Policy: script-src 'unsafe-inline'; style-src 'unsafe-inline'
X-Request-Id: 3c5c0b71-4301-4c93-895f-72d67819c827
X-Runtime: 0.006951

```



kubectl -n app exec -it -c app rails-655566cbbf-hgthc -- rails console

