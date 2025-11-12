### 1. Установить Redis
```sh
helm install hhi-redis bitnami/redis --namespace default -f values.yaml
```

### 2. Обновляем Redis
```sh
helm upgrade hhi-redis bitnami/redis --namespace default -f values.yaml
```

### 3. Удаляем Redis
```sh
helm uninstall hhi-redis --namespace default
```