## 1.Deployment作成
```
> kubectl apply -f .
configmap/nginx-config created
deployment.apps/nginx created
service/nginx-service created
```

## 2. kubectl get all
```
> kubectl get all
NAME                        READY   STATUS    RESTARTS   AGE
pod/nginx-bcd54c469-cg6xm   1/1     Running   0          68s
pod/nginx-bcd54c469-l9529   1/1     Running   0          68s
pod/nginx-bcd54c469-qzxqh   1/1     Running   0          68s


NAME                    TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/nginx-service   NodePort   10.101.161.213   <none>        80:32148/TCP   69s


NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nginx   3/3     3            3           69s

NAME                              DESIRED   CURRENT   READY   AGE
replicaset.apps/nginx-bcd54c469   3         3         3       69s

```

## 3.curlコマンド
```
> curl 192.168.99.100:32148
<html>
<head><title>302 Found</title></head>
<body>
<center><h1>302 Found</h1></center>
<hr><center>nginx/1.17.5</center>
</body>
</html>

```

