# DevOps Monitoring Project

This project demonstrates a **full DevOps monitoring stack** using:

- **Python app** exposing Prometheus metrics
- **Prometheus** to scrape metrics
- **Grafana** to visualize metrics
- **Kubernetes** for deployment
- **Docker** for containerization

---

![Docker](https://img.shields.io/badge/docker-ready-blue)
![Kubernetes](https://img.shields.io/badge/kubernetes-deployed-blue)
![Prometheus](https://img.shields.io/badge/monitoring-prometheus-orange)
![Grafana](https://img.shields.io/badge/dashboard-grafana-yellow)

---
## Features

- Real-time metrics collection from a Python application
- Grafana dashboards to visualize request rates and errors
- Prometheus metrics scraping
- Easy to deploy in Kubernetes
- Load-testing ready with tools like `hey` or `wrk`

---

## 📊 Grafana Dashboard

<img width="1914" height="969" alt="Screenshot 2025-10-21 165601" src="https://github.com/user-attachments/assets/a4994731-d523-4a51-8f2a-aa82ce3a48d3" />
<img width="1901" height="970" alt="Screenshot 2025-10-21 165625" src="https://github.com/user-attachments/assets/8e8702f8-a9f8-4f14-91a9-57743b9ea777" />

## 📊 Prometheus target 
<img width="1919" height="435" alt="Screenshot 2025-10-21 165655" src="https://github.com/user-attachments/assets/286f6368-3244-43d0-b856-ed3b8c2e47aa" />


## Deployment Instructions

### 1. Build Docker image

```bash
docker build -t <your-dockerhub-username>/python-app:latest ./app
docker push <your-dockerhub-username>/python-app:latest
```
### 2. Deploy to Kubernetes

```bash
kubectl apply -f k8s/
kubectl get pods
kubectl get svc
```
### 3. Access Grafana
```bash
kubectl port-forward svc/grafana 3000:3000
```
 * Grafana URL: http://localhost:3000
 * Default login: admin / admin

### 4. Access Prometheus
```bash
kubectl port-forward svc/prometheus 30090:9090
```
 * Prometheus URL: http://localhost:30090

### 5. Dashboard Metrics

 * app_requests_total → Total requests

 * rate(app_requests_total[1m]) → Requests per second

 * CPU / Memory usage if Node Exporter or kube-metrics installed

 * Optional: Error rates (app_errors_total)

## Project Structure
```
devops-monitoring/
├── app/
│   ├── app.py                # Your Python app
│   └── requirements.txt
├── k8s/
│   ├── python-app-deployment.yaml
│   ├── python-app-service.yaml
│   ├── prometheus-configmap.yaml
│   ├── prometheus-deployment.yaml
│   ├── prometheus-service.yaml
│   └── grafana-deployment.yaml
├── Dockerfile
├── .gitignore
└── README.md
```


