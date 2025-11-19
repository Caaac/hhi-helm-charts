### 1. Установить Redis
```sh
kubectl apply -f gitlab-service-account.yaml
```

### 2. Обновляем Redis
```sh
kubectl apply -f gitlab-service-account-secret.yaml
```

### 3. Получите токен
```sh
kubectl get secret gitlab-service-account-token -n default -o jsonpath='{.data.token}' | base64 --decode
```

### 4. Получение CA сертификата
```sh
kubectl get secret gitlab-service-account-token -n default -o jsonpath='{.data.ca\.crt}'
```

### 5. Получите адрес API сервера
```sh
kubectl cluster-info | grep 'Kubernetes control plane' | awk '/http/ {print $NF}'
```