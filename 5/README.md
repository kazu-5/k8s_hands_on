## 1.Deployment作成
```
> kubectl -n app apply -f .
configmap/nginx-config unchanged
deployment.apps/nginx created

> kubectl -n app get pod
NAME                     READY   STATUS    RESTARTS   AGE
nginx-857fdb9c5f-6n2lt   1/1     Running   0          44s
nginx-857fdb9c5f-kqwk5   1/1     Running   0          44s
nginx-857fdb9c5f-w8nch   1/1     Running   0          44s

> kubectl -n app get deployment nginx
NAME    DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
nginx   3         3         3            3           3m13s

> kubectl -n app get po -l app=nginx
NAME                     READY   STATUS    RESTARTS   AGE
nginx-857fdb9c5f-6n2lt   1/1     Running   0          3m49s
nginx-857fdb9c5f-kqwk5   1/1     Running   0          3m49s
nginx-857fdb9c5f-w8nch   1/1     Running   0          3m49s
```

## 2.`wget`コマンド実行
```
> kubectl -n app exec -it nginx-857fdb9c5f-6n2lt -- sh -c "wget localhost"
Connecting to localhost (127.0.0.1:80)
index.html           100% |**********************************************************************************************************************************|   612  0:00:00 ETA
```

## 3.deployment削除
```
> kubectl -n app delete deployment nginx
pod "nginx" deleted
```

