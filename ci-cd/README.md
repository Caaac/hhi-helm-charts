## Создание сервисного аккаунта (СА)

### 1. Создание СА
```sh
kubectl apply -f service-account/gitlab-service-account.yaml
```

### 2. Создание секретов СА
```sh
kubectl apply -f service-account/gitlab-service-account-secret.yaml
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


## Установка GitLab Runner с чартом Helm

### 1. Создание СА
```sh
helm repo add gitlab https://charts.gitlab.io
```

### 2. Проверить, к каким версиям GitLab Runner у есть доступ
```sh
helm search repo -l gitlab/gitlab-runner
```

### 3. Обновить чарт
```sh
helm repo update gitlab
```

### 4. Установить runnerToken в runner-values.yaml

### 5. Обновить чарт
```sh
helm install gitlab-runner gitlab/gitlab-runner -f gitlab-runner/runner-values.yaml --namespace gitlab-runner --create-namespace
```

### 6. Обновить чарт
```sh
helm upgrade gitlab-runner gitlab/gitlab-runner -f gitlab-runner/runner-values.yaml --namespace gitlab-runner
```

### 7. Обновить чарт
```sh
helm delete --namespace gitlab-runner gitlab-runner
```
