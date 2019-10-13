## 1.namespace作成

```
>kubectl -n app apply -f .
pod/nginx created

>kubectl create ns app
namespace/app created
```

## 2.Pod作成
```
> kubectl -n app apply -f .
pod/nginx created

> kubectl -n app get pod
NAME    READY   STATUS    RESTARTS   AGE
nginx   1/1     Running   0          18s
```

## 3.`wget`コマンド実行
```
> kubectl -n app exec -it nginx -- sh -c "wget localhost"
Connecting to localhost (127.0.0.1:80)
index.html           100% |********************************|   612  0:00:00 ETA
```

## 4.Pod削除
```
> kubectl -n app delete pod nginx
pod "nginx" deleted
```

## 5.namespace削除
```
>kubectl delete ns app
namespace "app" deleted
```