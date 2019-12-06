eval (minikube  docker-env)

docker build -t app:1 .


kubectl -n app exec -it -c nginx $(kubectl get po -l app=rails -o json | jq -r ".items[0].metadata.name") -- ash -c "apk add --update curl && curl -I localhost"
