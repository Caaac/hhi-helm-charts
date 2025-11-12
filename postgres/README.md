### 1. Создать PVC
```sh
kubectl apply -f postgres-pv.yaml
```

### 2. Создать секрет
```sh
kubectl apply -f postgres-secret.yaml
```

### 3. Установить PostgreSQL с Helm
```sh
helm install postgresql bitnami/postgresql --namespace default -f values.yaml
```

### 4. Проверить установку
```sh
kubectl get pods,secrets,pvc
```

### 5. Обновляем PostgreSQL
```sh
helm upgrade postgresql bitnami/postgresql --namespace default -f values.yaml
```

### 6. Удаляем PostgreSQL
```sh
helm uninstall postgresql --namespace default
```