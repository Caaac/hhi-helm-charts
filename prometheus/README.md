### 1. Установка Prometheus-community
```sh
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```

### 2. ...
```sh
helm repo update
```

### 3. Создание namespace
```sh
kubectl create namespace monitoring
```

### 4. Установка Prometheus-community
```sh
helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring
```

### 5. Проброс портов до Prometheus
```sh
kubectl port-forward svc/prometheus-kube-prometheus-prometheus 9090:9090 -n monitoring
```

### 6. Проброс портов до Grafana
```sh
kubectl port-forward svc/prometheus-grafana 3000:80 -n monitoring
```
