helm repo add bitnami https://charts.bitnami.com/bitnami

helm -n ctf upgrade --install mysql \
  --set auth.rootPassword=ctfd \
  --set auth.database=ctfd \
  --set auth.username=ctfd \
  --set auth.password=ctfd \
  --set primary.persistence.size=50Gi \
    bitnami/mysql

helm -n ctf install redis bitnami/redis --set auth.password=ctfd

helm -n ctf upgrade --install  ctfd ctfd