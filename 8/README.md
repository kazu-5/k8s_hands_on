
helm install stable/mysql --generate-name

> helm install --namespace app --name mysql -f mysql-values.yml stable/mysql
Error: unknown flag: --name
