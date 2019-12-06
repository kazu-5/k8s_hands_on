helm install stable/mysql --generate-name --namespace app





helm install stable/mysql --generate-name

> helm install --namespace app --name mysql -f mysql-values.yml stable/mysql
Error: unknown flag: --name

> minikube ip

> mysql -uroot -ppassword -h 192.168.99.101 -P32000
mysql: [Warning] Using a password on the command line interface can be insecure.
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.99.101' (61)