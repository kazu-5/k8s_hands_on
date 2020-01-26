gcloud auth login

gcloud services enable containerregistry.googleapis.com

docker tag app gcr.io/k8s-hands-on-262513/rails-app

gcloud auth configure-docker

docker push gcr.io/k8s-hands-on-262513/rails-app

gcloud container clusters create my-cluster --disk-size 30 --num-nodes 3

gcloud container clusters get-credentials my-cluster

kubectl create ns app

kubens app

kubectl apply -f development.yaml

kubectl apply -f configmap.yaml

kubectl apply -f service.yaml

kubectl -n app run mysql --image mysql:5.7 --port 3306 --env "MYSQL_ROOT_PASSWORD=password"

kubectl -n app expose deployment mysql --type "NodePort"



kubectl -n app exec -it -c app $(kubectl -n app get po -l app=rails -o json | jq -r ".items[0].metadata.name") bundle exec rails db:migrate
kubectl -n app exec -it -c app $(kubectl -n app get po -l app=rails -o json | jq -r ".items[0].metadata.name") bundle exec rails db:create




kubectl delete ns app
