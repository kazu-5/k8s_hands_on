

```
~> gcloud config set project k8s-hands-on-262513
Updated property [core/project].

```

```
~> gcloud config set compute/zone asia-northeast1-a
Updated property [compute/zone].
```

```
~> gcloud container clusters create k8s-hands-on
WARNING: In June 2019, node auto-upgrade will be enabled by default for newly created clusters and node pools. To disable it, use the `--no-enable-autoupgrade` flag.
WARNING: Starting in 1.12, new clusters will have basic authentication disabled by default. Basic authentication can be enabled (or disabled) manually using the `--[no-]enable-basic-auth` flag.
WARNING: Starting in 1.12, new clusters will not have a client certificate issued. You can manually enable (or disable) the issuance of the client certificate using the `--[no-]issue-client-certificate` flag.
WARNING: Currently VPC-native is not the default mode during cluster creation. In the future, this will become the default mode and can be disabled using `--no-enable-ip-alias` flag. Use `--[no-]enable-ip-alias` flag to suppress this warning.
WARNING: Starting in 1.12, default node pools in new clusters will have their legacy Compute Engine instance metadata endpoints disabled by default. To create a cluster with legacy instance metadata endpoints disabled in the default node pool, run `clusters create` with the flag `--metadata disable-legacy-endpoints=true`.
WARNING: Your Pod address range (`--cluster-ipv4-cidr`) can accommodate at most 1008 node(s). 
This will enable the autorepair feature for nodes. Please see https://cloud.google.com/kubernetes-engine/docs/node-auto-repair for more information on node autorepairs.
Creating cluster k8s-hands-on in asia-northeast1-a... Cluster is being health-checked (master is healthy)...done.       
Created [https://container.googleapis.com/v1/projects/k8s-hands-on-262513/zones/asia-northeast1-a/clusters/k8s-hands-on].
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload_/gcloud/asia-northeast1-a/k8s-hands-on?project=k8s-hands-on-262513
kubeconfig entry generated for k8s-hands-on.
NAME          LOCATION           MASTER_VERSION  MASTER_IP    MACHINE_TYPE   NODE_VERSION    NUM_NODES  STATUS
k8s-hands-on  asia-northeast1-a  1.13.11-gke.14  34.85.38.55  n1-standard-1  1.13.11-gke.14  3          RUNNING
```

```
~> 
kubectl run hello-server --image gcr.io/google-samples/hello-app:1.0 --port 8080
kubectl run --generator=deployment/apps.v1 is DEPRECATED and will be removed in a future version. Use kubectl run --generator=run-pod/v1 or kubectl create instead.
deployment.apps/hello-server created

```

```
~> kubectl expose deployment hello-server --type "LoadBalancer"
service/hello-server exposed
```

```
~> kubectl get all
NAME                                READY   STATUS    RESTARTS   AGE
pod/hello-server-6d89bbd574-4wnbh   1/1     Running   0          3m23s

NAME                   TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
service/hello-server   LoadBalancer   10.11.243.186   34.84.0.45    8080:30582/TCP   2m27s
service/kubernetes     ClusterIP      10.11.240.1     <none>        443/TCP          6m24s

NAME                           READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/hello-server   1/1     1            1           3m24s

NAME                                      DESIRED   CURRENT   READY   AGE
replicaset.apps/hello-server-6d89bbd574   1         1         1       3m24s


~> curl http://34.84.0.45:8080
Hello, world!
Version: 1.0.0
Hostname: hello-server-6d89bbd574-4wnbh

```

```
~> kubectl delete service hello-server
service "hello-server" deleted





